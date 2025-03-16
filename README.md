doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="initial-scale=1, maximum-scale=1, user-scalable=no" />
  <title> Hello AGOL</title>

  <style>
    html,
    body,
    #viewDiv {
      padding: 0;
      margin: 0;
      height: 100%;
      width: 100%;
    }
 /* I ended up editing this code because last time i did not call it correctly */   
  </style>
  <link rel="stylesheet" href="https://js.arcgis.com/4.25/esri/themes/light/main.css">
  <script src="https://js.arcgis.com/4.25/"></script>

</head>
<body>
  <div id="viewDiv"></div>
  <script>
    require([
    "esri/config",
    "esri/Map", 
    "esri/views/MapView",
    "esri/layers/GraphicsLayer",
    "esri/Graphic"
  ],

    /*adding graphic and graphicslayer */
    function(esriConfig, Map, MapView, GraphicsLayer, Graphic) {
      esriConfig.apiKey = "AAPTxy8BH1VEsoebNVZXo8HurKQVP8PWOfxuzYjdMuIGk7u1YyVthU1o8lLnxj2ur8dpMAL8Ub55z1RthTyo1-hIZGKRh5lFlMauHG5LDn2OaPJiBoJQ-8rBWW8nBPgjYAXvXdfhRmL5J4z0eXtsV9h3o9czM07mdtIeJBXPCZ5p0jmBC5rCp4hRr2JK5YDaaxguEukDHTdig7Nr485_uIj97SL6EXuPhwk4BsLQH5nwe0A.AT1_zi3VeksP";
      const map = new Map({
        basemap: "satellite" // Basemap layer service
      });

      const view = new MapView({
      map: map,
      center: [-81.613951, 27.243914], // Longitude, latitude
      zoom: 17.5, // Zoom level
      container: "viewDiv" // Div element
      });

      const graphicsLayer = new GraphicsLayer();
      map.add(graphicsLayer);

  const polygon = { //Create a polygon  
  type: "polygon", 
  rings: [  
    [-81.613677, 27.242217], // long, lat 
    [-81.613697, 27.245482],  
    [-81.614283, 27.245513],  
    [-81.614278, 27.242235] 
  ] 
  };

  const simpleFillSymbol = {  
  type: "simple-fill",
  color: [227, 139, 79, 0.8],  // Color of the polygon
  outline: {  
    color: [255, 255, 255], // White  
    width: 1
  }
};  

const popupTemplate = {  
  title: "Soil Health Zone",  
  content: "Soil Health in Citrus Groves"  
};
 
const polygonGraphic = new Graphic({  
  geometry: polygon,  
  symbol: simpleFillSymbol, 
  popupTemplate: popupTemplate,
});

graphicsLayer.add(polygonGraphic);

    });
    
    </script>

  </body>

</html>

