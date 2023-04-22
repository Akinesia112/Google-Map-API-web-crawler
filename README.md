# Google-Map-API-web-crawler

## Introduction

***Integration Plan of "Southern Tainan Suburb Center and Surrounding Areas" in East District of Tainan City***

**(臺南市東區南臺南副都心與周邊地區整合計畫)** [Website Link](https://www.behance.net/gallery/166339751/Integration-Plan-of-Southern-Tainan-Suburb-Center-Area)

The planning area is located in the southwest of the East District of Tainan City, including Zhongxiao Vil., Dade Vil., Dafu Vil., and Chongming Vil. in the East District, with an area of about 143.427 hectares (accounting for about 11% of the East District).
The core of the planning area mainly takes the Cultural Center as the cultural base, and the Southern Tainan Station of the Taiwan Railway as the Suburb Center node, adjacent to Provincial Highway No. 1, and is an important transportation hub connecting the Southern District and Rende District in Tainan City.

Surrounded by many living circles, it should be suitable for the mixed residential and commercial development. However, the planning scope is mainly for residential use, supplemented by commercial use, and the characteristics of the Suburb Center location within the planning scope are not fully utilized. It is planned to use the new public transportation station to attract crowds, so that the wholesale and retail industries in the rezoned area can be activated, and then combined with the Future Science Museum, Tainan's Barclay Memorial Park, and the park green belt after the underground railway will be established in the future Tainan Suburb Center.

The planning area will be suitable for the circular green belt corridor for recreation, combined with the convenient transportation brought by the future construction of the MRT Blue Line and the integration of commerce at the station, the use of commercial areas will be activated to attract people to live and work here, and it is also suitable for local residents rest and live at Tainan Suburb Center.

In addition, planned changes will be made to the urban physical environment, industrial structure, functions, and land use to bring new vitality to the old settlements, and the new rezoning areas will be both livable and convenient, so as to improve the built environment of urban life, revitalize the local economy, strengthen the connection role of Suburb Center to promote the sustainable development of Tainan City and the East District.

Fig 1 Analysis Demo
  ![image](Analysis_Demo.jpg)


## Google Map API: Take NCKU as Example

1. Directions API - Route Planning
2. Distance Matrix API - Calculation of Distance and Travel Time
3. Geocoding API - Convert Coordinates and Addresses
4. Maps JavaScript API - Customize the Interactive Map
5. Places API - Location Search

▌Http URL Request

Evample：

https://maps.googleapis.com/maps/api/place/nearbysearch/json?location=22.9988416,120.2195148&radius=1000&type=restaurant&key=AIzaSyBZ2Z5rAD6S1MvdQOMg-5YqRZeBXYI6UXU

Example parameters:

    - location=22.9988416,120.2195148
    - radius=1000
    - type=restaurant
    - key=AIzaSyBZ2Z5rAD6S1MvdQOMg-5YqRZeBXYI6UXU (change your own Key)
    
Wrap Http URL Request into function form:
    
    pip install googlemaps (installed when setting up the environment)

***1.Geocoding API***

https://maps.googleapis.com/maps/api/geocode/json?address=成大&key=YOUR_API_KEY
    
Convert coordinates and addresses to each other:

    maps = googlemaps. Client(key=YOUR_API_KEY )
    result = maps.geocode('成大')
    
Finally geocode_location gets (22.9988416,120.2195148).

***2. Distance Matrix API***

Calculate the path length and travel time of all point-to-point in the list.

    maps = googlemaps. Client(key=YOUR_API_KEY )
    result = maps.distance_matrix(location latitude and longitude list)

***3. Places API***

    maps = googlemaps.Client(key=YOUR_API_KEY )
    result = maps.places_nearby(location=(lat,lng), radius=,type=)
    
    Required parameters:
    - Location : the center of the search range (latitude and longitude)
    - Radius : the radius of the search area (m)
    - Return format: Json 
    - Common optional parameters: type (the type of location to search for)

  Return the result after calling with URL, and then use Python to parse the data.
  
▌Show in Google Map
  
  Installation kit (installed during environment setup)
  
    pip install gmaps
    jupyter nbextension enable --py gmaps

  P.S. It is confirmed that it can be displayed in jupyter notebook, jupyter lab has not tested
  
▌Add Marker

Search for the latitude and longitude of NCKU, find the latitude and longitude from the returned results, and mark the found points on google maps through gmaps.

![image](Add_Marker.png)
  
▌Add Heat Map

Use the number of ratings to present the heat map of crawling locations.

Set the latitude and longitude of all locations in the DataFrame, the maximum display value of the heat map and the radius of the points in the heat map.

![image](Add_Heat_Map.png)

▌Add Directions

![image](Add_Directions.png)

▌Route Planning

Use the top five locations with the highest ratings to plan the route.

Put the latitude and longitude of the top 5 restaurants with the highest number of comments into the array, create gmaps, set the latitude and longitude of the starting point, end point, and passing point, and calculate the total distance and time spent through another function. 

From the starting point of NCKU, pass through in sequence according to the order of the first five high places.

![image](Route_Planning.png)

▌Crawl the Popular Times of a Place

Enter the id of the place (the previous crawler has storage), return the result as the 24-hour popularity of each 7 days a week, add up the hourly popularity of the 7 days, and draw the summed 24-hour popularity as a long bar picture

![image](Popular_Times.png)


## Web-Crawler

Python sends a Get request, returns the webpage data and analyzes it with Python.

Use the get method of requests to grab the webpage, and the text attribute is the html file, specify html.parser as the parser, and grab <a></a>.

  ![image](Crawler.png)   
 
