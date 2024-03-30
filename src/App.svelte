<script>
  import logo1 from './assets/svelte.svg';
  let logo2 = '/vite.svg';
  let title = "영화제목 1";
  let year = 2024;
  let category = "액션";
  let textRed = "color: red;"

  const data = [
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
</script>

<main>
  <h1>영화정보</h1>
  <img src={logo1} alt="">
  <img src={logo2} alt="">
  <div>
    <h3 class="bg-yellow" style={textRed}>{data[0].title}</h3>
    <p>개봉: {data[0].year}</p>
    <p>장르: {data[0].category}</p>
    <p>{"hello".toUpperCase()}</p>
  </div>
  <div>
    <h3 class="bg-yellow" style={textRed}>{data[1].title}</h3>
    <p>개봉: {data[1].year}</p>
    <p>장르: {data[1].category}</p>
  </div>
</main>

<style>
  .bg-yellow {
    background: gold;
    padding: 10px;
  }
</style>
