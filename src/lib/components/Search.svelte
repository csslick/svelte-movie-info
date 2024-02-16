<script>
  export let data = [];
  export let data_temp = [];
  let inputText = "";
  let alertText = "";
  $: if(inputText.length > 16) {
    console.log('입력한도 초과');
    alertText = '입력한도 초과';
  } 

  const searchMovie = () => {
    // data에서 inputText를 포함하는 영화를 찾아서 반환
    data_temp = data.filter(movie => movie.title.includes(inputText));
    if(data_temp.length === 0) {
      alertText = '검색 결과가 없습니다.';
    } else {
      alertText = '';
    }
    console.log(data_temp);
    // 입력값 삭제
    // inputText = '';
  }
</script>

<div class="search-box">
  <div class="input-group">
    <input 
      type="search" 
      bind:value={inputText} 
      on:keydown={e => e.key === 'Enter' && searchMovie()}
    />
    <button on:click={ searchMovie }>검색</button>
  </div>
</div>
<button 
  on:click={() => {
    data_temp = JSON.parse(JSON.stringify(data));
    alertText = '';
  }} 
  class='btn' 
  style='margin-top: 1em;'
>전체보기</button>

<p style="text-align:center">{inputText}</p>
{#if alertText} 
  <p style="color:red">{alertText}</p>
{/if}  

<style>
  .search-box {
    padding: 0 20px;
    margin-top: 20px;
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
    width: 4em;
    height: 100%;
  }
</style>
