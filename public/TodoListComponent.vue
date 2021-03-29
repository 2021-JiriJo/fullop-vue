<template>
    <md-layout>
      <md-layout-item class="md-size-100 md-title">
        To Do
      </md-layout-item>
      <md-layout-item>
            <md-field>
              <label>To Do</label>
              <md-input type="text" v-model="newLine"></md-input>
              <button  v-on:click="addData" class='md-raised'></button>
            </md-field>
            <md-button v-on:click="addData" class='md-raised'>Add</md-button>

            <ol>
                <todo-item
                    v-for="item in dataList"
                    v-bind:todo="item"
                    v-bind:key="item.id"
                ></todo-item>
            </ol>

      </md-layout-item>
  </md-layout>
</template>

<script>

import Vue from 'vue'
import VueMaterial from 'vue-material'
import 'vue-material/dist/vue-material.min.css'
import 'vue-material/dist/theme/default.css'

Vue.use(VueMaterial);

      Vue.component('todo-item',{
          props: ['todo'],
          template: '<li>{{ todo.text }}</li>'
      });

export default {
    name: 'TodoComponent',
    data: {
              newLine: '',
              dataList:[]
          },
          methods: {
              addData: function(e) {
                  e.preventDefault();
                  this.dataList.push({"id":this.dataList.length+1, "text":this.newLine});
              }
          }
};
</script>