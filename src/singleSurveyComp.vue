<template>
  <div id="app">

    <div class="panel panel-defaullt">
      <div class="panel-body">
        <tr>
        <th scope="row">
          {{qt.id}}</th>
        <td>{{qt.name}}</td>
        <td><button style="margin-left:80% " v-on:click="onEdit(qt.id)" id="button1" class="btn btn-success ">Edit</button></td>
        </tr>

      </div>
      <div class="panel-footer">
        <div v-if="editing">
          <input type="text" v-model="editValue">
          <select  v-model="selected" class="form-control" id="sel1">
            <option v-for="option in options" v-bind:value="option.id">{{option.name}}</option>

          </select>


          <a  v-on:click="onUpdateSave">Save</a>

        </div>
        <div v-if="!editing">

        </div>

      </div>

    </div>

  </div>
</template>

<script>
  import axios from 'axios'
  export default {
    props:['qt','qtoption'],
    data(){
      return{
        editing:false,
        editValue:this.qt.name,
        id:this.qt.id,
        selected:'',
        surveyId:'',

        options: [],
      }
    },

    mounted(){
      axios.get('http://localhost:8000/getUsers')
        .then(
          response =>
          {
            this.options = response.data;
            console.log(this.options);
          }
        ).catch(
        (error)=>console.log(error)
      )// catch() ends
    },

    methods:{

      onUpdateSave(){
        this.editing = false;
        this.qt.name = this.editValue;
        this.qt.id = this.editUserOption;

        console.log(this.editValue);
        console.log( this.surveyId);
        console.log(this.selected);
        axios.post('http://localhost:8000/editSurvey',{name:this.editValue,surveyId:this.surveyId,userId:this.selected})
          .then(
            response => console.log(response)
          ).catch(
          error => console.log(error)
        )
      },


      onEdit(id){
        this.editing = true;
        this.editValue = this.qt.name;
        this.surveyId = id;
        this.selected = this.option
      },



    }


  }
</script>

<style>

</style>
