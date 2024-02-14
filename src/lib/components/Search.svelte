<script>
  let inputText = "";
</script>

<div class="search-box">
  <div class="input-group">
    <input type="search" bind:value={inputText} />
    <button>검색</button>
  </div>
</div>
<p style="text-align:center">{inputText}</p>

<style>
  .search-box {
    padding: 0 20px;
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
