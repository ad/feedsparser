# sensor.feedsparser
Fork of RSS feeds custom component for [Home Assistant](https://www.home-assistant.io/) which can be used in conjunction with the custom [Lovelace](https://www.home-assistant.io/lovelace) [list-card](https://github.com/custom-cards/list-card)

To get started put `/feedsparser/` here:
`<config directory>/custom_components/feedsparser/`

**Example configuration.yaml:**

```yaml
sensor:
- platform: feedsparser
  name: news
  show_topn: 3
  feeds_url:
    - https://news.ru/rss/category/post/russia/
    - https://news.ru/rss/category/post/world/
    - https://news.ru/rss/category/post/incidents/
    - https://news.ru/rss/category/post/economics/
  date_format: '%a, %b %d %I:%M %p'
  inclusions:
    - title
    - link
    - description
    - pubDate
  exclusions:
    - guid
    - language
    - category
  stop_words:
    - drugs
    - sex
    - pop
```

**Configuration variables:**

key | description
:--- | :---
**platform (Required)** | The platform name
**name (Required)** | Name your feed
**feeds_url (Required)** | The RSS feed URLs
**show_topn (Required)** | How many news will be shown per feed
**local_time (Optional)** | Whether to convert date into local time **Default** false
**stop_words (Optional)** | List of words for which titles will be excluded
**date_format (Optional)** | strftime date format for date strings **Default** `%a, %b %d %I:%M %p`
**inclusions (Optional)** | List of fields to include from populating the list
**exclusions (Optional)** | List of fields to exclude from populating the list
**scan_intervall (Optional)** |	Update interval in hours

***

Note: Will return all fields if no inclusions or exclusions are specified.
Will exclude very similar records.


Due to how `custom_components` are loaded, it is normal to see a `ModuleNotFoundError` error on first boot after adding this, to resolve it, restart Home-Assistant.
