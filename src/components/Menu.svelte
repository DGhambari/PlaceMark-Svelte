<script>
  import PlacemarkBrand from "../components/PlacemarkBrand.svelte";
</script>

<nav class="navbar">
  <div class="navbar-brand">
    <PlacemarkBrand/>
  </div>
  <a role="button" class="navbar-burger" data-target="navMenu" aria-label="menu" aria-expanded="false"> <span aria-hidden="true"></span>
    <span aria-hidden="true"></span> <span aria-hidden="true"></span> </a>
  <div class="navbar-menu" id="navMenu">
    <div class="navbar-end">
      <div class="navbar-item">
        <div class="buttons">
          <a id="dashboard" class="button" href="/dashboard"> Dashboard </a> 
          <a id="about" class="button" href="/#/about"> About </a> 
          <a id="map" class="button" href="/#/map"> Map </a>
          <a id="charts" class="button" href="/#/charts"> Charts </a>
          <a id="logout" class="button" href="/logout"> Logout </a>
        </div>
      </div>
    </div>
  </div>
</nav>

