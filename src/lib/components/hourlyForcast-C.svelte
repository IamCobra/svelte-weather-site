<script>
  import HourlyForecast from "./hourlyForecast-D.svelte";
  import { hourlyWeatherData } from "../data/stores/WeatherDataStores.js";

  $: hourlyData = $hourlyWeatherData;
</script>

<div class="flex">
  {#if hourlyData != null}
    {#if hourlyData.length === 0}
      <p>Loading...</p>
    {/if}
    {#each hourlyData as hour}
      <HourlyForecast
        time={hour.time}
        icon={hour.weathercode}
        temp={hour.temp}
      />
    {/each}
  {/if}
</div>

<style>
  .flex {
    overflow-y: hidden;
    display: flex;
    flex-wrap: nowrap;
    width: 100%;
    height: 140px;
    overflow-x: auto;
    gap: 5px;
    padding-bottom: 1rem;
  }
</style>
