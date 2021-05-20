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
        <tr>
          <td>Victor Pravo</td>
          <td>vpravo@vpravo.com</td>
        </tr>
        <tr>
          <td>Rembrandt Rey</td>
          <td>rrey@rrey.com</td>
        </tr>
        <tr>
          <td>Taka Got</td>
          <td>tgot@tgot.com</td>
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
    }
  }
</script>

<style scoped></style>