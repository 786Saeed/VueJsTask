<!-- Latest compiled and minified CSS -->
<template>
  <div id="app"><div class="row ">
    <div class="col-md-offset-3 col-md-6">
      <div class="panel panel-default ">
        <div class="panel-heading" style="text-align:center">Add Survey</div>
        <div class="panel-body">
          <form class="form-inline" >
            <label id="nameLabel" for="name">Name:</label>
            <input  type="name" class="form-control" v-model="name" id="name">
            <!--<br/>-->

            <div class="form-group">
              <label for="sel1">Select list:</label>
              <select  v-model="selected" class="form-control" id="sel1">
                <option v-for="option in options" v-bind:value="option.id">{{option.name}}</option>

              </select>
            </div>
            <div class="row">
              <button id="button" v-on:click="addSurvey" class="btn btn-success col-md-offset-4 col-md-4">Add</button>
            </div>
          </form>
        </div>


      </div>
    </div>

  </div>
    <div class="row">
      <div class="col-md-offset-2 col-md-8">
        <table class="table">
          <thead>

          </thead>
          <tbody>
          <tr v-for="survey in surveys" v-bind:value="survey.id">

            <single-survey :qt="survey" :qtoption="editUserId"></single-survey>

            <td>
            <button style="" id="button1" v-on:click="deleteSurvey(survey.id)"  class="btn btn-danger">Delete</button></td>
          </tr>

          </tbody>
        </table>
      </div>




    </div>
  </div>
</template>


<script>
  import formComp from './formComp.vue';
  import singleSurvey from './singleSurveyComp.vue'
  import axios from 'axios'

  export default {
    name: 'App',
    props:['qt','qtoption'],
    components: {
      'formComp': formComp,
      'single-survey':singleSurvey
    },

    data() {

      return {
        editing:false,
        editValue:this.surveys,
        options: [],
        surveys:[],
        selected:'',
        name:'',
        id:'',
        editName:'',
        editUserId:this.options,



      }

    },
    created(){
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
    mounted(){
      axios.get('http://localhost:8000/getSurveys')
        .then(
          response =>
          {
            this.surveys = response.data;
            console.log(this.surveys);
          }
        ).catch(
        (error)=>console.log(error)
      )// catch() ends

    },
    methods: {
      addSurvey(){
        axios.post('http://localhost:8000/addSurvey',{name:this.name,userId:this.selected})
          .then(
            response =>
            {

              console.log(response);
            }
          ).catch(
          (error)=>console.log(error)
        )// catch() ends

alert('Survey Added Successfully');
      },
      deleteSurvey(id){

        axios.post('http://localhost:8000/deleteSurvey',{id:id})
          .then(
            response =>
            {
              this.surveys = response.data; // extracting quotes from response and assigning it.
              console.log(response);
            }
          ).catch(
          (error)=>console.log(error)
        )// catch() ends
        alert('Survey Deleted Successfully');

      },



    },


    }



</script>

<style>
  #button {

    margin-top: 5%;
  }
</style>


