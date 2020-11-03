<template>
  <div id="employee-table">
    <table>
      <thead>
        <tr>
          <th>Employee name</th>
          <th>Employee email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="employee in employees" :key="employee.id">
          <td>{{ employee.name }}</td>
          <td>{{ employee.email }}</td>
          <button @click="() => deleteEmployee(employee.id)">Delete</button>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
    export default {
        name: 'employee-table',
        props: {
            employees: Array,
        },

        methods: {
            deleteEmployee(id) {
                console.log(id);
                this.$emit('delete-employee', id)
            }
        }
    }
</script>

<style scoped></style>