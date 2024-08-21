## World Cities Bare Bones API

`worldcities.json` is a json file that was made by coercing information from worldcities csv file ([simplemaps](https://simplemaps.com/data/world-cities)) and converting the data to a json file.

This json is publically hosted on github and you can easily access the file as you would an api to get cities, and city information for particular cities. I created this file for the purpose of autocomplete suggestions for when a user is typing in a city, but the data in this file can apply to other use cases.

<!-- Here's an example of how you might make an api call for an autocomplete city search using JavaScript: -->
// world cities local api
    const [citySearchQuery, setCitySearchQuery] = useState("");
    const [cityAutocomplete, setCityAutocomplete] = useState([]);
    const getWorldCities = async () => {
        if (citySearchQuery.length > 1) {
            let url = 'https://davidekunno93.github.io/worldcities_api/worldcities.json';
            const response = await fetch(url)
                .then(response => response.json())
                .then(data => {
                    let results = [];
                    let limit = 5;
                    for (let i = 0; i < data.length; i++) {
                        if (results.length === limit) {
                            break;
                        } else if (data[i].city_name.toLowerCase().includes(citySearchQuery)) {
                            results.push(data[i]);
                        }
                    };
                    setCityAutocomplete(results);
                })
        } else {
            setCityAutocomplete([]);
        }
    }
    useEffect(() => {
        getWorldCities()
    }, [citySearchQuery]);

Please share this bare bones api with other web developers who may be looking for this type of file!
Thanks