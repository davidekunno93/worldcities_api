## World Cities Bare Bones API

The `worldcities.json` is a json file that was made by coercing information from worldcities csv file ([simplemaps](https://simplemaps.com/data/world-cities)) and converting the data to a json file.

This json is publically hosted on github and you can easily access the file as you would an api to get cities, and city information for particular cities. I created this file for the purpose of autocomplete suggestions for when a user is typing in a city, but the data in this file can apply to other use cases.

Here's an example of how you might make an api call for an autocomplete city search using JavaScript:
- Make an api call using `const response = await fetch('https://davidekunno93.github.io/worldcities_api/worldcities.json')`
- Use `.then(response => response.json())`
- Then .then(data => { #loop through the data and check if the search text is included in the city_name key of each data object})
- Capture the data object if there is a match, push it into a `results` array, and if the length of the `results` array reaches 5, break the loop


Please share this bare bones api with other web developers who may be looking for this type of file!
Thanks