<script lang="ts" type="module">
  export let deleted: boolean;
  export let count: number;


  //１を足す
  function increment(): void{
	  count += 1;
  }

  //1以上の数字であれば1を引く
  function decrement(): void{
    //引かれる値が０より大きいか確認
    if(count > 0){
      count -= 1;
    }
  }

  //カウントのリセット
  function reset(): void{
	  count = 0;
  }

  //カウンターの削除
  function deletecounter(): void{
	  deleted = true;
  }
</script>

<style>
a {
  margin: 0px;
  font-family: inherit;
  border: none;
}

.increment_btn {
  background-color: #f56565; 
}

.decrement_btn {
  background-color: #4299e1; 
}

.reset_btn {
  background-color: #ecc94b; 
}

.deletecounter {
  color: #a0aec0;
}

.counter-btn {
  margin-left: 45px; 
}
</style>

<div class="counter-btn btn-group text-white relative pt-1 pb-1">
  <a class="btn increment_btn rounded-left" on:click={increment}>+</a>
  <a class="btn decrement_btn" on:click={decrement}>-</a>
  <a class="btn reset_btn rounded-right" on:click={reset}>0</a>
  <span class="pt-1 pl-3 pr-3 deletecounter cursor-pointer " on:click={deletecounter}>×</span>
</div>





