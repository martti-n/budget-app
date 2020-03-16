<template>
  <div class="app" :class="mode">
    <Budget :expenses="expenses" :mode="mode" @toggle="toggle"/>
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
      mode: 'light',
      expenses: []
    }
  },
  mounted() {
    if(localStorage.expenses) {
      this.expenses = JSON.parse(localStorage.expenses);
    }
    this.mode = JSON.parse(localStorage.mode);
  },
  watch: {
    expenses(newExpenses) {
      localStorage.expenses = JSON.stringify(newExpenses);
    },
    mode(newMode){
      localStorage.mode = JSON.stringify(newMode);
    }
  },
  methods: {
    deleteExpense(id) {
      this.expenses = this.expenses.filter(expense => expense.id !== id);
    },
    addExpense(newExpense) {
      this.expenses = [...this.expenses, newExpense];
    },
    toggle() {
      if(this.mode === 'dark') {
        this.mode = 'light';
      } else {
        this.mode = 'dark'
      }
    }

  }
}
</script>

<style>
      * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
        font-family: 'Roboto', sans-serif;
        line-height: 1.4;
        font-weight: 400;
      }
      
      .app {
        background: #15202b;
        color: #f3f3f3;
        width: 100vw;
        min-height: 100vh;
        transition: background 0.3s ease-in-out;

      }
      .btn {
        display: inline-block;
        border: none;
        background: #192938;
        border: 1px solid #f3f3f3;
        padding: 7px 20px;
        cursor: pointer;
        color: #f3f3f3;
        transition: background 0.2s;
      }

      .btn:hover {
        background: #1f2e3d;
      }
    
      .light {
        background-color: #f3f3f3;
        color: black;
      }

      .light .btn {
        background: #f3f3f3;
        border: 1px solid  rgb(119, 118, 118);
        color: black;
        transition: background 0.2s color 0.2s;
      }

      .light .btn:hover {
        background: #e9e8e8;
        color: black;
      }


</style>
