# Holidays.js
Holiday support for Moment.js.
## Installation
### Bower
```
bower install holidays
```
### Browser
1. Get your API key at http://holidayapi.com.
2. Declare your API key and include `Holidays.js` in your page **after** you have loaded `Moment.js`.
```
<script type="text/javascript">
	const holidays_api_key="9f4c25e6-81ba-48b9-FAKE-1ee8c24fd928"
</script>
<script src="moment.js" type="text/javascript"></script>
<script src="Holidays.js" type="text/javascript"></script>
```
## Usage
#### `.holiday()`
Tells if a moment is a holiday. This asynchronous function takes two callbacks as arguments: the first will be called on success and the second on failure.
```
moment('2015-12-25', 'YYYY-MM-DD').holiday(
    function(result){
        console.log(result); // true
    },
    function(error){
        console.log(error); // IO error, JSON parse error...
    }
);
```
#### `.holidays()`
Lists the names of a moment's holidays. This asynchronous function takes two callbacks as arguments: the first will be called on success and the second on failure.
```
moment('2015-12-25', 'YYYY-MM-DD').holidays(
    function(result){
        console.log(result); // ["Christmas"]
    },
    function(error){
        console.log(error); // IO error, JSON parse error...
    }
);
```
### Country code & language
Holiday names, dates and quantity vary between countries. Each query to the web service requires specifying a country code for which to retrieve the holidays. Holiday names are returned in the language which corresponds to the country code set at the moment of the function call (e.g. English for `US`, French for `FR`...). This setting defaults to `US`.
#### Get
To get the current country code:
```
var country_code = moment().countryCode(); // Default is 'US'.
```
#### Set
To switch country code:
```
moment().countryCode('FR');
```
All functions use the country code set at the time of call. Therefore, changing it will not affect previous calls. 
## Contributing
1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## History
v1.0.1
  * Adds https support
  * Adds API key support (required as of July 2016)
  
v1.0.0
  * All functions except `countryCode()` are asynchronous
  * Adds QUnit testing
  * ~~Preload years~~
  
v0.1.0
  * Check if day is a holiday
  * List moment holidays
  * Get or set country code
  * Preload years
  * Holidays are cached

## Credits
[Geoffroy EMPAIN](http://empain.eu)

[Josh Sherman](http://joshtronic.com/?ref=holidayapi) for his holiday API
## License
MIT
