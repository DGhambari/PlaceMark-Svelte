<script>
    import Menu from "../components/Menu.svelte";
    import Chart from 'svelte-frappe-charts';
  
    let data = {
      labels: ['Sun', 'Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
      datasets: [
        {
          values: [10, 12, 3, 9, 8, 15, 9]
        }
      ]
    };
  </script>

<Menu/>
<br>  
<div class="columns">
  <div class="column box has-text-centered">
    <h1 class="title is-4">Total Placemarks</h1>
    <Chart data={data} type="line" />
  </div>
</div>