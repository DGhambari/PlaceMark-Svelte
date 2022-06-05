<script>
  import {getContext, onMount} from 'svelte'

  const placemarkService = getContext("PlacemarkService");
  let placemarkList = [];

  onMount(async () => {
    placemarkList = await placemarkService.getPlacemarks();
  });
</script>

<table class="table is-fullwidth">
  <thead>
    <th>Title</th>
  </thead>
  <tbody>
    {#each placemarkList as placemark}
      <tr>
        <td>
          {placemark.title}
        </td>
      </tr>
    {/each}
  </tbody>
</table>
