<template>
    <div id="app">
        <button type="button" @click="$refs.chart.add({id: +new Date(), x: 10, y: 10, name: '', type: 'terminal', approvers:[{name: 'admin'}]})">
            Add Element
        </button>
        <button type="button" @click="$refs.chart.remove()">
            Delete element
        </button>
        <flowchart
           @dblclick="handleDblClick"
           ref="chart">
        </flowchart>
    </div>
</template>
<script>
  import Vue from 'vue';
  import FlowChart from 'flowchart-vue';

  Vue.use(FlowChart);

  export default {
    name: 'App',

    methods: {
      handleDblClick(position) {
        this.$refs.chart.add({
          id: new Date(),
          x: position.x,
          y: position.y,
          name: 'New',
          type: 'start',
          approvers: [],
        });
      },
    }
  };
</script>