<script>
   import "@carbon/styles/css/styles.css";
   import "@carbon/charts/styles.css";
   import { LineChart } from "@carbon/charts-svelte";

   export let data = [];

   let options = {
      title: "Temperatur",
      axes: {
         left: {},
         bottom: {
            scaleType: "time",
         },
      },
      timeScale: {
         timeIntervalFormats: {
            hourly: {
               primary: "MMM d, HH:mm",
               secondary: "HH:mm",
            },
         },
      },
      legend: {
         clickable: false,
      },
      height: "500px",
   };
</script>

<LineChart {data} {options} />
