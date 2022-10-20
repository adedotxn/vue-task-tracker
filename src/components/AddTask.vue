<template>
    <form @submit="onSubmit" action="" class="add-form">
        <div class="form-inputs">
            <div class="form-control">
                <label for="">Task</label>
                <input v-model="text" type="text" name="text" id="" placeholder="Add Task">
            </div>


            <div class="form-control">
                <label for="">Day & Time</label>
                <input type="text" v-model="day" name="day" placeholder="Add Day & Time">
            </div>

            <div class="form-control">
                <label for="">Set Reminder</label>
                <input  v-model="reminder" type="checkbox"  name="reminder">
            </div>
        </div>

        <div class="submitt">  
            <input type="submit" value="Save Task" class="btn btn-block">
        </div>
    </form>
</template>


<script lang = "ts">
    export default {
        name : "AddTask",
        data() {
            return {
                text : '',
                day : `${Date.now()}`,
                reminder : false
            }
        },
        methods : {
            onSubmit(e : Event) {
                e.preventDefault()

                if(!this.text) {
                    return alert("please add a task")
                }

                const newTask = {
                    id : Math.floor(Math.random() * 10000),
                    text : this.text,
                    day : this.day,
                    reminder : this.reminder
                }

                this.$emit('add-task', newTask)

                this.text = this.day = " "
                this.reminder = false

                console.log("newTask", newTask)
            }
        }
    }
</script>


<style scoped>
.add-form {
    display: grid;
    place-items: center;
    /* margin : 0rem 1rem; */
}
.form-inputs {
    display: flex;
    gap: 2rem;
}

.form-control {
    display: grid;
}

.submitt {
    margin-top: .5rem;
}
</style>