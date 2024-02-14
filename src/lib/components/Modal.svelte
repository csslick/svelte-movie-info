<script>
   // props 받기: 모달 여부, 선택한 영화의 인덱스, 데이터
  export let 
    isModal = false, 
    selectedMovie = 0, 
    data = [];
  console.log(isModal, selectedMovie, data);
</script>

<div class="modal">
  <div class="inner">
    <h3>{data[selectedMovie].title}</h3>
    <p>영화 상세정보</p>
    <button on:click={() => isModal=false} class="btn">닫기</button>
  </div>
</div>


<style>
    .modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background-color: rgba(0,0,0,0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 100;
  }

  .modal .inner {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    position: relative;
    width: 80%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    z-index: 100;
    box-shadow: 0 0 10px rgba(0,0,0,0.5);
  }
</style>