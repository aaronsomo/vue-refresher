<template>
    <div id="employee-form">
        <form @submit.prevent="handleSubmit">
            <label>Employee Name</label>
            <input
                type="text"
                ref="first"
                :class="{ 'has-error': submitting && invalidName }"
                v-model="employee.name"
                @focus="clearStatus"
                @keypress="clearStatus"
            />
            <label>Employee Email</label>
            <input
                type="text"
                :class="{ 'has-error': submitting && invalidEmail }"
                v-model="employee.email"
                @focus="clearStatus"
            />
            <p
                v-if="error && submitting"
                class="error-message"
            >
                !Please enter all required fields
            </p>
            <p
                v-if="success"
                class="success-message"
            >
                !Employee successfully added
            </p>
            <button>Add Employee</button>
        </form>
    </div>
</template>

<script>
    export default {
        name:'employee-form',
        data() {
            return {
                submitting: false,
                error: false,
                success: false,
                employee: {
                    name: '',
                    email: '',
                },
            }
        },

        methods: {
            handleSubmit() {
                console.log('testing handleSubmit')

                this.submitting = true;
                this.clearStatus();

                if (this.invalidName || this.invalidEmail) {
                    this.error = true;
                    return;
                }

                // add typed in employee fields to employee list
                this.$emit('add:employee', this.employee)

                // automatically go to first field after form submission
                this.$refs.first.focus()

                // reset employee after adding to list
                this.employee = {
                    name: '',
                    email: '',
                }

                // reset submitting, error, and success
                this.submitting = false;
                this.error = false;
                this.success = true;
            },

            clearStatus() {
                this.success = false;
                this.error = false;
            }
        },

        computed: {
            invalidName() {
                return this.employee.name === '';
            },

            invalidEmail() {
                return this.employee.email === '';
            },
        }
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

    [class*='-message'] {
        font-weight: 500;
    }

    .error-message {
        color: #d33c40;
    }

    .success-message {
        color: #32a95d;
    }
</style>
