<script>
  import img from "./assets/svelte.svg";
  let logo = "/vite.svg";

  const data = [
    {
      title: "노량",
      year: 2023,
      category: "액션, 드라마",
      like: 0,
    },
    {
      title: "아쿠아맨과 로스트 킹덤",
      year: 2023,
      category: "액션, 판타지, 어드벤처",
      like: 0,
    },
  ];

  const increment = (i) => {
    data[i].like += 1;
  }
</script>

<main>
  <h1>영화정보</h1>
  <img src={logo} alt="logo" />
  <img src={img} alt="" />
  <!-- 반복문으로 데이터를 출력 -->
  {#each data as movie, i}
    <div class="item">
      <h3 class="bg-yellow">{i}: {movie.title}</h3>
      <p>개봉: {movie.year}</p>
      <p>장르: {movie.category}</p>
      <button on:click={() => increment(i)} class="btn">좋아요 {movie.like}</button>
    </div>
  {/each}
</main>

<style>
  .btn {
    background-color: #000;
    color: #fff;
    padding: 10px 20px;
    border: none;
  }
  .bg-yellow {
    background: gold;
    padding: 10px;
  }
</style>
