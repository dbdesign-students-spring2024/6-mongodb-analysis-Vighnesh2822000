# AirBnB MongoDB Analysis

## Data Source
Data set details:

- Display some of the raw data from the original data file (the first 20 rows is enough - feel free to clip the text in fields to prevent line-wrapping).

- The data I use in this assignment was taken from Inside Airbnb, which is an investigatory website releasing data on Airbnb listings in various cities.[Sunshine Coast, Queensland, Australia](https://data.insideairbnb.com/australia/qld/sunshine-coast/2024-02-29/data/listings.csv.gz)
- The original data was in a `csv` file compressed with `gzip` compressino.
- Sample data - I'm inserting an image because formatting the first 20 rows using markdown will be a waste of time
 [sample data](data/Screenshot%202024-04-05%20095637.png)

- There were some datas missing from the 'neighbourhood', 'first_review', 'host_reponse_time', 'host_response_rate', 'host_acceptance_rate', some review_score_rating fields and 'last review' fields, but none of fields are used in this analysis. The 'neighbouthood_cleansed' field has the necessary detail to find the neighbourhood of the listing.Other fields have a reson to be empty. I have chosen to leave the documents for which we dont have review_score_ratings as it is, because those data's are useful in knowing the number of listings. And in the query that deals with the review ratings, i have chosen to omit those documents.   


## Analysis:

  1. - show exactly two documents from the `listings` collection in any order
  ```
      db.listings.find().limit(2)
  ```
```   
   [
  {
    _id: ObjectId('660dfa89b6515eb205796364'),
    id: 300526,
    listing_url: 'https://www.airbnb.com/rooms/300526',
    scrape_id: Long('20240229002402'),
    last_scraped: '2024-02-29',
    source: 'city scrape',
    name: 'Tiny Farm House on The Hill',
    description: 'Welcome to the Tiny Farm House on The Hill. Enjoy the 180° views of the rolling Sunshine Coast Hinterland, mini cows, sheep & alpacas all from the windows of this minimal impact luxury tiny house. Cook up a feast with the equipped kitchenette and patio BBQ and eat near the outdoor fireplace watching the country stars come out. Meet the hand raised farm animals up close or snack on some seasonal organic farm fruit, veggies & herbs.',
    neighborhood_overview: '',
    picture_url: 'https://a0.muscache.com/pictures/miso/Hosting-300526/original/9b381f4c-d740-457e-91d4-6de46043cad5.jpeg',
    host_id: 1547968,
    host_url: 'https://www.airbnb.com/users/show/1547968',
    host_name: 'Ben',
    host_since: '2011-12-29',
    host_location: 'Peachester, Australia',
    host_about: 'I moved to iconic Mango Hill Farm in 2017. Since moving my family and I have rescued dozens of animals and produced seasonal fruit and vegetables for local restaurants.',
    host_response_time: 'within an hour',
    host_response_rate: '100%',
    host_acceptance_rate: '100%',
    host_is_superhost: 'f',
    host_thumbnail_url: 'https://a0.muscache.com/im/pictures/user/30b2d6ec-76b7-4291-ab1f-585017839bd2.jpg?aki_policy=profile_small',     
    host_picture_url: 'https://a0.muscache.com/im/pictures/user/30b2d6ec-76b7-4291-ab1f-585017839bd2.jpg?aki_policy=profile_x_medium',    
    host_neighbourhood: '',
    host_listings_count: 4,
    host_total_listings_count: 4,
    host_verifications: "['email', 'phone']",
    host_has_profile_pic: 't',
    host_identity_verified: 't',
    neighbourhood: '',
    neighbourhood_cleansed: 'Beerwah',
    neighbourhood_group_cleansed: 'Sunshine Coast',
    latitude: -26.84728,
    longitude: 152.86976,
    property_type: 'Farm stay',
    room_type: 'Entire home/apt',
    accommodates: 4,
    bathrooms: 1,
    bathrooms_text: '1 bath',
    bedrooms: 2,
    beds: 2,
    amenities: '["Cooking basics", "Fire extinguisher", "Outdoor dining area", "Air conditioning", "Cleaning products", "Bed linens", "Wine glasses", "Barbecue utensils", "Outdoor furniture", "Smoke alarm", "Kitchen", "First aid kit", "Laundromat nearby", "Essentials", "Ceiling fan", "Heating", "Mini fridge", "Bidet", "Shower gel", "Hot water kettle", "Toaster", "Shampoo", "Luggage dropoff allowed", "Garden view", "Fire pit", "Long term stays allowed", "Hot water", "Dedicated workspace", "Free parking on premises", "Conditioner", "Mountain view", "TV", "Free dryer", "Freezer", "Hair dryer", "Clothing storage", "Wifi", "Shared backyard \\u2013 Fully fenced", "Lockbox", "Dishes and silverware", "Free washer", "Iron", "Stove", "BBQ grill: gas", "Private patio or balcony", "Coffee", "Microwave", "Self check-in", "Refrigerator", "Body soap", "Room-darkening shades", "Cleaning available during stay"]',
    price: '$198.00',
    minimum_nights: 2,
    maximum_nights: 30,
    minimum_minimum_nights: 1,
    maximum_minimum_nights: 2,
    minimum_maximum_nights: 1125,
    maximum_maximum_nights: 1125,
    minimum_nights_avg_ntm: 2,
    maximum_nights_avg_ntm: 1125,
    calendar_updated: '',
    has_availability: 't',
    availability_30: 0,
    availability_60: 0,
    availability_90: 0,
    availability_365: 0,
    calendar_last_scraped: '2024-02-29',
    number_of_reviews: 119,
    number_of_reviews_ltm: 38,
    number_of_reviews_l30d: 0,
    first_review: '2021-07-18',
    last_review: '2024-01-23',
    review_scores_rating: 4.83,
    review_scores_accuracy: 4.83,
    review_scores_cleanliness: 4.63,
    review_scores_checkin: 4.91,
    review_scores_communication: 4.95,
    review_scores_location: 4.92,
    review_scores_value: 4.58,
    license: '',
    instant_bookable: 'f',
    calculated_host_listings_count: 1,
    calculated_host_listings_count_entire_homes: 1,
    calculated_host_listings_count_private_rooms: 0,
    calculated_host_listings_count_shared_rooms: 0,
    reviews_per_month: 3.73
  },
  {
    _id: ObjectId('660dfa89b6515eb205796363'),
    id: 177754,
    listing_url: 'https://www.airbnb.com/rooms/177754',
    scrape_id: Long('20240229002402'),
    last_scraped: '2024-02-29',
    source: 'city scrape',
    name: 'Coolum Ocean Views, 6 guests at no extra cost!',
    description: 'Accommodates up to 7 guests! Beautiful tropical surroundings for privacy. <br />Glorious white surf, sand and ocean views. Wake to a Pacific Sunrise. Beach holidays at your door step.  Watch whales from your deck. Class and style best describe our Holiday House. <br />2 Min WALK TO BEACH, TV in every room, INTERNET, AIRCON, OFF STREET PARKING, DOG FRIENDLY.<br />Bookings are WEEKLY Sat - Sat during school holidays or min of 3 nts booking. 15% discount on request for weekly Bookings outside school holidays.',
    neighborhood_overview: '',
    picture_url: 'https://a0.muscache.com/pictures/11666017/347c8c5d_original.jpg',
    host_id: 850132,
    host_url: 'https://www.airbnb.com/users/show/850132',
    host_name: 'Maureen',
    host_since: '2011-07-21',
    host_location: 'Coolum Beach, Australia',
    host_about: 'We have travelled all over the world and lived in many countries.\n' +
      'We are dog lovers and  offer our holiday house to owners and their pets.',
    host_response_time: 'within a few hours',
    host_response_rate: '100%',
    host_acceptance_rate: '81%',
    host_is_superhost: 't',
    host_thumbnail_url: 'https://a0.muscache.com/im/users/850132/profile_pic/1326064835/original.jpg?aki_policy=profile_small',
    host_picture_url: 'https://a0.muscache.com/im/users/850132/profile_pic/1326064835/original.jpg?aki_policy=profile_x_medium',
    host_neighbourhood: '',
    host_listings_count: 2,
    host_total_listings_count: 2,
    host_verifications: "['email', 'phone']",
    host_has_profile_pic: 't',
    host_identity_verified: 't',
    neighbourhood: '',
    neighbourhood_cleansed: 'Coolum Beach',
    neighbourhood_group_cleansed: 'Sunshine Coast',
    latitude: -26.53614,
    longitude: 153.09206,
    property_type: 'Entire home',
    room_type: 'Entire home/apt',
    accommodates: 7,
    bathrooms: 2,
    bathrooms_text: '2 baths',
    bedrooms: 3,
    beds: 5,
    amenities: '["Backyard", "Lockbox", "Wine glasses", "Dishwasher", "Hot water kettle", "High chair", "Hangers", "Freezer", "Oven", "Baby safety gates", "Cooking basics", "Bathtub", "Crib - available upon request", "Hot water", "Outdoor furniture", "Coffee maker: espresso machine", "Washer", "Self check-in", "Bed linens", "Children\\u2019s books and toys", "Free parking on premises", "Smoking allowed", "Microwave", "Pets allowed", "Board games", "Dryer", "Rice maker", "Sea view", "Iron", "Extra pillows and blankets", "Drying rack for clothing", "Mini fridge", "Central heating", "Stove", "Clothing storage: walk-in closet", "Central air conditioning", "Wifi", "Ceiling fan", "Barbecue utensils", "Long term stays allowed", "Dishes and silverware", "Blender", "65\\" TV with standard cable", "Cleaning products", "Laundromat nearby", "Beach view", "Public or shared beach access", "Dedicated workspace", "Free street parking", "Private entrance", "Toaster", "Hair dryer", "Books and reading material", "Dining table", "Outdoor dining area", "Refrigerator", "Window guards", "Patio or balcony", "Room-darkening shades", "BBQ grill", "Kitchen", "Ocean view", "Smoke alarm"]',
    price: '$360.00',
    minimum_nights: 3,
    maximum_nights: 60,
    minimum_minimum_nights: 3,
    maximum_minimum_nights: 7,
    minimum_maximum_nights: 60,
    maximum_maximum_nights: 60,
    minimum_nights_avg_ntm: 3.6,
    maximum_nights_avg_ntm: 60,
    calendar_updated: '',
    has_availability: 't',
    availability_30: 14,
    availability_60: 44,
    availability_90: 74,
    availability_365: 319,
    calendar_last_scraped: '2024-02-29',
    number_of_reviews: 47,
    number_of_reviews_ltm: 6,
    number_of_reviews_l30d: 0,
    first_review: '2012-02-05',
    last_review: '2024-01-20',
    review_scores_rating: 4.74,
    review_scores_accuracy: 4.74,
    review_scores_cleanliness: 4.87,
    review_scores_checkin: 4.83,
    review_scores_communication: 4.78,
    review_scores_location: 4.85,
    review_scores_value: 4.68,
    license: '',
    instant_bookable: 'f',
    calculated_host_listings_count: 2,
    calculated_host_listings_count_entire_homes: 2,
    calculated_host_listings_count_private_rooms: 0,
    calculated_host_listings_count_shared_rooms: 0,
    reviews_per_month: 0.32
  }
]
```

2. - show exactly 10 documents in any order, but "prettyprint" in easier to read format, using the `pretty()` function.
   ```
   db.listings.find().pretty().limit(10)
   ```
```   [
  {
    _id: ObjectId('660dfa89b6515eb205796364'),
    id: 300526,
    listing_url: 'https://www.airbnb.com/rooms/300526',
    scrape_id: Long('20240229002402'),
    last_scraped: '2024-02-29',
    source: 'city scrape',
    name: 'Tiny Farm House on The Hill',
    description: 'Welcome to the Tiny Farm House on The Hill. Enjoy the 180° views of the rolling Sunshine Coast Hinterland, mini cows, sheep & alpacas all from the windows of this minimal impact luxury tiny house. Cook up a feast with the equipped kitchenette and patio BBQ and eat near the outdoor fireplace watching the country stars come out. Meet the hand raised farm animals up close or snack on some seasonal organic farm fruit, veggies & herbs.',
    neighborhood_overview: '',
    picture_url: 'https://a0.muscache.com/pictures/miso/Hosting-300526/original/9b381f4c-d740-457e-91d4-6de46043cad5.jpeg',
    host_id: 1547968,
    host_url: 'https://www.airbnb.com/users/show/1547968',
    host_name: 'Ben',
    host_since: '2011-12-29',
    host_location: 'Peachester, Australia',
    host_about: 'I moved to iconic Mango Hill Farm in 2017. Since moving my family and I have rescued dozens of animals and produced seasonal fruit and vegetables for local restaurants.',
    host_response_time: 'within an hour',
    host_response_rate: '100%',
    host_acceptance_rate: '100%',
    host_is_superhost: 'f',
    host_thumbnail_url: 'https://a0.muscache.com/im/pictures/user/30b2d6ec-76b7-4291-ab1f-585017839bd2.jpg?aki_policy=profile_small',     
    host_picture_url: 'https://a0.muscache.com/im/pictures/user/30b2d6ec-76b7-4291-ab1f-585017839bd2.jpg?aki_policy=profile_x_medium',    
    host_neighbourhood: '',
    host_listings_count: 4,
    host_total_listings_count: 4,
    host_verifications: "['email', 'phone']",
    host_has_profile_pic: 't',
    host_identity_verified: 't',
    neighbourhood: '',
    neighbourhood_cleansed: 'Beerwah',
    neighbourhood_group_cleansed: 'Sunshine Coast',
    latitude: -26.84728,
    longitude: 152.86976,
    property_type: 'Farm stay',
    room_type: 'Entire home/apt',
    accommodates: 4,
    bathrooms: 1,
    bathrooms_text: '1 bath',
    bedrooms: 2,
    beds: 2,
    amenities: '["Cooking basics", "Fire extinguisher", "Outdoor dining area", "Air conditioning", "Cleaning products", "Bed linens", "Wine glasses", "Barbecue utensils", "Outdoor furniture", "Smoke alarm", "Kitchen", "First aid kit", "Laundromat nearby", "Essentials", "Ceiling fan", "Heating", "Mini fridge", "Bidet", "Shower gel", "Hot water kettle", "Toaster", "Shampoo", "Luggage dropoff allowed", "Garden view", "Fire pit", "Long term stays allowed", "Hot water", "Dedicated workspace", "Free parking on premises", "Conditioner", "Mountain view", "TV", "Free dryer", "Freezer", "Hair dryer", "Clothing storage", "Wifi", "Shared backyard \\u2013 Fully fenced", "Lockbox", "Dishes and silverware", "Free washer", "Iron", "Stove", "BBQ grill: gas", "Private patio or balcony", "Coffee", "Microwave", "Self check-in", "Refrigerator", "Body soap", "Room-darkening shades", "Cleaning available during stay"]',
    price: '$198.00',
    minimum_nights: 2,
    maximum_nights: 30,
    minimum_minimum_nights: 1,
    maximum_minimum_nights: 2,
    minimum_maximum_nights: 1125,
    maximum_maximum_nights: 1125,
    minimum_nights_avg_ntm: 2,
    maximum_nights_avg_ntm: 1125,
    calendar_updated: '',
    has_availability: 't',
    availability_30: 0,
    availability_60: 0,
    availability_90: 0,
    availability_365: 0,
    calendar_last_scraped: '2024-02-29',
    number_of_reviews: 119,
    number_of_reviews_ltm: 38,
    number_of_reviews_l30d: 0,
    first_review: '2021-07-18',
    last_review: '2024-01-23',
    review_scores_rating: 4.83,
    review_scores_accuracy: 4.83,
    review_scores_cleanliness: 4.63,
    review_scores_checkin: 4.91,
    review_scores_communication: 4.95,
    review_scores_location: 4.92,
    review_scores_value: 4.58,
    license: '',
    instant_bookable: 'f',
    calculated_host_listings_count: 1,
    calculated_host_listings_count_entire_homes: 1,
    calculated_host_listings_count_private_rooms: 0,
    calculated_host_listings_count_shared_rooms: 0,
    reviews_per_month: 3.73
  },
  {
    _id: ObjectId('660dfa89b6515eb205796363'),
    id: 177754,
    listing_url: 'https://www.airbnb.com/rooms/177754',
    scrape_id: Long('20240229002402'),
    last_scraped: '2024-02-29',
    source: 'city scrape',
    name: 'Coolum Ocean Views, 6 guests at no extra cost!',
    description: 'Accommodates up to 7 guests! Beautiful tropical surroundings for privacy. <br />Glorious white surf, sand and ocean views. Wake to a Pacific Sunrise. Beach holidays at your door step.  Watch whales from your deck. Class and style best describe our Holiday House. <br />2 Min WALK TO BEACH, TV in every room, INTERNET, AIRCON, OFF STREET PARKING, DOG FRIENDLY.<br />Bookings are WEEKLY Sat - Sat during school holidays or min of 3 nts booking. 15% discount on request for weekly Bookings outside school holidays.',
    neighborhood_overview: '',
    picture_url: 'https://a0.muscache.com/pictures/11666017/347c8c5d_original.jpg',
    host_id: 850132,
    host_url: 'https://www.airbnb.com/users/show/850132',
    host_name: 'Maureen',
    host_since: '2011-07-21',
    host_location: 'Coolum Beach, Australia',
    host_about: 'We have travelled all over the world and lived in many countries.\n' +
      'We are dog lovers and  offer our holiday house to owners and their pets.',
    host_response_time: 'within a few hours',
    host_response_rate: '100%',
    host_acceptance_rate: '81%',
    host_is_superhost: 't',
    host_thumbnail_url: 'https://a0.muscache.com/im/users/850132/profile_pic/1326064835/original.jpg?aki_policy=profile_small',
    host_picture_url: 'https://a0.muscache.com/im/users/850132/profile_pic/1326064835/original.jpg?aki_policy=profile_x_medium',
    host_neighbourhood: '',
    host_listings_count: 2,
    host_total_listings_count: 2,
    host_verifications: "['email', 'phone']",
    host_has_profile_pic: 't',
    host_identity_verified: 't',
    neighbourhood: '',
    neighbourhood_cleansed: 'Coolum Beach',
    neighbourhood_group_cleansed: 'Sunshine Coast',
    latitude: -26.53614,
    longitude: 153.09206,
    property_type: 'Entire home',
    room_type: 'Entire home/apt',
    accommodates: 7,
    bathrooms: 2,
    bathrooms_text: '2 baths',
    bedrooms: 3,
    beds: 5,
    amenities: '["Backyard", "Lockbox", "Wine glasses", "Dishwasher", "Hot water kettle", "High chair", "Hangers", "Freezer", "Oven", "Baby safety gates", "Cooking basics", "Bathtub", "Crib - available upon request", "Hot water", "Outdoor furniture", "Coffee maker: espresso machine", "Washer", "Self check-in", "Bed linens", "Children\\u2019s books and toys", "Free parking on premises", "Smoking allowed", "Microwave", "Pets allowed", "Board games", "Dryer", "Rice maker", "Sea view", "Iron", "Extra pillows and blankets", "Drying rack for clothing", "Mini fridge", "Central heating", "Stove", "Clothing storage: walk-in closet", "Central air conditioning", "Wifi", "Ceiling fan", "Barbecue utensils", "Long term stays allowed", "Dishes and silverware", "Blender", "65\\" TV with standard cable", "Cleaning products", "Laundromat nearby", "Beach view", "Public or shared beach access", "Dedicated workspace", "Free street parking", "Private entrance", "Toaster", "Hair dryer", "Books and reading material", "Dining table", "Outdoor dining area", "Refrigerator", "Window guards", "Patio or balcony", "Room-darkening shades", "BBQ grill", "Kitchen", "Ocean view", "Smoke alarm"]',
    price: '$360.00',
    minimum_nights: 3,
    maximum_nights: 60,
    minimum_minimum_nights: 3,
    maximum_minimum_nights: 7,
    minimum_maximum_nights: 60,
    maximum_maximum_nights: 60,
    minimum_nights_avg_ntm: 3.6,
    maximum_nights_avg_ntm: 60,
    calendar_updated: '',
    has_availability: 't',
    availability_30: 14,
    availability_60: 44,
    availability_90: 74,
    availability_365: 319,
    calendar_last_scraped: '2024-02-29',
    number_of_reviews: 47,
    number_of_reviews_ltm: 6,
    number_of_reviews_l30d: 0,
    first_review: '2012-02-05',
    last_review: '2024-01-20',
    review_scores_rating: 4.74,
    review_scores_accuracy: 4.74,
    review_scores_cleanliness: 4.87,
    review_scores_checkin: 4.83,
    review_scores_communication: 4.78,
    review_scores_location: 4.85,
    review_scores_value: 4.68,
    license: '',
    instant_bookable: 'f',
    calculated_host_listings_count: 2,
    calculated_host_listings_count_entire_homes: 2,
    calculated_host_listings_count_private_rooms: 0,
    calculated_host_listings_count_shared_rooms: 0,
    reviews_per_month: 0.32
  },
  {
    _id: ObjectId('660dfa89b6515eb205796365'),
    id: 368309,
    listing_url: 'https://www.airbnb.com/rooms/368309',
    scrape_id: Long('20240229002402'),
    last_scraped: '2024-02-29',
    source: 'city scrape',
    name: 'Magical Malindi,  Montville. QLD',
    description: '',
    neighborhood_overview: '',
    picture_url: 'https://a0.muscache.com/pictures/miso/Hosting-368309/original/efcf4b66-6229-4330-91fb-f00258283e4d.jpeg',
    host_id: 603365,
    host_url: 'https://www.airbnb.com/users/show/603365',
    host_name: 'Tony & Patty',
    host_since: '2011-05-19',
    host_location: 'Montville, Australia',
    host_about: 'We are both semi-retired and live in a beautiful part of SE Queensland. \n' +
      'We have four children, one son, three daughters and six grandchildren. \n' +
      'Our main interests are our family, gardening, healthy living and eating and travelling.\n' +
      'We travel regularly to the UK to visit our son and one of our daughters living there. \n' +
      'We then love to hire a car and travel to the continent to explore and always stay in Airbnbs. This allows us to be flexible and cook our own meals.\n' +
      'South America is also one of our favourite destinations and we have visited there twice.\n' +
      'We enjoy sharing our home and meeting so many lovely people. \n' +
      'Our experiences have been nothing but positive. \n',
    host_response_time: 'within an hour',
    host_response_rate: '100%',
    host_acceptance_rate: '92%',
    host_is_superhost: 't',
    host_thumbnail_url: 'https://a0.muscache.com/im/users/603365/profile_pic/1423523725/original.jpg?aki_policy=profile_small',
    host_picture_url: 'https://a0.muscache.com/im/users/603365/profile_pic/1423523725/original.jpg?aki_policy=profile_x_medium',
    host_neighbourhood: '',
    host_listings_count: 1,
    host_total_listings_count: 1,
    host_verifications: "['email', 'phone']",
    host_has_profile_pic: 't',
    host_identity_verified: 't',
    neighbourhood: '',
    neighbourhood_cleansed: 'Caloundra Hinterland',
    neighbourhood_group_cleansed: 'Sunshine Coast',
    latitude: -26.71549,
    longitude: 152.88951,
    property_type: 'Entire home',
    room_type: 'Entire home/apt',
    accommodates: 10,
    bathrooms: 3.5,
    bathrooms_text: '3.5 baths',
    bedrooms: 4,
    beds: 6,
    amenities: '["Backyard", "Carbon monoxide alarm", "Private pool", "Dishwasher", "Luggage dropoff allowed", "High chair", "Hangers", "Oven", "Shampoo", "Cooking basics", "Fire extinguisher", "Hot water", "Outdoor furniture", "Washer", "Bed linens", "Free parking on premises", "Microwave", "Dryer", "Coffee maker: Nespresso", "Iron", "Extra pillows and blankets", "Stove", "Wifi", "Long term stays allowed", "Dishes and silverware", "First aid kit", "Air conditioning", "Heating", "Private patio or balcony", "TV with standard cable", "Hair dryer", "Essentials", "Refrigerator", "BBQ grill", "Kitchen", "Lake access", "Coffee", "Smoke alarm"]',
    price: '$646.00',
    minimum_nights: 2,
    maximum_nights: 1125,
    minimum_minimum_nights: 2,
    maximum_minimum_nights: 2,
    minimum_maximum_nights: 1125,
    maximum_maximum_nights: 1125,
    minimum_nights_avg_ntm: 2,
    maximum_nights_avg_ntm: 1125,
    calendar_updated: '',
    has_availability: 't',
    availability_30: 12,
    availability_60: 26,
    availability_90: 43,
    availability_365: 195,
    calendar_last_scraped: '2024-02-29',
    number_of_reviews: 354,
    number_of_reviews_ltm: 51,
    number_of_reviews_l30d: 3,
    first_review: '2013-01-01',
    last_review: '2024-02-24',
    review_scores_rating: 4.96,
    review_scores_accuracy: 4.96,
    review_scores_cleanliness: 4.92,
    review_scores_checkin: 4.99,
    review_scores_communication: 4.99,
    review_scores_location: 4.97,
    review_scores_value: 4.87,
    license: '',
    instant_bookable: 'f',
    calculated_host_listings_count: 1,
    calculated_host_listings_count_entire_homes: 1,
    calculated_host_listings_count_private_rooms: 0,
    calculated_host_listings_count_shared_rooms: 0,
    reviews_per_month: 2.6
  },
```
3. - choose two hosts (by reffering to their `host_id` values) who are superhosts (available in the `host_is_superhost` field), and show all of the listings offered by both of the two hosts
```
db.listings.find({$or:[{host_id: 5926852},{host_id: 8761644}], host_is_superhost: "t"},{name:1, _id:0, price:1, neighbourhood: 1, host_name:1, host_is_superhost:1})
```
```
[
  {
    name: 'Townhouses in Central Noosa Parade Location',
    host_name: 'Nautilus',
    host_is_superhost: 't',
    neighbourhood: 'Noosa Heads, Queensland, Australia',
    price: '$210.00'
  },
  {
    name: 'The Shack Noosa - Heated Pool, Beach House',
    host_name: 'Holiday Homes@Noosa',
    host_is_superhost: 't',
    neighbourhood: 'Noosa Heads, Queensland, Australia',
    price: '$359.00'
  },
  {
    name: 'Noosa Rest - Amazing Sunset Views of Noosa River',
    host_name: 'Holiday Homes@Noosa',
    host_is_superhost: 't',
    neighbourhood: 'Noosa Heads, Queensland, Australia',
    price: '$323.00'
  },
```
  - Both these superhosts have their footprint in the Noosa Heads neighbourhood
   
4. - find all the unique `host_name` values
```
db.listings.distinct("host_name")
```
```
[
  'A',
  'A S Coastal',
  'AJ & Nethmie',
  'Aaron',
  'Abbey',
  'Abby-Rose',
  'Abi',
  'Abizer',
```
  
5. - find all of the places that have more than 2 `beds` in a neighborhood of your choice (referred to as either the `neighborhood` or `neighbourhood_group_cleansed` fields in the data file), ordered by `review_scores_rating` descending
```
db.listings.find({neighbourhood_group_cleansed: "Noosa", beds: {$gte :2}, review_scores_rating: {$ne:''}},{name:1, _id:0, beds:1, review_scores_rating:1, price:1}).sort({"review_scores_rating":-1}).pretty()
```
```
[
  {
    name: 'Almost Surf Side! - Little Cove & National Park',
    beds: 4,
    price: '$300.00',
    review_scores_rating: 5
  },
  {
    name: 'Entire House in Noosa Heads',
    beds: 3,
    price: '$262.00',
    review_scores_rating: 5
  },
  {
    name: 'Noosa - Pet friendly home at Castaways Beach',
    beds: 5,
    price: '$536.00',
    review_scores_rating: 5
  },
```
  - A lot of 5 star reviews! Almost Surf Side! - Little Cove & National Park, gives a less pricey option for 4 beds with great reivews.

6. - show the number of listings per host
```
db.listings.aggregate([{$group:{_id: "$host_name", listingcount :{$sum: 1}}}]).pretty().sort({listingcount: -1})
```
```
[
  { _id: 'Niche Holidays', listingcount: 121 },
  { _id: 'Accom Caloundra', listingcount: 108 },
  { _id: 'Aspire Property Management', listingcount: 94 },
  { _id: 'Melanie And Verena', listingcount: 88 },
```
  - Niche Holidays is the biggest business in Sunshine Coast when it comes to Airbnb! 

7. - find the average `review_scores_rating` per neighborhood, and only show those that are `4` or above, sorted in descending order of rating (see [the docs](https://docs.mongodb.com/manual/reference/operator/aggregation/sort/))
```
db.listings.aggregate([{$group:{_id: "$neighbourhood_cleansed", average_rating: {$avg: "$review_scores_rating"}}},{$match:{average_rating:{$gte: 4}}}, {$sort: {average_rating: -1}}])
```
```
 [
  { _id: 'Glass House Mountains', average_rating: 4.908695652173913 },
  { _id: 'Caloundra Hinterland', average_rating: 4.908339100346021 },
  { _id: 'Eumundi - Yandina', average_rating: 4.899937888198758 },
  { _id: 'Diddillibah - Rosemount', average_rating: 4.898333333333333 },
  { _id: 'Peregian Springs', average_rating: 4.897659574468085 },
  { _id: 'Noosa Hinterland', average_rating: 4.891152416356878 },
```
  - Glass House Mountains neighbourhood has a lot of great options, with rave reviews!!

