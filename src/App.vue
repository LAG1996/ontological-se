<template>
  <div id="page">
    <div id="editor" v-on:click="onClickShell()">
      <table>
        <tbody>
          <tr v-for="(line, index) in lines">
            <td class="line-number">
              {{index + 1}}
            </td>
            <td>
              <TextEditorLine
                v-bind:lineNo="1"
                v-on:enter="onClickEnter()"
              ></TextEditorLine>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

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
import TextEditorLine from './components/TextEditorLine.vue';
export default {
  name: 'app',
  components: { TextEditorLine },
  data: function() {
    return {
      lines: [''],
    };
  },
  methods: {
    onClickShell: function() {
      return false;
    },
    onClickEnter: function() {
      this.lines.push('');
    },
  },
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
  min-height: 100vh;
  border: 2px solid #d5d5e4;
  border-radius: 5px;
}

#page > #editor {
  min-height: 100%;
}

table {
  width: 100%;
}

table .line-number {
  width: 3em;
  vertical-align: top;
}

.label {
  position: absolute;
}
</style>
