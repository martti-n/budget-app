<template>
    <div class="input-field">
        <form @submit="addExpense">
            <input type="text1" id="text1" v-model="title" name="title" placeholder="Add item">
            <input type="number" step="0.01" min="0" v-model="value" name="value" placeholder="Add value" style="width: 7em">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>
<script>
import {v4} from 'uuid';
export default {
    name: "AddExpense",
    props: ['budget'],
    data() {
        return {
            title: '',
            value: ''
        }
    },
    methods: {
        addExpense(e) {
            if(this.title === '') {
                e.preventDefault();
                return alert('Add an item first!')
            } else if(this.value === '') {
                e.preventDefault();
                return alert('Add a value to the item!')
            }
            e.preventDefault();
            const newExpense = {
                id: v4(),
                title: this.title,
                value: this.value
            }

            this.$emit('add-expense', newExpense);

            this.title = '';
            this.value = '';
            document.getElementById("text1").focus();
            
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
        margin: 0 auto;
        width: 75%;
    }


    input[type="text1"] {
          flex: 7;
          padding: 5px;
    }
    input [type="number"] {
          padding: 5px;
    }

    input[type="submit"] {
          flex: 2;
          padding: 5px;
    }

    @media only screen and (max-width: 516px) {
        input[type="text1"] {
            display: block;
            width:50%;
        }
        
        

    }
</style>