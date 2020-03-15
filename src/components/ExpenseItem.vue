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
    props: ["expense", "mode"],
    
}
</script>

<style scoped>
    .expense-item {
        padding: 10px;
        font-weight: 400;
        background-color: #192734;
        color: #fff;
        width: 75%;
        margin: 0 auto;
        border: 1px solid #15202b;
        transition: background 0.2s
      }

      .expense-item:hover {
          background: #1f2e3d;
      }

      .light .expense-item {
    
          background-color: #f3f3f3;
          border: 0.3px solid black;
          color: black;
          transition: background 0.2s;
      }

      .light .expense-item:hover {
          background-color: #e9e8e8;
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
          background: #15202b;
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

      .light .del {
          background: #f3f3f3;
          color: black;
          border-radius: 49%;
          border: black solid 1px;
          transition: background 0.2s color 0.2s;
      }

      .light .del:hover {
          background: black;
          color: #f3f3f3;
      }
</style>