<script>
  let code_block;
  let key_to_insert = "";
  let value_to_insert = "";
  let capacity = 10;

  let arr = Array(capacity).fill(0);
  let key = "";

  $: arr = Array(capacity).fill(0);
  $: key = key_to_insert;
  $: value = value_to_insert;
  console.log();
  const run = () => {
    let ran_code_block = `let key = "${key_to_insert}"\n` + code_block;
    let index = 0;
    eval(ran_code_block);
    index = index % capacity;
    arr[index] = value;
    key_to_insert = "";
    value_to_insert = "";
  };

  let example_01 =
    "let total = 0;\n\
for(let i = 0; i < key.length; ++i) {\n\
    total += key.charCodeAt(i);\n}\n\
	index = total;";
</script>

<!-- begin HTML -->
<main>
  <div>function hash(key) {"{"}</div>
  <div>let index = 0;</div>
  <textarea spellcheck="false" rows="6" cols="42" bind:value={code_block} />
  <div>return index % capacity</div>
  <div style="margin-bottom: 30px;">{"}"}</div>
  <div>
    <input bind:value={key_to_insert} type="text" placeholder="key..." />
    <input bind:value={value_to_insert} type="number" placeholder="value..." />

    <button on:click={run}>Run</button>
  </div>
  <div class="array">
    {#each arr as elem}
      <ae>{elem}</ae>
    {/each}
  </div>
  <div>
    Capacity: {capacity}
  </div>
  <input bind:value={capacity} type="range" min="1" max="25" />

  <div class="examples">
    <div>Example 01</div>
    <textarea
      style="border: 2px dashed gray"
      readonly
      spellcheck="false"
      rows="7"
      cols="42"
    >
      {example_01}
    </textarea>
  </div>
</main>

<!-- end HTML -->
<style>
  main {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -60%);
  }

  .array {
    display: flex;
  }

  ae {
    display: grid;
    justify-items: center;
    align-items: center;
    min-width: 40px;
    min-height: 40px;
    border: 1px solid green;
    font-weight: 800;
    font-size: 30px;
    padding-left: 5px;
    padding-right: 5px;
  }
</style>
