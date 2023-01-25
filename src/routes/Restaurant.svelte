<script lang="ts">
  export let data;
  let directionsUrl = `https://www.google.com/maps/dir/?api=1&destination=${data.lat},${data.lon}`;
</script>


<div class="restaurant" href={data.detailslink}>
  <a href={data.detailslink}><h2>{data.lokal}</h2></a>
  <div class="doplacilo">
    <a href={directionsUrl} target="_blank" rel="noreferrer">↱</a>
    <div>{data.doplacilo} €</div>
  </div>
</div>

<style>
  a {
    color: black;
    text-decoration: none;
  }

  .doplacilo {
    text-align: center;
    margin-top: auto;
    margin-bottom: auto;
  }

  .restaurant {
    width: 90vw;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    background-color: #eeeeee;
    border-radius: 10px;
    padding-left: 10px;
    padding-right: 20px;
    margin-bottom: 10px;
  }
</style>
