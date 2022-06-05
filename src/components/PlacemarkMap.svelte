<script>
    import 'leaflet/dist/leaflet.css';
    import {LeafletMap} from '../services/leaflet-map';
    import {getContext, onMount} from "svelte";

    const placemarkService = getContext("PlacemarkService");
  
    const mapConfig = {
      location: {lat: 53.1424, lng: -7.6921},
      zoom: 7,
      minZoom: 1,
    }; 
    let map = null;
  
    onMount(async () => {
      const map = new LeafletMap("placemark-map", mapConfig);
      map.showZoomControl();
      map.addLayerGroup('Placemarks');
      map.showLayerControl();

    const pointsOfInterest = await placemarkService.getPointsOfInterest();
        pointsOfInterest.forEach(pointOfInterest => {
        addPlacemarkMarker(pointOfInterest);
        });
    });

    function addPlacemarkMarker(pointOfInterest) {
        const pointOfInterestStr = `${pointOfInterest.category} ${pointOfInterest.place}`;
        map.addMarker({lat: pointOfInterest.lat, lng: pointOfInterest.lng}, pointOfInterestStr, "Placemarks");
  }
  </script>
  
  <div class="box" id="placemark-map" style="height:800px" >
  </div>