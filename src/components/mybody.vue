<template>
<div>
<table class="table text-center">
        <thead>
          <tr>
             <th scope="col">ID</th>
            <th scope="col">Name</th>
            <th scope="col">City</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="student in students" :key="student.id">
            <td>{{student.ID}}</td>
            <td>{{student.name}}</td>
            <td>{{student.city}}</td>
          </tr>
        </tbody>
      </table>
  </div>
</template>

<script>
import students from '../students'
export default {
   data:()=>({
            students:students,
    }),
}
</script>

<style>

</style>