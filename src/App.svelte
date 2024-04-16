<script>
  import data from "./lib/movies";
  import Navbar from "./lib/components/Navbar.svelte";
  import Modal from "./lib/components/Modal.svelte";
  import Movies from "./lib/components/Movies.svelte";
  import Event from "./lib/components/Event.svelte";
  import SearchBar from "./lib/components/SearchBar.svelte";
  import { onDestroy, onMount } from "svelte";

  // 이벤트 텍스트
  const eventText = [
    "영화 정보 업데이트",
    "신규 영화 추가",
    "이벤트 진행중"
  ]

  // data 사본 추가
  let data_temp = [...data]; // 복사본
  let likeCount = 0; // 좋아요 수를 저장할 변수

  const handleLike = (id) => {
    // data[i].likeCount += 1;
    // console.log(likeCount, i);
    // 원본 data에서 id에 해당하는 like를 1 증가
    data.map(movie => {
      if (movie.id === id) {
        movie.likeCount += 1;
      }
    });
    // data_temp = [...data]; // 데이터 복사본으로 초기화
    // data_temp 있는 내용만 필터링해서 복사
    data_temp = data.filter(movie => {
      return data_temp.includes(movie);
      // if(data_temp.includes(movie)) {
      //   return movie;
      // }
    })
  };

  let isModal = false; // 모달창 변수 추가
  let selectedMovie = 0; // 선택한 영화의 인덱스 변수 추가

  const closeModal = () => {
    isModal = false;
  };

  const handleMovieNumber = (i) => {
    selectedMovie = i;
  };

  let alertText = "";
  let isEvent = true; // 이벤트창 표시 여부
  let eventIndex = 0; // 이벤트 텍스트 인덱스
  let intervalEventText; // 이벤트 텍스트 인터벌 변수

  $: {
    // 이벤트 인터벌 제거
    clearInterval(intervalEventText);

    // 일정 시간 경과 후 eventIndex를 1증가
    intervalEventText = setInterval(() => {
      eventIndex += 1;
      if (eventIndex >= eventText.length) {
        eventIndex = 0;
      }
    }, 3000);
  }
 
</script>
 
<Navbar />

<!-- <div class={isEvent ? 'event show' : 'event'}> -->
{#if isEvent}  
  <Event bind:isEvent {eventText} {eventIndex} />
{/if}

<SearchBar {data} bind:data_temp bind:alertText />

<!-- 전체보기 버튼 추가 -->
<div class="container">
  <button on:click={() => {
    data_temp = [...data]; // 데이터 복사본으로 초기화
    alertText = ""; // 검색 결과 초기화
  }}>전체보기</button>
</div>

<Movies {data_temp} bind:isModal {handleMovieNumber} {handleLike} />

{#if isModal}
  <Modal {data} {selectedMovie} {closeModal} />
{/if}

<style>
  .container {
    text-align: center;
  }
</style>