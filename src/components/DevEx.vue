<template>
  <DxDiagram
    id="diagram"
    ref="diagram"
     @selection-changed="showEmployeeInfo"
  >

    <DxCustomShape
      :category="'hardware'"
      :type="'phone'"
      :title="'Phone'"
      :background-image-url="'https://i.ibb.co/5c2K5mD/Amazon-EC2-DB-on-Instance-dark-bg.png'"
      :background-image-left="0.15"
      :background-image-top="0"
      :background-image-width="0.7"
      :background-image-height="0.7"
      :default-width="0.75"
      :default-height="0.75"
      :default-text="'Phone'"
      :allow-edit-text="true"
      :text-left="0"
      :text-top="0.7"
      :text-width="1"
      :text-height="0.3"
    >
    </DxCustomShape>
   
    <DxToolbox :visible="true">
      <DxGroup
        :category="'hardware'"
        :title="'Hardware'"
      />
    </DxToolbox>
  </DxDiagram>
</template>
<script>
import {
  DxDiagram, DxGroup, DxToolbox, DxCustomShape,
} from 'devextreme-vue/diagram';
import 'whatwg-fetch';

export default {
  components: {
    DxDiagram, DxGroup, DxToolbox, DxCustomShape,
  },
  data() {
      return {
          wifiNodes: [
              {x: '0.5',
              y: '0.5'}
          ]
      }
  },
  mounted() {
    const diagram = this.$refs.diagram.instance;
    console.log("🚀 ~ file: DevEx.vue ~ line 55 ~ mounted ~ this.$refs.diagram.instance", this.$refs.diagram)
    fetch('https://js.devexpress.com/Demos/WidgetsGallery/JSDemos/data/diagram-hardware.json')
      .then((response) => response.json())
      .then((json) => {
        diagram.import(JSON.stringify(json));
      })
      .catch(() => {
        throw new Error('Data Loading Error');
      });
  },
  methods:{
    showEmployeeInfo() {
      console.log('ss');
    }
  }
};
</script>
<style scoped>
    #diagram {
      height: 900px;
    }
</style>
