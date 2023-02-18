<script>
export let dataList;

async function getTemp(){
   const response = await fetch('/src/temp.json') ;
   const tempList = await response.json();

   dataList = formatToChart(tempList);
}

function formatToChart(tempList){
   return tempList.map(data => {
      return {group: "CPU", date: data.date + " " + data.time, value: parseFloat(data.cpuTemp)};
   });
   
}
</script>
<button on:click={getTemp}>Temperatur</button>