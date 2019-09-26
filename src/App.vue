<template>
  <div id="page">
    <div id="editor" contenteditable="true"></div>

    <div class="label">
      <span>^</span>
      <span>system name</span>
      <span>^</span>
    </div>
<!--     <div class="label">verb</div>
    <div class="label">system response</div> -->
  </div>
</template>

<script>
export default {
  name: 'app',
}
</script>

<style>
body {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  font-size: 3vh;
  color: #2c3e50;
  background-color: #ecefff;
}

#page {
  margin: 15px 27px;
  padding: 10px;
  height: 100vh;
  min-height: 100vh;
  border: 2px solid #d5d5e4;
  border-radius: 5px;
}

#page > #editor {
  min-height: 100%;
}

#page > #editor:focus{
  outline: none;
}

#page > #editor > div {
  margin: 15px 0;
}

.label {
  position: absolute;
}
</style>
