<script>
   import Btn from "../lib/components/Btn.svelte";
   import Chart from "../lib/components/Chart.svelte";

   let dataList = [];
</script>

<h1>Welcome to Carbon Chart</h1>

<Chart data={dataList}/>
<Btn bind:dataList />
