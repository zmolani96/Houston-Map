http://zmolani96.github.io/Houston-Map

# Houston-Map
VMD Houston interactive map 
<!DOCTYPE html>
<html>
  <head>
  <style>
    #map-canvas { width:500px; height:400px; }
    .layer-wizard-search-label { font-family: sans-serif };
  </style>
  <script type="text/javascript"
    src="http://maps.google.com/maps/api/js?sensor=false">
  </script>
  <script type="text/javascript">
    var map;
    var layer_0;
    var layer_1;
    function initialize() {
      map = new google.maps.Map(document.getElementById('map-canvas'), {
        center: new google.maps.LatLng(29.73453737640685, -95.38959207001948),
        zoom: 11,
        mapTypeId: google.maps.MapTypeId.ROADMAP
      });
      layer_0 = new google.maps.FusionTablesLayer({
        query: {
          select: "col7",
          from: "1xpsHP9tP6QnrtkXvBnmjgkaIACn6PslNERcyzARp"
        },
        map: map,
        styleId: 5,
        templateId: 8
      });
      layer_1 = new google.maps.FusionTablesLayer({
        query: {
          select: "col7",
          from: "1TPT2rvLOcBez7F6PakAfSc-b75TIwAcXdRpUfXzq"
        },
        map: map,
        styleId: 2,
        templateId: 2
      });
    }
    function changeMap_0() {
      var whereClause;
      var searchString = document.getElementById('search-string_0').value.replace(/'/g, "\\'");
      if (searchString != '--Select--') {
        whereClause = "'CountyName' = '" + searchString + "'";
      }
      layer_0.setOptions({
        query: {
          select: "col7",
          from: "1xpsHP9tP6QnrtkXvBnmjgkaIACn6PslNERcyzARp",
          where: whereClause
        }
      });
    }
    google.maps.event.addDomListener(window, 'load', initialize);
  </script>
  </head>
  <body>
    <div id="map-canvas"></div>
    <div style="margin-top: 10px;">
      <label class="layer-wizard-search-label">
        County Name
        <select id="search-string_0" onchange="changeMap_0(this.value);">
          <option value="--Select--">--Select--</option>
          <option value="BRAZORIA">BRAZORIA</option>
          <option value="CHAMBERS">CHAMBERS</option>
          <option value="FORT BEND">FORT BEND</option>
          <option value="GALVESTON">GALVESTON</option>
          <option value="HARRIS">HARRIS</option>
          <option value="LIBERTY">LIBERTY</option>
          <option value="MONTGOMERY">MONTGOMERY</option>
          <option value="WALLER">WALLER</option>
        </select>
      </label> 
    </div>
  </body>
</html>
