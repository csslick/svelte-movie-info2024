<script>
  export let data = [];
  export let isModal = false;
  export let selectedMovie = 0;
  export let handleLike;
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
        <p>개봉: {movie.year}</p>
        <p>장르: {movie.category}</p>
        <button
          on:click={() => {
            handleLike(i);
          }}>좋아요 {data[i].likeCount}</button
        >
        <button
          on:click={() => {
            isModal = true;
            selectedMovie = i;
            console.log("Selected movie:", data[i]);
          }}
          class="btn btn-primary">상세보기</button
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
