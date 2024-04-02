<script>
  import logo1 from './assets/svelte.svg';
  let logo2 = '/vite.svg';
  let textRed = "color: red;"

  const data = [
    {
      title: "파묘",
      year: 2024,
      category: "미스터리, 공포",
    },
    {
      title: "고질라 X 콩: 뉴 엠파이어",
      year: 2024,
      category: "어드벤처, 액션, SF",
    },
    {
      title: "듄: 파트2",
      year: 2024,
      category: "액션",
    },
  ];

  const foods = ['pizza', 'burger', 'sushi', 'pasta'];
</script>

<main>
  {#each foods as food, i}
    <p>{i}: {food}</p>
  {/each}
  <h1>영화정보</h1>
  <img src={logo1} alt="">
  <img src={logo2} alt="">
  {#each data as movie, i}
    <div>
      <h3 class="bg-yellow" style={textRed}>{movie.title}</h3>
      <h3>{movie.title}</h3>
      <p>개봉: {movie.year}</p>
      <p>장르: {movie.category}</p>
    </div>
  {/each}
</main>

<style>
  .bg-yellow {
    background: gold;
    padding: 10px;
  }
</style>
