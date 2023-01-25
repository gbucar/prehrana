<script>
  import restaurants from "./restaurants.json";
  import Restaurant from "./Restaurant.svelte";
  let res = restaurants;

  let cheapFirst = true;
  let city = "LJUBLJANA";
  let justOpen = true;

  $: res = res.sort((a,b)=> cheapFirst ? a.cena-b.cena : b.cena - a.cena);
  $: res = res.filter(a => a.city === city)
  $: res = res.filter(a => {
    const now = new Date()
    const day = now.getDay()
    const now_minutes = now.getHours() * 60 + now.getMinutes();
    const [from, to] = day < 5 ? a.delovniCasTeden : day == 5 ? a.delovniCasSobota : a.delovniCasNedelja;
    return !justOpen ? true : from < now_minutes && now_minutes < to;
  })
  
</script>

<div>
  <h1>Boni</h1>
  <div class="boni">
    {#each res as restaurant}
      <Restaurant data={restaurant} />
    {/each}
  </div>
    
</div>

<style>
  h1 {
    text-align: center;
  }
  .boni {
    display: flex;
    flex-direction:column;
    justify-items:center;
    align-items: center;
  }
</style>
