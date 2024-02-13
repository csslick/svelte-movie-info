<script>
  import img from "./assets/svelte.svg";
  let logo = "/vite.svg";

  const data = [
    {
      title: "노량",
      year: 2023,
      category: "액션, 드라마",
    },
    {
      title: "아쿠아맨과 로스트 킹덤",
      year: 2023,
      category: "액션, 판타지, 어드벤처",
    },
  ];
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
    </div>
  {/each}
</main>

<style>
  .bg-yellow {
    background: gold;
    padding: 10px;
  }
</style>
