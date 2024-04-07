<script>
  import data from './lib/movies';
  import Navbar from './lib/components/Navbar.svelte';
  import Modal from './lib/components/Modal.svelte';
  import Movies from './lib/components/Movies.svelte';
  
  let likeCount = 0; // 좋아요 수를 저장할 변수
  const handleLike = (i) => {
    data[i].likeCount += 1;
    console.log(likeCount, i);
  };

  let isModal = false; // 모달창 변수 추가
  let selectedMovie = 0; // 선택한 영화의 인덱스 변수 추가

  const closeModal = () => {
    isModal = false;
  }
</script>

<Navbar />
<Movies {data} bind:isModal {selectedMovie} {handleLike} />

{#if isModal}
  <Modal {data} {selectedMovie} {closeModal}/>
{/if}

<style>
</style>
