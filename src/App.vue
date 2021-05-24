<template>
  <!-- <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div> -->
  <div id="app" class="small-container">
    <h1>Employees</h1>

    <employee-form @add:employee="addEmployee" />
    <employee-table v-bind:employees="employees" />
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

// export default {
//   name: 'App',
//   components: {
//     HelloWorld
//   }
// }
import EmployeeTable from '@/components/EmployeeTable.vue'
// import EmployeeForm from '@/components/EmployeeForm.vue'
import EmployeeForm from './components/EmployeeForm.vue'

  export default {
    name: 'app',
    components: {
      EmployeeTable,
      EmployeeForm
    },

    data() {
      return {
        employees: [
        {
          id: 1,
          name: 'Victor Pravo',
          email: 'vpravo@vpravo.com',
        },
        {
          id: 2,
          name: 'Rembrandt Rey',
          email: 'rrey@rrey.com',
        },
        {
          id: 3,
          name: 'Taka Got',
          email: 'tgot@tgot.com',
        },
      ],
      }
    },

    methods: {
      addEmployee(employee) {
        const lastId = this.employees.length > 0 ? this.employees[this.employees.length - 1].id : 0;
        const id = lastId + 1;
        const newEmployee = {
          ...employee,
          id,
        }
        this.employees = [...this.employees, newEmployee];
      }
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
  button {
    background: #009435;
    border: 1px solid #009435;
    border-radius: 5px;
    max-width: 75px;
  }

  .small-container {
    /* max-width: 680px; */
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
    align-items: center;
  }
</style>
