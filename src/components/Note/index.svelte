<script>
  import { noteItems } from "@/store";

  import { NoteInputItem, NoteItem } from "./components";

  export let noteIndex;

  const addItem = item => {
    console.log("tetse item: ", item);
    noteItems.update(value => [...value, item]);
  };
</script>

<div class="content neomorphism border-radios">
  <h1>Todo do list</h1>

  <NoteInputItem on:addItem={event => addItem(event.detail)} />

  <h2>Itens</h2>
  <div>
    {#each $noteItems as item}
      <NoteItem {item} />
    {/each}
  </div>

</div>
