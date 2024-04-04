<script>
  import data from './lib/movies';
  
  let likeCount = 0; // 좋아요 수를 저장할 변수
  const handleLike = (i) => {
    data[i].likeCount += 1;
    console.log(likeCount, i);
  };

  let isModal = false; // 모달창 변수 추가
  let selectedMovie = 0; // 선택한 영화의 인덱스 변수 추가
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
          on:click={()=> {
            isModal = true;
            selectedMovie = i;
            console.log('Selected movie:', data[i]);
          }}
          class="btn btn-primary"
        >상세보기</button>
      </div>
    </div>
  {/each}
</main>

{#if isModal}
  <div class="modal">
    <div class="inner">
      <h3>{data[selectedMovie].title}</h3>
      <p>{@html data[selectedMovie].story}</p>
      <button 
        on:click={()=>isModal=false}
        class="btn-close"
      >닫기</button>
    </div>
  </div>
{/if}

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

  .modal {
    background: rgba(0, 0, 0, 0.7);
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal .inner {
    background: #fff;
    width: 80%;
    padding: 20px;
    border-radius: 10px;
  }
</style>
