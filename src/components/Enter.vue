<template>
    <div class="hello">
        <h1>Are you feeling lucky?</h1>
        <p>
            <input type="text" value=""/>
        </p>
        <button @click="getInvoice($event, '10000')">Enter</button>
    </div>
</template>

<script>
    export default {
        name: 'Enter',
        props: {
            msg: String
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 {
        margin: 40px 0 0;
    }
    ul {
        list-style-type: none;
        padding: 0;
    }
    li {
        display: inline-block;
        margin: 0 10px;
    }
    a {
        color: #42b983;
    }
</style>
