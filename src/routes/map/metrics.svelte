<script lang="ts">
    import { onMount } from 'svelte';

    let latitude:any = null;
  
    async function fetchLatitude() {
      try {
        const response = await fetch('https://api.zippopotam.us/us/90310');
        const data = await response.json();
        latitude = data.places[0].latitude;
              console.log('Latitude:', latitude);
      } catch (error) {
        console.error(error);
      }
    }
  
    onMount(() => {
      setInterval(fetchLatitude, 1000);
      fetchLatitude();
    });
  </script>
  
  <div class="metrics container">
    <h6 class="head text-center pt-2">Metrics</h6>
    <div class="figs text-center" style="margin-right: 1em;">
      <div class="row text-center">
        <div class="col">
          Velocity
          <p id="velocity">0</p>
        </div>
        <div class="col">
          Longitude
          <p class="Longitude">0</p>
        </div>
      </div>
      <div class="row text-center">
        <div class="col">
          Latitude
          {#if latitude !== null}
            <p class="latitude">{latitude}</p>
          {:else}
            <p>Loading...</p>
          {/if}
        </div>
        <div class="col">
          Altitude
          <p class="Altitude">0</p>
        </div>
      </div>
      <div class="row text-center">
        <div class="col">
          Heading
          <p class="heading">0</p>
        </div>
        <div class="col">
          Yaw (Degree)
          <p class="yaw">0</p>
        </div>
      </div>
    </div>
  </div>
  
  <style>
    .metrics {
      background-color: white;
      border-radius: 10px;
      margin-top: 0.75em;
      height: 50vh;
    }
  
    .head {
      font-size: 1.8em;
    }
  
    .row {
      margin-top: 1em;
      margin-left: 0.5em;
    }
  
    .figs {
      font-size: 1.2em;
    }
  
    p {
      color: #40b3ff;
    }
  
    .col {
      margin: 0;
      padding: 0;
    }
  </style>
  