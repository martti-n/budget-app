<template>
    <div class="budget">
        <p>{{budget}}</p>
        <input type="number" placeholder="Enter your budget" v-model="budget">
    </div>
</template>
<script>


export default {
    name: "budget",
    data() {
        return {
            budget:''
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
        font-size: 50px;
    }
</style>