<template>
    <div>
        <add-to-list @task-added="addTask"></add-to-list>
        <ul class="task-list">            
            <li v-for="task in addedTasks" :key="task.id">
                <base-card class="list-item"> 
                    <div class="task-container">
                        <div class="task" :class="{ 'completed': task.completed }">{{ task.task }} </div>
                        <div class="actions">             
                            <base-button mode="flat" @click="doneCheck(task)">Done</base-button>
                            <base-button mode="flat" @click="deleteItem(task)">Delete</base-button>
                        </div>   
                    </div>                               
                </base-card>
            </li>            
        </ul>
    </div>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
import BaseCard from '../UI/BaseCard.vue';
import AddToList from './AddToList.vue';

export default {
    components: {
        AddToList,
        BaseButton,
        BaseCard, 
    },
    data() {
        return {
            addedTasks: [],                      
        };
    },
    methods: {       
        addTask(task) {                 
            this.addedTasks.unshift({
                task,
                id: new Date().toISOString(),
                completed: false,
            });
        },
        deleteItem(task) {
            const taskIndex = this.addedTasks.findIndex((item) => item.id === task.id); 
            if (taskIndex !== -1) {
                this.addedTasks.splice(taskIndex, 1);
            }
        },
        doneCheck(task) {
            task.completed = !task.completed; 
        },
    },  
};
</script>

<style scoped>
.task-list {
    padding: 0;
    margin: 0;
    list-style: none;
    font-size: 1.1rem;
    color: rgb(2, 2, 48);
}

.completed {
    color: gray;
    text-decoration: line-through;
    text-decoration-color: rgb(42, 42, 42);
}

.list-item {
    margin-bottom: 10px; 
}

.task-container {
    display: grid;
    grid-template-columns: 1fr auto;
    align-items: center;
}

.task {
    overflow-wrap: break-word; 
    word-wrap: break-word;
    word-break: break-word;
    hyphens: auto; 
}

.actions {
    display: flex;
    justify-content: flex-end; 
}
</style>