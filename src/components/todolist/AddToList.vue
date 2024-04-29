<template>
    <base-dialog v-if="inputIsInvalid" @close="confirmError">
        <template #default>
            <p>Invalid!</p>
            <p>You must add at least a few characters! </p>
        </template>
        <template #actions> 
            <base-button @click="confirmError">OK</base-button>
        </template>
    </base-dialog>
    <base-card class="add-form">       
        <form @submit.prevent="submitData" class="form">
            <label for="todo">New task</label>
            <div class="input-button-row">
                <input type="text" v-model="text" placeholder="Add your text here" class="input-field"
                :class="{ 'active': isInputClicked }" 
                @focus="isInputClicked = true"
                @blur="isInputClicked = false">
                <base-button type="submit">Add</base-button>   
            </div>         
        </form>
    </base-card>
</template>

<script>
export default {  
    data() {
        return {
            text: "",
            inputIsInvalid: false,
            isInputClicked: false,
        };
    },
    methods: {
        submitData() {    
            if (this.text.trim() === "") {
                this.inputIsInvalid = true;
            } else {               
                this.$emit('task-added', this.text);            
                this.text = '';
            }
        },
        confirmError() {
            this.inputIsInvalid = false;
        }
    }
}
</script>

<style scoped>
.add-form {
    display: flex;
    flex-direction: column;
    align-items: stretch;
}

.form {
    display: flex;
    flex-direction: column;
}

label {
    font-size: 1.4rem;
    margin-bottom: 0.5rem;
    color: rgb(6, 6, 97);
    font-weight: bold;
    text-align: center;
}

.input-button-row {
    display: flex;
}

.input-field {
    flex-grow: 1;
    padding: 0.5rem;
    margin-right: 0.5rem;
    font-size: 1rem;
    color:  rgb(2, 2, 48);
    border: 1px solid rgb(6, 6, 97);
    border-radius: 4px;
    box-sizing: border-box;
}

.base-button {
    margin-top: 0;
}

.input-field.active {
  border: 1px solid rgb(6, 6, 97);
  outline: 2px solid rgb(6, 6, 97); 
}

</style>