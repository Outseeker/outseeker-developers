# Outseeker Preliminary API documation


## Sample call:

### Perform a search for restuarants:
```sh
https://api.outseeker.com/venues?multsearch=5.00&multallsearch=2.00&online_reservations_only=false&moodText=coffee&multmoodsearch=2&cost_min=0&cost_max=20&fast_food_ok=true&restaurants_ok=false&multloc=2.25&multact=1&overall=1&food=1&atmosphere=1&service=1&multrel=0.8&critic=1&verified=1&public=1&latitude=40.7502109&longitude=-74.0035789&open_day=MON&text=trendy&api_key=XXXXXXXX
```



### Using API KEY

These calls require a valid API key supplied by Outseeker.  To obtain a key, send an email to [developers@outseeker.com](mailto:developers@outseeker.com).

Calls without a valid key will return this output:

```sh
{"error_msg": "Invalid api_key"}
```

## Input

The API accepts the following input parameters (shown with exapmple values from above call)

Required parameters:



|  **Required parameters:** |                                                                 |
|:-----------------------|-----------------------------------------------------------------|
| cost_min=0            | minimum cost of restuarants (acts as filter)                    |
| cost_max=20           | maximum cost of restuarants (acts as filter)                    |
| fast\_food\_ok=true     | if true, only return restaurants that have fast_food=T (filter) |
| restaurants_ok=false  | if true, only return restaurants that have fast_food=F (filter) |
| latitude=40.7502109   | geolocation                                                     |
| longitude=-74.0035789 | geolocation                                                     |
|**Optional parameters:**||
|multsearch=5.00|importance of search text|
|multallsearch=2.00|importance of all search terms|
|online\_reservations_only=false|if true, only return results that accept online reservations (filter)|
|moodText=coffee|a 'mood' text to search for|
|multmoodsearch=2|importance of 'mood' text|
|multloc=2.25|importance of location|
|multact=1|importance of value for money|
|overall=1|importance of overall ratings|
|food=1|importance of food ratings|
|atmosphere=1|importance of atmosphere ratings|
|service=1|importance of service ratings|
|multrel=0.8|importance of reliability|
|critic=1|importance of ratings from critics|
|verified=1|importance of ratings from verified customers|
|public=1|importance of ratings from general public|
|open_day= MON|only return restaurants open on this day|
||can be text (Mon, Tue, etc) or integer  0=Monday, 1=Tuesday ... 6=Sunday|
||NOTE: if any value is specified for this parameter, then restaurants|
||lacking open hours information will be excluded from results; to avoid|
||this do not specify open_day, or use open_day=-1|
|open_hour=20            |only return restaurants open at this hour (0-23), defaults to 20|
|open_minute=0           |only return restaurants open at this minute (0-59), defaults to 0|
|text=trendy|optional text to search for|
|limit=4|number of restaurants to return (max=24)|

####Minimum Call:

```sh
http://api.outseeker.com/venues?cost_min=0&cost_max=120&fast_food_ok=true&restaurants_ok=true&latitude=40.7502109&longitude=-74.0035789&api_key=XXXXXXXX
```


## Output

The API returns JSON with the following elements:

|  Returned values: |                                                                 |
|:-----------------------|-----------------------------------------------------------------|
|num_searched				    | total number of restaurants that match filter criteria|
|num_matches				    	| list of search term, number of matches|
|search\_found\_count			    | total number of matches to search text|
|meal_pricing						| basis for pricing ("dinner","lunch", etc.)|
| open_at|the requested opening time, blank if none requested|
|objects				           	| list of restaurants, with lots of fields for each |


Here is the start of the output from the call at the top of this page:

