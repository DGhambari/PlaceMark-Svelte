<script>
  import Main from "./pages/Main.svelte"
  import Login from "./pages/Login.svelte"
  import Signup from "./pages/Signup.svelte"
  import About from "./pages/About.svelte"
  import Dashboard from "./pages/Dashboard.svelte"
  import Placemark from "./pages/Placemark.svelte"
  import PointOfInterest from "./pages/PointOfInterest.svelte"
  import Map from "./pages/Map.svelte";
  import Charts from "./pages/Charts.svelte";
  import Router from "svelte-spa-router";
  import { PlacemarkService } from "./services/PlacemarkService";
  import { setContext } from "svelte";

  let routes = {
    "/": Main,
    "/main": Main,
    "/login": Login,
    "/signup": Signup,
    "/about": About,
    "/dashboard": Dashboard,
    "/placemark": Placemark,
    "/map": Map,
    "/pointofinterest": PointOfInterest,
    "/charts": Charts,
  }

setContext("PlacemarkService", new PlacemarkService("http://localhost:4000"));

</script>

<Router {routes}/>

