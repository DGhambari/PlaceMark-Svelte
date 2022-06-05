<script>
  import {getContext, onMount} from 'svelte'

  const placemarkService = getContext("PlacemarkService");
  export let placemarkList = [];

  onMount(async () => {
    placemarkList = await placemarkService.getPlacemarks();
  });

</script>

<table class="table is-fullwidth">
  <thead>
    <tr>
      <th>Category</th>
      <th>Point of Interest</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    {#each placemark.pointOfInterests as poi}
      <tr>
        <td>
          {poi.category}
        </td>
        <td>
          {poi.place}
        </td>
        <td>
          {poi.lat}
        </td>
        <td>
          {poi.lng}
        </td>
        <td>
          <a href="/pointOfInterest/{{../placemark._id}}/editpointOfInterest/{{_id}}" class="ui icon button">
            <i class="fas fa-edit"></i>
          </a>
        </td>
        <td>
          <a href="/placemark/{{../placemark._id}}/deletepointOfInterest/{{_id}}" class="ui icon button">
            <i class="fas fa-trash"></i>
          </a>
        </td>
      </tr>
    {{/each}}
  </tbody>
</table>
