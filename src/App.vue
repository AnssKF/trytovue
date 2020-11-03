<template>
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <hr>
  <EmployeeForm @add-employee="addEmployee" />
  <hr>
  <EmployeeTable :employees="employees" @delete-employee="deleteEmployee"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import EmployeeTable from './components/EmployeeTable.vue'
import EmployeeForm from './components/EmployeeForm.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    EmployeeTable,
    EmployeeForm
  },
  data() {
    return {
      employees: [
        {
          id: 1,
          name: 'Richard Hendricks',
          email: 'richard@piedpiper.com',
        },
        {
          id: 2,
          name: 'Bertram Gilfoyle',
          email: 'gilfoyle@piedpiper.com',
        },
        {
          id: 3,
          name: 'Dinesh Chugtai',
          email: 'dinesh@piedpiper.com',
        },
      ],
    }
  },
  methods: {
    addEmployee(employee) {
    const lastId = this.employees.length > 0 ? this.employees[this.employees.length - 1].id : 0;
    const id = lastId + 1;
    const newEmployee = { ...employee, id };

      this.employees = [...this.employees, newEmployee]
    }
  },

  deleteEmployee(id) {
    console.log(id);
    this.employees = this.employees.filter( x => (x.id !== id))
    console.log(this.employees)
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
