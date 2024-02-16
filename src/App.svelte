<script>
  import data from './lib/movies';
  import Navbar from './lib/components/Navbar.svelte';
  import Modal from './lib/components/Modal.svelte';
  import Movies from './lib/components/Movies.svelte';
  import Event from './lib/components/Event.svelte';
  import Search from './lib/components/Search.svelte';

  const increment = (i) => {
    data[i].like += 1;
  }

  let isModal = false;  // 모달 여부
  let selectedMovie = 0; // 선택한 영화의 인덱스

  // data 사본을 생성
  let data_temp = JSON.parse(JSON.stringify(data));
</script>

<main>
  <Navbar />
  <Event />
  <Search {data} bind:data_temp />
  <Movies {data_temp} bind:isModal bind:selectedMovie {increment} />
</main>

{#if isModal}
  <!-- <Modal bind:isModal={isModal} data={data} selectedMovie={selectedMovie} /> -->
  <Modal bind:isModal {data} bind:selectedMovie />
{/if}


<style>
  main {
    width: 100vw;
  }
</style>