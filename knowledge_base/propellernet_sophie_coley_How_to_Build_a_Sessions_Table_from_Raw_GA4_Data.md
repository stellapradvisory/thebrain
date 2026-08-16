# How to Build a Sessions Table from Raw GA4 Data in BigQuery Colin Differ | 18 June 2026 Read more

*Trusted source: Sophie Coley / Propellernet / Propellernet*
*Original publication: [https://www.propellernet.co.uk/insights/how-to-build-a-sessions-table-from-raw-ga4-data-in-bigquery/](https://www.propellernet.co.uk/insights/how-to-build-a-sessions-table-from-raw-ga4-data-in-bigquery/)*
*Publication date: Date not supplied by source*
*Added to Stella PR Advisory knowledge base: 16 August 2026*
*Use: Relevant evidence and thinking for SEO, AI search, GEO, LLM visibility and earned-first strategy.*

---

## Source Summary

See the source article for the complete argument.

## Extracted Source Content

How to Build a Sessions Table from Raw GA4 Data in BigQuery
Colin Differ
18 June 2026
This is the first in a series of articles talking about BigQuery and the common questions we are asked.
For anyone who has started using BigQuery with GA4 data, there’s one main misunderstanding we come across: sessions. We’ve had sessions for years. We understand them, and even when GA4 came along built on events, we still had sessions in the interface. But BigQuery doesn’t deal with sessions,  it’s purely events.
GA4’s BigQuery export gives you a flat table of events. Every page view, scroll, click and purchase is a separate row. That’s useful, but there’s no sessions table out of the box.
That means if you want to work with sessions in BigQuery, you need to build them yourself.
What is a session in GA4
A session is a group of events fired by the same user within the same visit. GA4 creates a new session when a user arrives on the site, and will start a new one if there’s a period of inactivity or if the user comes back via a different marketing channel.
When a new session begins, GA4 fires a session_start event. Each session gets a ga_session_id  a number GA4 generates at that point. Combined with user_pseudo_id, which identifies the device or browser, you have everything you need to group events into sessions.
Why not just count session_start events?
You could just do this:
SELECT
COUNT(*) AS total_sessions
FROM
`bigquery-public-data.ga4_obfuscated_sample_ecommerce.events_*`
WHERE
event_name = 'session_start'
AND _TABLE_SUFFIX BETWEEN '20201101' AND '20210131'
And you’d get a count of session_start events. But that’s all you’d get: a number with no context. You can’t join it to anything, you can’t see which sessions came from paid search, and you can’t tell which ones resulted in a purchase.
There’s also an accuracy problem. The session_start event doesn’t always fire once per session.
If your site is running GA4 Consent Mode (and if you’re not, why not?) GA4 will fire events for users who haven’t given consent, but without a persistent cookie to identify them. That means each page they visit can look like a new session, because there’s nothing to stitch their journey together. The result is inflated session_start counts in BigQuery that are very difficult to spot if you’re just counting rows.
When you build a sessions table using user_pseudo_id and ga_session_id, duplicates are removed, as well as those where consent wasn’t given.
That’s what we’re building here.
What does the raw data look like?
If you run a simple query against the GA4 events table in BigQuery, the results can look a bit confusing at first. Each event isn’t a single clean row with all its data in columns. Instead, the parameters for each event are stored in a field called event_params, which means each parameter sits on its own row.
A single session_start event looks like this in the raw data:
event_name
event_params key
event_params value
session_start
ga_session_id
9819679542
session_start
page_location
https://shop.googlemerchandise
…
session_start
page_referrer
null
session_start
ga_session_number
2
session_start
page_title
Home
session_start
session_engaged
1
session_start
engaged_session_event
1
Extracting the data with UNNEST
To extract a specific parameter from event_params you use a subquery with UNNEST. It looks like this:
(SELECT value.int_value
FROM UNNEST(event_params)
WHERE key = 'ga_session_id') AS session_id
This unpacks the event_params array, finds the row where the key is ga_session_id, and returns the value as a single column. You’ll use this pattern repeatedly when working with GA4 data in BigQuery.
Note that ga_session_id is stored as an integer, so we use value.int_value. Source and medium are strings, so those use value.string_value. If you get that wrong (and you will), you’ll get a lot of null results.
The SQL
Here’s the full query to build a clean sessions table:
SELECT
user_pseudo_id,
(SELECT value.int_value
FROM UNNEST(event_params)
WHERE key = 'ga_session_id') AS session_id,
TIMESTAMP_MICROS(event_timestamp) AS session_start_time
FROM
`bigquery-public-data.ga4_obfuscated_sample_ecommerce.events_*`
WHERE
event_name = 'session_start'
AND _TABLE_SUFFIX BETWEEN '20201101' AND '20210131'
What each field means
Field
What it is
user_pseudo_id
A unique identifier GA4 assigns to each device or browser. It’s cookie-based, not tied to a logged-in user
session_id
A number GA4 generates when a new session starts. Not unique on its own, two different users can have the same value
user_pseudo_id + session_id
Combined, these give you a truly unique session key. Always use both together when joining or grouping session data
session_start_time
When the session started, converted from GA4’s raw format into a readable timestamp
page_title
The title of the page_location of this event
session_engaged
A GA4 flag that marks whether the session met GA4’s definition of an engaged session. That means the user either spent more than 10 seconds on 

---

## Relevance to Stella's Work

This source has been added to Stella's trusted-source monitor. Assess the insight in context and apply it where relevant to the **Brand Visibility Across Search & AI** layer of the Modern Earned Media Measurement Framework. Do not treat a source statistic as universal without retaining its original context, methodology and publication date.

## Related Knowledge Base Files

- [Modern_Earned_Media_Measurement_Framework.md](./Modern_Earned_Media_Measurement_Framework.md)
- [RRF_AI_Visibility_Non_Determinism_Trusted_Insight.md](./RRF_AI_Visibility_Non_Determinism_Trusted_Insight.md)
- [AI_Visibility_LLM_Fan_Out_Research_LinkedIn_Post.md](./AI_Visibility_LLM_Fan_Out_Research_LinkedIn_Post.md)
- [AI_Visibility_LLM_Citation_Behaviour_LinkedIn_Post.md](./AI_Visibility_LLM_Citation_Behaviour_LinkedIn_Post.md)
