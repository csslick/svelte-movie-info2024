<script>
  const data = [
    {
      title: "파묘",
      year: 2024,
      category: "미스터리, 공포",
      likeCount: 0,
      imgUrl: "/images/파묘.jpg",
      story:
        "미국 LA, 거액의 의뢰를 받은<br>무당 ‘화림’(김고은)과 ‘봉길’(이도현)은<br>기이한 병이 대물림되는 집안의 장손을 만난다.<br>조상의 묫자리가 화근임을 알아챈 ‘화림’은 이장을 권하고,<br>돈 냄새를 맡은 최고의 풍수사 ‘상덕’(최민식)과 장의사 ‘영근’(유해진)이 합류한다.",
    },
    {
      title: "고질라 X 콩: 뉴 엠파이어",
      year: 2024,
      category: "어드벤처, 액션, SF",
      likeCount: 0,
      imgUrl: "/images/고질라X콩.jpg",
      story:
        "‘고질라’ VS ‘콩’, 두 타이탄의 전설적인 대결 이후<br>할로우 어스에 남은 ‘콩’은 드디어<br>애타게 찾던 동족을 발견하지만<br>그 뒤에 도사리고 있는 예상치 못한 위협에 맞닥뜨린다.",
    },
    {
      title: "듄: 파트2",
      year: 2024,
      category: "액션",
      likeCount: 0,
      imgUrl: "/images/듄-파트2.jpg",
      story:
        "황제의 모략으로 멸문한 가문의 유일한 후계자 폴.(티모시 샬라메)<br>어니 레이디 제시카(레베카 퍼거슨)와<br>간신히 목숨만 부지한 채 사막으로 도망친다.<br>그곳에서 만난 반란군들과 숨어 지내다<br>그들과 함께 황제의 모든 것을 파괴할 전투를 준비한다.",
    },
  ];

  let likeCount = 0; // 좋아요 수를 저장할 변수

  const handleLike = (i) => {
    data[i].likeCount += 1;
    console.log(likeCount, i);
  };

  let isModal = false; // 모달창 변수 추가
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
      <h3>영화 상세정보</h3>
      <button class="btn-close">닫기</button>
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
