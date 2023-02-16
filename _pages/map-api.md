---
layout: categories
permalink: /map/
title: Near Me Finder
search_exclude: true
---
<script>
  
  var raw = "";

var requestOptions = {
  method: 'POST',
  body: raw,
  redirect: 'follow'
};

fetch("http://10.8.134.131:8089/api/users/", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
</script>

<!--- CSS Styling Sheet-->
<style>

.row {
  align-items: center;
  display: flex;
}
#map {
      height: 700px; /* The height is 400 pixels */
      width: 100%; /* The width is the width of the web page */
}

.column {
  flex: 33.33%;
  padding: 5px;
}
</style>

## Near Me Finder
#### Use the map below to find important locations in your area. If you look in the bottom right of the map there is a person you can drag and place any where on the map and you can get a 360 view of your selected location (it also tells you the name of the selected location in the top left.) You can use <a href='https://cubnavarro.github.io/Tri2GroupFastpages/markdown/'><button>THIS</button></a> to plan your activities!
<div id="map"></div>

<script src="https://maps.googleapis.com/maps/api/js?key=AIzaSyD0erTF9F5UoSk6YZ4wIWNg0j7vbkSXGcw&callback=initMap&v=weekly" defer></script>
    
<script>                              
      // Initialize and add the map
      function initMap() {
        // The location of Borrego Springs
        var sd = { lat: 32.986370, lng: -117.023491 };

        var map = new google.maps.Map(document.getElementById("map"), {
          zoom: 9,  
          center: sd,
        });

        var markers = [
          {
          coords : {lat: 32.832809, lng: -117.271271}, 
          content: '<p style="color:blue;">House 1-La Jolla</p>' 
          },
          {
          coords : {lat: 32.999780, lng: -117.257200}, 
          content: '<p style="color:blue;">House 2-North Pacific Beach</p>'  
          }, 
          {
          coords : {lat: 32.713631, lng: -117.155602}, 
          content: '<p style="color:blue;">House 3-Downtown San Diego</p> '  
          }, 
          {  
          coords : {lat: 33.158350, lng: -117.032630}, 
          content: '<p style="color:blue;"> Daves Hot Chicken (Food)</p>'  
          }, 
          {
          coords : {lat: 32.912239, lng: -117.147217}, 
          content: '<p style="color:blue;">Raising Canes (Food)</p>'  
          },
          {
          coords : {lat: 32.769939, lng: -117.251091}, 
          content: '<p style="color:blue;">Belmont Park (Activity)</p>'  
          },
          {
          coords : {lat: 33.010290, lng: -116.947480}, 
          content: '<p style="color:blue;">Potato Chip Rock (Activity)</p>'  
          },
	
        ];
      
        // Loop through markers 
        for(var i = 0; i < markers.length; i++) { 
          addMarker(markers[i]); 
        }
                                          
        // Add Marker 
        function addMarker(props){ 
          var marker =  new google.maps.Marker({ 
            position:props.coords, 
            map:map, 
          });

          if(props.content) { 
               var infoWindow = new google.maps.InfoWindow({ 
              content:props.content 
               });
            infoWindow.open(map, marker);
            marker.addListener( 'click', function(){ 
              infoWindow.open(map, marker); 
            });
          }
        }                                          
      }

      window.initMap = initMap;
</script>
<br/>
<br/>
<br/>
<div id="map1"></div>