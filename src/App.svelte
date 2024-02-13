<script>
  const data = [
    {
      title: "노량",
      year: 2023,
      category: "액션, 드라마",
      like: 0,
      imgUrl: '/images/노량.jpg',
    },
    {
      title: "아쿠아맨과 로스트 킹덤",
      year: 2023,
      category: "액션, 판타지, 어드벤처",
      like: 0,
      imgUrl: '/images/아쿠아맨.jpg',
    },
    {
      title: "3일의 휴가",
      year: 2023,
      category: '판타지, 드라마',
      like: 0,
      imgUrl: '/images/3일의휴가.jpg',
    },
  ];

  const increment = (i) => {
    data[i].like += 1;
  }

  let isModal = false;
</script>

<main>
  <h1>영화정보</h1>
  <!-- 반복문으로 데이터를 출력 -->
  {#each data as movie, i}
    <div class="item">
      <figure>
        <img src={movie.imgUrl} alt={movie.title}>
      </figure>
      <div class="info">
        <h3 class="bg-yellow">{i}: {movie.title}</h3>
        <p>개봉: {movie.year}</p>
        <p>장르: {movie.category}</p>
        <button on:click={() => increment(i)} class="btn">좋아요 {movie.like}</button>
        <button on:click={()=> isModal=true} class="btn btn-primary">상세보기</button>
      </div>
    </div>
  {/each}
</main>

{#if isModal }
<div class="modal">
  <div class="inner">
    <h3>Detail</h3>
    <p>영화 상세정보</p>
    <button on:click={()=>{isModal=false}} class="btn">닫기</button> 
  </div>
</div>
{/if}

<style>
  .btn {
    background-color: #000;
    color: #fff;
    padding: 10px 20px;
    border: none;
    margin-bottom: 10px;
  }

  .btn-primary {
    background-color: transparent;
    border: 1px solid #000;
    color: #000;
  }

  .item {
    text-align: left;
    margin-bottom: 40px;
    display: flex;
    gap: 20px;
    padding: 20px;
  }

  .item figure {
    margin: 0;
    width: 50%;
  }
  .item .info {
    width: 50%;
  }

  .item img {
    width: 100%;
  }

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
