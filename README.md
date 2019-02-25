<html>
<head>
    <title> leaflet map </title>

    <!-- External Stylesheets -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.0.3/dist/leaflet.css" />

</head>
<body>
    <!--our web map and content will go here-->
   <!-- Add the Leaflet JavaScript library -->
    <script src="https://unpkg.com/leaflet@1.0.3/dist/leaflet.js"></script>

    <div id="map" style="width: 1000px; height: 705px"></div>
<script>
	var planes = [
	["Nnamdi Azikiwe international airport",9.006790,7.263169],
	["Murtala Muhammed international airport", 6.577370,3.32116],
	["Port Harcout internation airport",5.015490,6.94959],
	["Mallam Aminu international airport", 12.047599,8.52462], 
	["Makudi Airport",7.703879,8.61394],
	["Margaret Ekpo international airport", 4.976019,8.3472],
	["point 1",9.057944,7.458670],
	["point 2", 9.058562,7.477187],
	["point 3 ",9.059517,  7.498490]
	];
	
    // Create variable to hold map element, give initial settings to map
    var map = L.map('map',{ center: [ 9.036992, 7.445568], zoom: 14});

// Add OpenStreetMap tile layer to map element
googleSat =L.tileLayer('http://{s}.google.com/vt/lyrs=s&x={x}&y={y}&z={z}',{
    maxZoom: 20,
    subdomains:['mt0','mt1','mt2','mt3']
}).addTo(map);
googleTerrain = L.tileLayer('http://{s}.google.com/vt/lyrs=p&x={x}&y={y}&z={z}',{
    maxZoom: 20,
    subdomains:['mt0','mt1','mt2','mt3']
}).addTo(map);
var baseMaps = {
    "googleSat": googleSat,
    "googleTerrain": googleTerrain
};
L.control.layers(baseMaps).addTo(map);


// add circle by passing center, radius, and some basic styles
    L.circle([9.059517,  7.498490], 400,{color:'yellow',opacity:1,fillColor: 'blue',fillOpacity:.4}).addTo(map);
    
    
for (var i = 0; i < planes.length; i++) {
			marker = new L.marker([planes[i][1],planes[i][2]])
				.bindPopup(planes[i][0])
				.addTo(map);
		}
</script>
<script> // create a red polyline from an array of LatLng points
var latlngs = [
    [  9.057944,   7.458670],
    [  9.058562,  7.477187],
    [  9.059517,  7.498490]
];
var polyline = L.polyline(latlngs, {color: 'red'}).addTo(map);
</script>


</body>
</html>
