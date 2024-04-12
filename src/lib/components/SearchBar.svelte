<script>
  let inputText = "";
  let alertText = "";
  export let data = [];
  export let data_temp = [];

  $: if(inputText.length > 16) {
    alertText = "입력한도 초과";
  } else {
    alertText = ""; 
  }

  // 입력한 영화제목이 데이터에 있는지 확인
  const searchMovie = () => {
    data_temp = data.filter(movie => {
      return movie.title.includes(inputText);
    })
  
    // 자료가 없으면 경고메시지 출력
    if(data_temp.length === 0) {
      alertText = "검색 결과가 없습니다";
    } else {
      alertText = '';
    }
  }
 
</script>

<div class="search-box">
  <div class="input-group">
    <input 
      type="search" 
      bind:value={inputText}
      on:keydown={(e) => {
        if(e.key ==="Enter") {
          searchMovie();
        }
      }}
    >
    <button on:click={searchMovie}>검색</button>
  </div>
</div>
<p class="text-center">inputText: {inputText}</p>
{#if alertText}
  <p class="text-center alert-text">{alertText}</p>
{/if}  

<style>
  .text-center {
    text-align: center;
  }

  .alert-text {
    color: red;
  }

  .search-box {
    padding: 0 20px;
    margin: 20px 0;
  }

  .input-group {
    width: 100%;
    border: 1px solid #ccc;
    position: relative;
    padding: 0 20px;
  }

  .search-box input {
    width: 100%;
    border: none;
    outline: none;
    padding: 10px;
  }

  .search-box button {
    position: absolute;
    right: 0;
    top: 0;
    border: none;
    outline: none;
    background: #666;
    color: #fff;
    width: 5em;
    height: 100%;
    margin: 0;
  }
</style>