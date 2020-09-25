# test-weather
The main links for the Weather Channel functionality are:
- Administrative area: https://dev-weather-channel.pantheonsite.io/admin/config/services/aggregator
- Imported Weather Feed demo: https://dev-weather-channel.pantheonsite.io/weather-feed-aggregator (built as a Views page which can be configured to be rendered as a table, list, grid, etc.)
- Help Page: https://dev-weather-channel.pantheonsite.io/admin/help/op_weather_agg
- Basic Aggregator service configuration page: https://dev-weather-channel.pantheonsite.io/admin/config/services/aggregator/settings
- We can add custom fields for feeds sources: https://dev-weather-channel.pantheonsite.io/admin/config/services/aggregator/fields

Exposed API Endpoints Demo:

Existing data: https://dev-weather-channel.pantheonsite.io/weather-feed-aggregator/feed

API Feed by Source. As a test I added some Sources. The API Endpoints requires the Feed Source Id in the links:
- https://dev-weather-channel.pantheonsite.io/api/v1/weather/source/1?_format=xml
- https://dev-weather-channel.pantheonsite.io/api/v1/weather/source/1?_format=json

API Feed, All collected Weather Feed data:
- https://dev-weather-channel.pantheonsite.io/api/v1/weather/all?_format=xml
- https://dev-weather-channel.pantheonsite.io/api/v1/weather/all?_format=json

Weather Feed Aggregator channel:

The functionality allows to configure external weather feeds to be pulled into Drupal. The Drupal Core Aggregator Service is used to build this functionality and can be extended via  Entity definitions \ Service Decorators: https://dev-weather-channel.pantheonsite.io/admin/config/services/aggregator

The Weather Feed data is pulled in Entities, so we can very easy to create different variants of displays, pages, etc. The Weather feed data is pulled data during the Server Cron Jobs. The cron runs in the background and does not affect the user experience navigating through the pages.

Each source of the weather feed allows configuring the Source server and the period how often it should be pulled. The Sources are Fieldable Entities so can be easily extended by adding the Drupal fields that can be used as conditions, categories later on the queries used for the Weather Feed.

The Weather Feeds collected can be easily shared by the Feeds page created (Feed display can be attached to any query so the visitors can see/download this. Another way to expose the collected data, it’s using the API, which creates the GET endpoints for the Weather feeds using the Drupal REST API. The endpoints can be configured used the Drupal Views features - creates the queries and custom paths for the desired API endpoints. Easily can be reconfigured by clicks, some more customizations can be achieved by creating custom Rest endpoints.

Using a server with hight capabilities, the application will allow visitors to use the Weather channel without any problems.

Points covered partially by Drupal CMS.
- Service has high availability
- Security
- Device antagonistic UI
- Scalability
- Caching

*NOTE:* An example of CI / CD can be found on the links:
- Gitlab: https://github.com/web247/test-weather/blob/master/_ci/.gitlab-ci.yml
- Bitbucket: https://bitbucket.org/optasy/weather-channel/src/master/.ci/
