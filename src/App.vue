<template>
  <div id="app">
    <div class="container">
      <main class="flexbox">

        <board id="board-1">
          <card id="card-1" draggable>
            <text-edit/>
          </card>
        </board>
        <board id="board-2">
          <card id="card-2" draggable>
            <image-edit/>
          </card>
          <card id="card-3" draggable>
            <text-edit/>
          </card>
        </board>
      </main>
    </div>
  </div>
</template>

<script>
import ImageEdit from "@/components/wysiwyg/ImageEdit";
import TextEdit from "@/components/wysiwyg/TextEdit";
import Board from "@/components/DnD/Board";
import Card from "@/components/DnD/Card";

export default {
  name: 'App',
  components: {
    TextEdit,
    ImageEdit,
    Board,
    Card,
  }
}
</script>

<style lang="less">
body {
  margin: 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 15px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.flexbox {
  display: flex;
  justify-content: space-between;

  overflow: hidden;

  margin: 0 auto;
  padding: 15px;
}

.board {
  display: flex;
  flex-direction: column;

  width: 100%;
  max-width: 300px;

  background-color: #313131;

  padding: 15px;
}

.card {
  padding: 15px 25px;
  background-color: #F3F3F3;

  cursor: pointer;
  margin-bottom: 15px;
}
</style>
