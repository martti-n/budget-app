<template>
  <div id="app">
    <Budget :expenses="expenses"/>
    <AddExpense @add-expense="addExpense"/>
    <Expenses :expenses="expenses" @del-expense="deleteExpense"/>
  </div>
</template>

<script>
import Budget from './components/Budget';
import Expenses from './components/Expenses';
import AddExpense from './components/AddExpense'
export default {
  name: 'app',
  components: {
    Budget,
    Expenses,
    AddExpense
  },
  data() {
    return {
      expenses: []
    }
  },
  methods: {
    deleteExpense(id) {
      this.expenses = this.expenses.filter(expense => expense.id !== id);
    },
    addExpense(newExpense) {
      this.expenses = [...this.expenses, newExpense];
    }

  }
}
</script>

<style>
      * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
      }
      body {
        font-family: Arial, Helvetica, sans-serif;
        line-height: 1.4;
        background: #333;
      }
      .btn {
        display: inline-block;
        border: none;
        background: #555;
        color: #fff;
        padding: 7px 20px;
        cursor: pointer;
      }

      .btn:hover {
        background: #666;
      }  
</style>
