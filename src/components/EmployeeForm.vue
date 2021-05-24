<template>
    <div id="employee-form">
        <form @submit.prevent="handleSubmit">
            <label>Employee Name</label>
            <input type="text" v-model="employee.name"/>
            <label>Employee Email</label>
            <input type="text" v-model="employee.email"/>
            <button>Add Employee</button>
        </form>
    </div>
</template>

<script>
    export default {
        name:'employee-form',
        data() {
            return {
                employee: {
                    name: '',
                    email: '',
                }
            }
        },
        methods: {
            handleSubmit() {
                console.log('testing handleSubmit')
                this.$emit('add:employee', this.employee)
            },
        },
    }
</script>

<style scoped>
    #employee-form {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        max-width: 680px;
        height: 150px;
    }

    form {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        height: 100%;
    }
</style>
