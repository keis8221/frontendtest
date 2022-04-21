<script lang="ts" type="module">
  import Counter from './component/Counter.svelte'; 

  interface Counter{
    deleted: boolean; //カウンターが削除カウンターが削除されているかを判断する変数
    title: string; // カウンターのタイトル
    count: number; // カウンターのカウント数
  }

  /** 生成したカウンター配列 */
  let counterArray: Counter[] = [{deleted: false, title: 'new', count: 0}];
  
  /** カウンターの配列　*/
  $: validCounterArray = counterArray.filter((element) => {return !(element.deleted)});

  /** カウンターの合計値 */
  $: sum = validCounterArray.reduce((sum, element) => sum + element.count, 0);

  /** カウンターの名前を格納したString配列 */
  $: titleList = validCounterArray.reduce(
    (string, element) => [...string, element.title],
    []
  );
  /** カウンターを増やす関数 */
  function addCounter(): void {
    counterArray = [
      ...counterArray,
      {
        deleted: false,
        title: "new",
        count: 0
      }
    ];
  }
</script>

<style>
h1 {
  font-weight: inherit;
  font-size: 4rem;
} 

.addcounter_btn {
  background-color: #68d391;
  border: none;
  color: #fff;
  max-width: 24rem;
}

.counter-box{
  max-width: 24rem;
  box-sizing: border-box;
  background-color: #f7fafc;
  margin-bottom: 2rem;
}

input, button {
  font-family: inherit;
  font-size: 100%;
  line-height: inherit;

}

input {
  border: none;
  width: 8rem;
  color: #718096;
  box-sizing: border-box;
  height: 22px;
  margin-right: 2.5rem;
  margin-left: 10px;
}

span {
  font-size: 1.2rem;
}
</style>

<div class="text-center mt-2">
  <h1>Multiple Counter</h1>

  {#each counterArray as {deleted, title, count}}
    {#if !deleted}
      <div class="counter-box rounded mx-auto shadow-lg mb-2">
        <input class="" bind:value={title}>
        {#key count}
            <span class="mx-auto absolute font-weight-bold">{count}</span>
        {/key}
        <Counter bind:deleted bind:count />
      </div>
    {/if}
  {/each}
  
  <div class="addcounter_btn m-auto text-white rounded text-center cursor-pointer" on:click={addCounter}>
    new counter
  </div>
  
  <div class="">
      title list: {titleList} <br/>
      {#key sum}
          sum of count: <span>{sum}</span>
      {/key}
  </div>
</div>



