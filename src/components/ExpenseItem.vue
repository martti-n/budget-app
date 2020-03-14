<template>
    <div class="expense-item">
        <div class="row">
            <div class="col-1">
                {{expense.title}}
            </div>
            <div class="col-2">
                - {{expense.value}}€
                <button @click="$emit('del-expense', expense.id)" class="del">x</button>
            </div>        
        </div>
             
    </div>
    
</template>
<script>
export default {
    name: "ExpenseItem",
    props: ["expense"],
    
}
</script>
<style scoped>
    

    .expense-item {
        padding: 10px;
        font-weight: 400;
        background-color: rgb(70, 70, 70);
        color: #fff;
        width: 75%;
        margin: 0 auto;
        border-bottom: 1px solid rgb(80, 80, 80);
        transition: background 0.2s
    }

    .expense-item:hover {
        background: rgb(90, 89, 89);
    }

    .row {
        margin: 0 auto;
        display: flex;
        justify-content: center;
    }

    .col-1 {
        width: 55%;
    }
    .col-2 {
        width: 45%;
        float: right;
    }

    .del {
        background: #333;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
        transition: background 0.2s;
    }
    .del:hover {
        background: #e76262;
    }
</style>