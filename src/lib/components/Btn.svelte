<script>
export let dataList;
/**
 * Fetch from testfile (temp.json)
 */
async function getTemp(){
   const response = await fetch('/src/temp.json') ;
   const tempList = await response.json();

   dataList = formatToChart(tempList);
}

/**
 * reformat json array to fit cerbon chart
 * 
 * @param tempList List to format
 * @returns Formatted array
 */
function formatToChart(tempList){
   return tempList.map(data => {
      return {group: "CPU", date: data.date + " " + data.time, value: parseFloat(data.cpuTemp)};
   });
   
}
</script>
<button on:click={getTemp}>Temperatur</button>