```json
{"num_searched": 3144, "num_matches": [["trendy AND coffee", 8], ["trendy", 17], ["coffee", 817], ["trendy OR coffee", 826]], "search_found_count": 17, "open_at": "MON 20:00","meal_pricing": "dinner", "objects": [{"suitability_grade": 67.0, "reliable_value_grade": 71.0, "michelin_forks": null, "owner_description": "The Roast Boast: Seasonal Veggies & Greens, good-for-you grains & perfect pastas. Marinated Meats Rotisserie-Roasted to perfection, one bowl at a time.", "open_table_id": null, "cost_scaled": 95.0, "michelin_stars": null, "open_table_ambiance": null, "outseeker_overall_grade": 55.0, "gayot_rating": null, "detail_image_url": "http://detail.images.outseeker.com/roast-kitchen.com.png/roast-kitchen.com.png", "address_street": "740 7th Ave", "distance_scaled": 4.0, "zagat_decor": 12.0, "michelin_description": null, "address_postal_code": "10019", "fast_quick": true, "outseeker_cuisine": "Salad|New American|Juice Bar|Smoothies", "google_description": "Updated health-conscious fast-food counter creating bowls & wraps with grilled meats & add-ins.", "comb_pos_badge_text": "Closer Distance", "cost_grade": 40.0, "zagat_description": "This \"busy\" health-food chain offers customizable hot and cold salads featuring a slew of trendy, upmarket ingredients (quinoa, kale), as well as your choice of fish, meat or roasted veggies (and \"watching the prep is fun\"); though service is \"not so friendly\", not many linger since the counter setups are geared toward takeout.", "longitude": -73.984018000000006, "latitude": 40.760474000000002, "zagat_food": 21.0, "website_url": "http://www.roast-kitchen.com", "open_table_food": null, "search_grade": 93.0, "OpenTable_description": null, "yelp_rating": 3.0, "resy_web_link": null, "hours": {"Wed": "7:00am-11:00pm", "Sun": "7:00am-10:00pm", "Thu": "7:00am-11:00pm", "Tue": "7:00am-11:00pm", "Mon": "7:00am-11:00pm", "Fri": "7:00am-11:00pm", "Sat": "7:00am-11:00pm"}, "phone": "212-399-9100", "outseeker_atmosphere_grade": 59.0, "michelin_bib_gourmand": null, "final_grade": 97.0, "open_table_overall": null, "open_table_service": null, "priority_grade": 0.0, "gayot_description": null, "raw_grade": 67.0, "outseeker_food_grade": 46.0, "distance": 1.2447572862920768, "address_city": "New York, NY", "google_PeopleTalkAbout_description": null, "value_grade": 39.0, "name": "Roast Kitchen", "comb_neg_badge_text": "More Expensive|Lower Value for Money", "zagat_service": 15.0, "pred_badge_combined_text": "Most favorable: Zagat Food;     Least favorable: Yelp, Zagat Service;     Ratings from: Yelp, Zagat", "reliability_grade": 79.0, "zagat_url": "http://roast-kitchen-new-york1", "distance_grade": 95.0, "outseeker_rank": 4, "cost": 18, "image_url": "http://images.outseeker.com/roast-kitchen.com.jpg", "ratings_from": "Yelp|Zagat", "outseeker_service_grade": 37.0, "_id": "kud1eaNE"}, {"suitability_grade": 41.0, "reliable_value_grade": 13.0, "michelin_forks": null, "owner_description": null, "open_table_id": null, "cost_scaled": 70.0, "michelin_stars": null, "open_table_ambiance": null, "outseeker_overall_grade": 26.0, "gayot_rating": null, "detail_image_url": "http://detail.images.outseeker.com/nan.png/nan.png", "address_street": "708 3rd Ave", "distance_scaled": 5.0, "zagat_decor": null, "michelin_description": null, "address_postal_code": "10017", "fast_quick": true, "outseeker_cuisine": "Italian|Fast Food", "google_description": null, "comb_pos_badge_text": "Closer Distance", "cost_grade": 79.0, "zagat_description": null, "longitude": -73.973244999999991, "latitude": 40.752512000000003, "zagat_food": null, "website_url": "http://nan", "open_table_food": null, "search_grade": 92.0, "OpenTable_description": null, "yelp_rating": 2.0, "resy_web_link": null, "hours": {"Wed": "10:00am-10:00pm", "Sun": "10:00am-10:00pm", "Thu": "10:00am-10:00pm", "Tue": "10:00am-10:00pm", "Mon": "10:00am-10:00pm", "Fri": "10:00am-10:00pm", "Sat": "10:00am-10:00pm"}, "phone": "212-557-2782", "outseeker_atmosphere_grade": 67.0, "michelin_bib_gourmand": null, "final_grade": 96.0, "open_table_overall": null, "open_table_service": null, "priority_grade": 0.0, "gayot_description": null, "raw_grade": 41.0, "outseeker_food_grade": null, "distance": 1.5948631279186372, "address_city": "New York, NY", "google_PeopleTalkAbout_description": null, "value_grade": 45.0, "name": "Hello Pasta", "comb_neg_badge_text": "Lower Overall Ratings", "zagat_service": null, "pred_badge_combined_text": "Least favorable: Yelp;     Ratings from: Yelp", "reliability_grade": 18.0, "zagat_url": "http://nan", "distance_grade": 92.0, "outseeker_rank": 7, "cost": 13, "image_url": "http://images.outseeker.com/nan.jpg", "ratings_from": "Yelp", "outseeker_service_grade": null, "_id": "wc3lvSfh"},...
```

## Retrieve information for a single restaurant:

*FOR TESTING PURPOSES*, an additional API call is available, which retrieves information on a single known restaurant (in this case "hCLcr4LT")

```sh
https://api.outseeker.com/venues/hCLcr4LT?api_key=XXXXXXXX
```

Note that this call is generally not needed, as all the information it returns is included for each restaurant in the search call described above.  Here is the output:

```json
{"zagat_overall": null, "gayot_rating": null, "michelin_forks": null, "open_table_ambiance": null, "zagat_description": "The \"savory\" Taiwanese steamed buns are \"seriously delicious\" at Eddie Huang's East Villager, whose \"fast-food vibe\" gets a boost from \"blaring hip-hop music\"; despite \"teenage\" service and \"no decor to speak of\", \"cheap\" checks keep its \"college\" crowd content.", "open_table_id": null, "cost": 17, "longitude": -73.985791000000006, "owner_description": null, "OpenTable_description": null, "detail_image_url": "http://detail.images.outseeker.com/baohausnyc.com.png/baohausnyc.com.png", "address_street": "238 E. 14th St.", "zagat_decor": 14.0, "michelin_description": null, "google_description": "Savory Taiwanese steamed buns are the specialty of this bare-bones East Village eatery.", "open_table_service": null, "latitude": 40.732385999999998, "zagat_food": 23.0, "website_url": "http://www.baohausnyc.com", "open_table_food": null, "yelp_rating": 3.5, "phone": "646-669-8889", "michelin_bib_gourmand": null, "open_table_overall": null, "gayot_description": "Baohaus, an East Village eatery from Eddie and Evan Huang, serves up gua bao, or something like a Taiwanese burger. Wrapped in an Asian bun, the gua bao come in several different varieties, including the Haus Bao (braised beef cheek) and Chairman Bao (ultra-tender Niman Ranch pork belly).", "address_city": "New York, New York", "google_PeopleTalkAbout_description": null, "name": "Baohaus", "zagat_service": 16.0, "zagat_url": "baohaus-new-york", "address_postal_code": "10003", "image_url": "http://images.outseeker.com/baohausnyc.com.jpg", "_id": "hCLcr4LT", "michelin_stars": null}

```


