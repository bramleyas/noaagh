# NOAAGH
### *A JavaScript wrapper for the NOAA/NWS Public API*

## About
This package can be used to easily access data from the National Weather Service's [public API](https://www.weather.gov/documentation/services-web-api#). It's stupid simple: no, really - this implementation is a bit rough. This is my first package project, and it's been a while since I've touched code. After time, this code will be way more efficient. The wrapper uses the Fetch API to access the NWS' endpoints.
## Usage
All functions are named after their respective endpoints in as listed in the 'Specification' tab of the API's website listed above, slashes removed and typed in camelCase.

*Logging the response from the `/glossary` endpoint*
```js
const noaagh = require('noaagh');
noaagh.glossary();
/* '1-2-3 Rule'
'A means of avoiding winds associated with a tropical cyclone by taking into account the forecast track error of the National Weather Service...'*/
```
*Logging the response from the `/alerts/active/zone/ILC104` endpoint for Chicago, Illinois*
```js
noaagh.alertsActiveZone('ILC104');
/* 'Current watches, warning, and advisories for ILC104' */
```
## Resources
- Public Zone IDs: https://www.weather.gov/pimar/PubZone
- *More coming soon*
## TODO
- Write new functions for specific applications
  - Temperature for specific location
  - Weather condition for specific location
  - Images?
- Clean up the code, perhaps not so repetitive
- Provide example .js files
- Provide more NWS resources