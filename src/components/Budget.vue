<template>
    <div class="budget">
        <p>How much can i spend?</p>
        <input type="number" placeholder="Enter your budget" v-model="budget">
        <h1>{{remaining}}€</h1>
    </div>
</template>
<script>


export default {
    props: ['expenses'],
    name: "budget",
    data() {
        return {
            budget:''
        }
    },
    computed: {
        remaining() {

            let remaining = parseFloat(this.budget);
            this.expenses.forEach( expense => {
                remaining -= parseFloat(expense.value);
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
        background: #333;
        color: #fff;
        text-align: center;
        padding: 10px;
    }
    .budget p {
        font-size: 30px;
        margin-bottom: 10px;
    }

    input {
        text-align: center;
    }
    h1 {
        font-weight: 300;
        font-size: 50px;
    }

    
</style>