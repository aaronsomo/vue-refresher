<template>
    <div id="employee-table">
        <table>
            <thead>
                <tr class="table-header">
                    <th>Employee name</th>
                    <th>Employee email</th>
                </tr>
            </thead>
            <tbody>
                <tr class="table-contents" v-for="employee in employees" :key ="employee.id">
                    <td>{{ employee.name }}</td>
                    <td>{{ employee.email }}</td>
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

<style scoped>
    #employee-table {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }

    table {
        display: flex;
        flex-direction: column;
        width: 300px;

    }

    .table-header {
        display: flex;
        justify-content: space-between;
    }

    .table-contents {
        display: flex;
        justify-content: space-between;
    }
</style>