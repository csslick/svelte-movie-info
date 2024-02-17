<script>
  export 
    let 
      data_temp = [],
      isModal = false,
      selectedMovie = 0,
      increment;
</script>

<main>
  <h1>영화정보</h1>
  {#each data_temp as movie, i}
    <div class="item">
      <figure>
        <img src={movie.imgUrl} alt={movie.title}>
      </figure>
      <div class="info">
        <h3>{movie.id}: {movie.title}</h3>
        <p>개봉: {movie.year}</p>
        <p>장르: {movie.category}</p>
        <button on:click={() => increment(movie.id)} class="btn">좋아요 {movie.like}</button>
        <button 
          on:click={()=> {isModal=true; selectedMovie=movie.id}} 
          class="btn btn-primary"
        >상세보기</button>
      </div>
    </div>
  {/each}
</main>


<style>
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