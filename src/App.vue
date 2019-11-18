<template>
  <div id="app">
    <!-- Uncomment this code to render button on the page -->
    <!-- <ejs-button v-on:click="buttonClick">Load Data</ejs-button> -->
    
    <!-- Remove dataSource property and add ref="datagrid" in the below grid code while working with Ajax -->
    <ejs-grid :dataSource="data">
      <e-columns>
        <e-column field="OrderID" headerText="Order ID" textAlign="Right" width="90"></e-column>
        <e-column field="CustomerID" headerText="Customer ID" width="120"></e-column>
        <e-column field="OrderDate" headerText="Order Date" textAlign="Right" format="yMd" type="date" width="120"></e-column>
        <e-column field="ShipCountry" headerText="Ship Country" width="120"></e-column>
      </e-columns>
    </ejs-grid>
  </div>
</template>

<script>
import Vue from 'vue';
import { GridPlugin } from '@syncfusion/ej2-vue-grids';
import { DataManager, WebApiAdaptor } from '@syncfusion/ej2-data';

// Uncomment this code to bind data in Vue Grid through AJAX post
// import { Ajax } from '@syncfusion/ej2-base';

Vue.use(GridPlugin);

export default {
  data () {
    return {
       data: new DataManager({
         url: "https://ej2services.syncfusion.com/production/web-services/api/Orders?$top=7",
         adaptor: new WebApiAdaptor()
       })
    }
  },
  // Uncomment this code to bind data in Vue Grid through AJAX post
  // methods: {
  //   buttonClick: function() {
  //     var grid = this.$refs.datagrid // Grid instance
  //     var ajax = new Ajax(
  //       "https://ej2services.syncfusion.com/production/web-services/api/Orders",
  //       "GET"
  //     );
  //     ajax.send();
  //     ajax.onSuccess = function(result) {
  //     grid.ej2Instances.setProperties({dataSource : JSON.parse(result)})
  //     };
  //   }
  // }
}
</script>

<style>
  @import url("https://cdn.syncfusion.com/ej2/material.css");
</style>