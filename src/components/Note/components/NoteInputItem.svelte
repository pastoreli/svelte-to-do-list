<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  const currentItem = {
    title: null,
    description: null
  };

  const addItem = item => {
    item = { ...item };
    console.log("tetse item: ", item);
    dispatch("addItem", item);
    currentItem.title = null;
    currentItem.description = null;
  };
</script>

<style lang="scss" global>
  @import "../../../assets/sass/main.scss";
  .note-input {
    padding: 20px;
    input {
      width: 100%;
      display: block;
      border: none;
      outline: none;
      padding: 5px 10px;
      background-color: transparent;
      &::placeholder {
        color: $placeholder-color;
      }
    }
    &-title {
      font-size: $h2 !important;
      margin: 0;
    }
    &-description {
      @extend input;
      font-size: $p !important;
      &::placeholder {
      }
    }
  }
</style>

<div class="note-input border-bottom">
  <form on:submit|preventDefault={addItem(currentItem)}>
    <input
      bind:value={currentItem.title}
      placeholder="Titulo"
      type="text"
      class="note-input-title" />
    <textarea
      bind:value={currentItem.description}
      placeholder="Descrição"
      type="text"
      class="note-input-description" />
    <button type="submit">Adicionar</button>
  </form>
</div>
