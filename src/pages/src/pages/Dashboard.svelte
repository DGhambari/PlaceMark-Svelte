<script>
  import Menu from "../components/Menu.svelte";
  import ListPlacemarks from "../components/ListPlacemarks.svelte";
  import AddPlacemark from "../components/AddPlacemark.svelte";
  import PlacemarkMap from "../components/PlacemarkMap.svelte";
  // import Map from "../components/Map.svelte";
  import Analytics from "../components/Analytics.svelte";
  import {getContext} from "svelte";

  const placemarkService = getContext("PlacemarkService");
  placemarkService.logout();
</script>

<Menu/>

<section class="section">
  <ListPlacemarks/>
  <!-- <MapBox/> -->
  <PlacemarkMap/>
    <center><Analytics/></center>
  <br>
  <AddPlacemark/>
</section>
