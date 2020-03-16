<template>
    <div class="budget">
        <Toggle :mode="mode" @toggle="$emit('toggle')"/>
        <p>How much can i spend?</p>
        <input type="number" step="0.01" placeholder="Enter your budget" v-model="budget">
        <h1>{{remaining}}€</h1>
    </div>
</template>
<script>
import Toggle from './Toggle.vue'

export default {
    props: ['expenses', 'mode'],
    name: "budget",
    data() {
        return {
            budget:''
        }
    },
    mounted() {
        this.budget = JSON.parse(localStorage.budget);
    },
    watch: {
        budget(newBudget) {
            localStorage.budget = JSON.stringify(newBudget);
        }
    },
    components: {
        Toggle
    },
    computed: {
        remaining() {

            let remaining = parseFloat(this.budget);
            this.expenses.forEach( expense => {
                remaining -= expense.value;
            })
            
            if (isNaN(remaining) == true) {
                return 0
            }

            return remaining;
        }
    
    }

}
    

</script>

<style scoped>
    .budget {
        color: #fff;
        text-align: center;
        padding: 10px;
      }
    .budget p {
        font-size: 30px;
        margin-bottom: 10px;
        margin-right: 60px;
      }

    input {
        text-align: center;
      }
    h1 {
        font-weight: 300;
        font-size: 50px;
      }

    .light .budget {
        color: black;
      }
</style>