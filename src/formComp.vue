<template>
<div id="app">

  <table id="users-table" class="table">
    <thead><tr>

      <th>id</th>
      <th>name</th>
      <th>email</th>
      <th>address</th>
      <th>job_title</th>
      <th>phone_country_code</th>
      <th>two_factor_options</th>
      <th>integration_id</th>
      <th>gateway</th>
      <th>card_brand</th>
      <th>card_last_four</th>
      <th>trial_ends_at</th>
      <th>payment_method_token</th>
      <th>created_by</th>
      <th>updated_by</th>
      <th>deleted_at</th>
      <th>created_at</th>
      <th>updated_at</th>
      <th>notification_preferences</th>
      <th>reward_points</th>
    </tr></thead>

  </table>


</div>
</template>

<script>
    $(function() {
      $('#users-table').DataTable({
        processing: true,
        serverSide: true,
        ajax: 'http://localhost:8080/task/public/',
        columns: [
          {data: 'id'},
          {data: 'name'},
          {data: 'email'},
          {data: 'address'},
          {data: 'job_title'},
          {data: 'phone_country_code'},
          {data: 'two_factor_options'},
          {data: 'integration_id'},
          {data: 'gateway'},
          {data: 'card_brand'},
          {data: 'card_last_four'},
          {data: 'trial_ends_at'},
          {data: 'payment_method_token'},
          {data: 'created_by'},
          {data: 'updated_by'},
          {data: 'deleted_at'},
          {data: 'created_at'},
          {data: 'updated_at'},
          {data: 'notification_preferences'},
          {data: 'reward_points'},


        ]
      });
    });

  export default {


  }

</script>

<style>

</style>
