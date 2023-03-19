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


## Google Map API

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

    maps = googlemaps.Client(key=YOUR_API_KEY )
    result = maps.geocode('成大’)
    
Convert coordinates and addresses to each other:

    maps = googlemaps. Client(key=YOUR_API_KEY )
    result = maps.geocode('Chengdu')
    
Finally geocode_location gets (22.9988416,120.2195148).

***2. Distance Matrix API***

Calculate the path length and travel time of all point-to-point in the list.

    maps = googlemaps. Client(key=YOUR_API_KEY )
    result = maps.distance_matrix(location latitude and longitude list)

***3. Places API***

    maps = googlemaps.Client(key=YOUR_API_KEY )
    result = maps.places_nearby(location=(lat,lng), radius=,type=)

  Return format: Json
  
  Common optional parameters: type (the type of location to search for)
  
▌Show in Google Map
  
  Installation kit (installed during environment setup)
  
    pip install gmaps
    jupyter nbextension enable --py gmaps

  P.S. It is confirmed that it can be displayed in jupyter notebook, jupyter lab has not tested

***3. Geocoding API***

***4. Maps JavaScript API***

***5. Places API***


## Web-Crawler

1. *`2022_Jun-Sep_降雨量(mm)_分景點_小雨1,大雨2,強雨3.csv`*: Rainfall Data.


## Results

  ![image](Isochrone.PNG)   
 
  * Isochrones of tourist attractions
  
  ![image](Weather_Station_Voronoi.PNG)   

  * Voronoi regions of Tainan weather station
