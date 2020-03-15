<template>
  <div>
    <div :key="expense.id" v-for="expense in expenses">
      <ExpenseItem :expense="expense" @del-expense="$emit('del-expense', expense.id)" />
    </div>
  </div>
</template>

<script>
import ExpenseItem from './ExpenseItem';

export default {
  name: 'Expenses',
  components: {
    ExpenseItem
  },
  props: ["expenses"]
  
}
</script>

