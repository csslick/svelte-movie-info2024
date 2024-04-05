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