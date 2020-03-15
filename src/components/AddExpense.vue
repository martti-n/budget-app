<template>
    <div class="input-field">
        <form @submit="addExpense">
            <input type="text1" v-model="title" name="title" placeholder="Add item">
            <input type="number" step="0.01" v-model="value" name="value" placeholder="Add value">
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
                return alert('Add an item first!')
            } else if(this.value === '') {
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
          flex: 3;
          padding: 5px;
    }

    input[type="submit"] {
          flex: 2;
    }
</style>