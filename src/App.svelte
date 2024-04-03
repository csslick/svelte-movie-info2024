<script>
  const data = [
    {
      title: "파묘",
      year: 2024,
      category: "미스터리, 공포",
      likeCount: 0,
      imgUrl: "/images/파묘.jpg",
    },
    {
      title: "고질라 X 콩: 뉴 엠파이어",
      year: 2024,
      category: "어드벤처, 액션, SF",
      likeCount: 0,
      imgUrl: "/images/고질라X콩.jpg",
    },
    {
      title: "듄: 파트2",
      year: 2024,
      category: "액션",
      likeCount: 0,
      imgUrl: "/images/듄-파트2.jpg",
    },
  ];

  let likeCount = 0; // 좋아요 수를 저장할 변수

  const handleLike = (i) => {
    data[i].likeCount += 1;
    console.log(likeCount, i);
  };
</script>

<main class="container">
  <h1>영화정보</h1>
  {#each data as movie, i}
    <div class="item">
      <figure>
        <img src={movie.imgUrl} alt={movie.title} />
      </figure>
      <div class="info">
        <h3 class="bg-yellow">{movie.title}</h3>
        <h3>{movie.title}</h3>
        <p>개봉: {movie.year}</p>
        <p>장르: {movie.category}</p>
        <button
          on:click={() => {
            handleLike(i);
          }}>좋아요 {data[i].likeCount}</button
        >
      </div>
    </div>
  {/each}
</main>

<style>
  .bg-yellow {
    background: gold;
    padding: 10px;
    color: #333;
  }

  .item {
    width: 100%;
    border: 1px solid #ccc;
    display: flex;
    margin-bottom: 20px;
    padding: 1rem;
  }

  .item figure {
    width: 30%;
    margin-right: 1rem;
  }

  .item img {
    width: 100%;
  }

  .item .info {
    width: 100%;
  }
</style>
