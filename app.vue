<template>
  <div id="app">
    <v-grid
      theme="compact"
      :autoSizeColumn="{
        mode: 'autoSizeOnTextOverlap',
      }"
      :source="rows"
      :columns="columns"
      @beforeCellFocus="beforeFocus"
    ></v-grid>
    <button id="columns-add" v-on:click="colClicked"></button>
    <button id="rows-add" v-on:click="rowClicked"></button>
  </div>
</template>

<script>
import VGrid, { VGridVueTemplate } from "@revolist/vue-datagrid";
import Vue from "vue";
// your vue component
const myVue = Vue.component("my-component", {
  props: ["rowIndex", "name"],
  data: function () {
    return {
      count: 0,
    };
  },
  methods: {
    iAmClicked(e) {
      this.count++;
    },
    updateContent() {
      // 通过点击按钮改变 P 标签的内容
      this.$emit("update-content");
    },
  },
  template:
    '<button v-on:click="iAmClicked">You {{name}} me {{ count }} times.</button>',
});

export default {
  name: "App",
  data() {
    return {
      name: 123,
      columns: [
        {
          name: "Vue",
          size: 200,
          cellTemplate: VGridVueTemplate(myVue),
        },
        {
          name: "Vue",
          prop: "details",
          autoSize: true,
        },
      ],
      rows: [
        {
          details: "My neighbour is Vue component",
        },
      ],
    };
  },
  methods: {
    beforeFocus(e) {
      e.preventDefault();
    },
    colClicked() {
      let col = this.columns.map((x) => x);
      col.push({ name: "Vue", size: 200 });
      this.columns = col;
    },
    rowClicked() {
      let row = this.rows.map((x) => x);
      row.push({
        details: "My neighbour is Vue component",
      });
      this.rows = row;
    },
  },
  components: {
    VGrid,
    myVue,
  },
};
</script>

<style>
#app {
  height: 400px;
  width: 500px;
  display: flex;
  flex-wrap: wrap;
}
revo-grid {
  height: auto;
  width: 80%;
}
#columns-add {
  font-size: 24px;
  width: 20%;
  height: 10px;
  background: none;
  border: none;
  outline: none;
  cursor: pointer;
}
#columns-add:before {
  content: "+";
}
#rows-add {
  font-size: 24px;
  width: 10px;
  height: 10px;
  background: none;
  border: none;
  outline: none;
  cursor: pointer;
}
#rows-add:before {
  content: "+";
}
</style>
