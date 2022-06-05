<script>
  import {createEventDispatcher, getContext, onMount} from "svelte";
  import Coordinates from "./Coordinates.svelte";

  const dispatch = createEventDispatcher();
  const placemarkService = getContext("PlacemarkService");

  let pointOfInterestList = [];
  let category = "";
  let place = "";
  let lat = 52.160858;
  let lng = -7.152420;
  let message = "Add a Point of Interest";

  onMount(async () => {
    pointOfInterestList = await placemarkService.getPointsOfInterest()
  });

  async function addPointOfInterest() {
    const category = pointOfInterestList[0].category;
    const place = pointOfInterestList[0].place;
    const pointOfInterest = {
      category: category,
      place: place,
      lat: lat,
      lng: lng
    };
    const success = await placemarkService.addPointOfInterest(pointOfInterest);
    if (!success) {
      message = "Placemark not completed - some error occurred";
      return;
    }
    message = `Success!`;
    dispatch("message", {
      pointOfInterest: pointOfInterest,
    });
    }
</script>

<form on:submit|preventDefault={addPointOfInterest}>
  <div class="field">
    <label class="label" for="amount">Enter Category</label> <input bind:value={category} class="input" id="category"
                                                                  name="category" placeholder="Enter Category" type="text">
  </div>
  <div class="field">
    <label class="label" for="amount">Enter Place</label> <input bind:value={place} class="input" id="place"
                                                                  name="place" placeholder="Enter place" type="text">
  </div>
  <div class="field">
    <label class="label" for="amount">Enter Latitude</label> <input bind:value={lat} class="input" id="latitude"
                                                                  name="latitude" placeholder="Enter latitude" type="text">
  </div>
  <div class="field">
    <label class="label" for="amount">Enter Longitude</label> <input bind:value={lng} class="input" id="longitude"
                                                                  name="longitude" placeholder="Enter longitude" type="text">
  </div>

  <Coordinates bind:lat={lat} bind:lng={lng}/>
  <div class="field">
    <div class="control">
      <button class="button is-link is-dark">Add Placemark</button>
    </div>
  </div>
  <div class="section">
  </div>
</form>