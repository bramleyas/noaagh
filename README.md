# NOAAGH
### *A JavaScript wrapper for the NOAA/NWS Public API*

## About
- https://github.com/bramleyas/noaagh
- https://www.npmjs.com/package/noaagh

This package can be used to easily access data from the National Weather Service's [public API](https://www.weather.gov/documentation/services-web-api#). It's stupid simple: no, really - this implementation is a bit rough. This is my first package project, and it's been a while since I've touched code. After time, this code will be way more efficient. The wrapper uses the Fetch API to access the NWS' endpoints.
## Usage
All functions are named after their respective endpoints in as listed in the 'Specification' tab of the API's website listed above, slashes removed and typed in camelCase.

*GETting the response from the `/glossary` endpoint*
```js
const noaagh = require('noaagh');
noaagh.glossary();
/* ...'1-2-3 Rule'
'A means of avoiding winds associated with a tropical cyclone by taking into account the forecast track error of the National Weather Service'...*/
```
*Logging the response from the `/alerts/active/zone/ILC104` endpoint for Chicago, Illinois*
```js
noaagh.alertsActiveZone('ILC104').then(output) => {
  console.log(output);
};
/* ...'Current watches, warning, and advisories for ILC104'... */
```
*Logging the temperature of a specific coordinate (this will eventually be included in the package, but the API is giving me some grief and I'm tired)*
```js
function temperature(point) {
  noaagh.points(point).then((out) => {
    noaagh.gridpointsWfoXYForecastHourly(out.properties.cwa, out.properties.gridX, out.properties.gridY).then((output) => {
      console.log(output.properties.periods[0].temperature);
    });
  });
};
```
## Resources
- Public Zone IDs: https://www.weather.gov/pimar/PubZone
- *More coming soon*
## TODO
- Write new functions for specific applications
  - Temperature for specific location (basically done)
  - Weather condition for specific location
  - Images?
- Clean up the code, perhaps not so repetitive
- Provide example .js files
- Provide more NWS resources
