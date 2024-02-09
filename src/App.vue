<template>
  <ejs-diagram id="diagram" :width="width" :height="height" :nodes="nodes" :getNodeDefaults="getNodeDefaults"
    :connectors="connectors"></ejs-diagram>
</template>
<script>
import { DiagramComponent } from '@syncfusion/ej2-vue-diagrams';

let nodes = [
  {
    id: "node1",
    //height: 60,
    //width: 170,
    //offsetX: 600,
    offsetY: 50,
    shape: { type: "Flow", shape: "Terminator" },
    annotations: [{ content: "Start" }]
  },
  {
    id: "node2",
    offsetY: 140,
    shape: { type: "Flow", shape: "Process" },
    annotations: [{ content: "create variable i = 0" }]
  },
  {
    id: "node3",
    offsetY: 230,
    shape: { type: "Flow", shape: "Decision" },
    annotations: [{ content: "is i < 10?" }]
  },
  {
    id: "node4",
    offsetY: 340,
    shape: { type: "Flow", shape: "PreDefinedProcess" },
    annotations: [
      {
        content: 'print "Syncfusion!!"'
      }
    ]
  },
  {
    id: "node5",
    offsetY: 430,
    shape: { type: "Flow", shape: "Process" },
    annotations: [
      {
        content: "i = i + 1"
      }
    ]
  },
  {
    id: "node6",
    offsetY: 520,
    shape: { type: "Flow", shape: "Terminator" },
    annotations: [{ content: "End" }]
  }
];

let connectors = [
  {
    id: "connector1",
    sourceID: "node1",
    targetID: "node2"
  },
  {
    id: "connector2",
    sourceID: "node2",
    targetID: "node3"
  },
  {
    id: "connector3",
    sourceID: "node3",
    targetID: "node4",
    annotations: [{ content: "Yes", style: { fill: "white"}}]
  },
  {
    id: "connector4",
    sourceID: "node4",
    targetID: "node5"
  },
  {
    id: "connector5",
    sourceID: "node3",
    targetID: "node6",
    type: "Orthogonal",
    segments:[
      { length: 30, direction: "Right"},
      { length: 300, direction: "Bottom"}
    ],
    annotations: [{ content: "No", style: { fill: "white" } }]
  },
  {
    id: "connector6",
    sourceID: "node5",
    targetID: "node3",
    type: "Orthogonal",
        segments: [
            { length: 30, direction: "Left" },
            { length: 200, direction: "Top" }
        ]
  }
];

export default {
  components: {
    "ejs-diagram": DiagramComponent
  },

  data: function () {
    return {
      width: "1250px",
      height: "560px",
      nodes: nodes,
      connectors: connectors,
      getNodeDefaults: (node) => {
        node.height = 60;
        node.width = 170;
        node.offsetX = 600;
        return node;
      }
    }
  }
}
</script>
<style>
@import "../node_modules/@syncfusion/ej2-vue-diagrams/styles/material.css";
</style>
