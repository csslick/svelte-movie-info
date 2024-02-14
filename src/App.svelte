<script>
  import data from './lib/movies';
  import Navbar from './lib/components/Navbar.svelte';
  import Modal from './lib/components/Modal.svelte';

  const increment = (i) => {
    data[i].like += 1;
  }

  let isModal = false;  // 모달 여부
  let selectedMovie = 0; // 선택한 영화의 인덱스
</script>

<Navbar />
<main>
  <h1>영화정보</h1>
  <!-- 반복문으로 데이터를 출력 -->
  {#each data as movie, i}
    <div class="item">
      <figure>
        <img src={movie.imgUrl} alt={movie.title}>
      </figure>
      <div class="info">
        <h3>{i}: {movie.title}</h3>
        <p>개봉: {movie.year}</p>
        <p>장르: {movie.category}</p>
        <button on:click={() => increment(i)} class="btn">좋아요 {movie.like}</button>
        <button 
          on:click={()=> {isModal=true; selectedMovie=i}} 
          class="btn btn-primary"
        >상세보기</button>
      </div>
    </div>
  {/each}
</main>
<Modal/>



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

</style>
