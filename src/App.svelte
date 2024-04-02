<script>
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

  let likeCount = 0; // 좋아요 수를 저장할 변수

  const handleLike = () => {
    likeCount += 1;
    console.log(likeCount)
  }
</script>

<main>
  <h1>영화정보</h1>
  {#each data as movie, i}
    <div>
      <h3 class="bg-yellow">{movie.title}</h3>
      <h3>{movie.title}</h3>
      <p>개봉: {movie.year}</p>
      <p>장르: {movie.category}</p>
      <button on:click={handleLike}>좋아요 {likeCount}</button>
    </div>
  {/each}
</main>

<style>
  .bg-yellow {
    background: gold;
    padding: 10px;
    color: #333;
  }
</style>
