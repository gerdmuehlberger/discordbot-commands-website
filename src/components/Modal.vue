<template>
    <div class="back" @click.self="closeCommandModal">
        <div class="modal" :class="{ darkmode: darkmode === true }">
            <h1>{{ modalheader }}</h1>
            <p id="p-desc">{{ modaldesc }}</p>
            <p id="p-args">Arguments: {{ modalargs }} </p>
        </div>
    </div>
</template>

<script>
export default {
    props: ['modalheader', 'modaldesc', 'modalargs', 'darkmode'],
    methods: {
        closeCommandModal(){
            this.$emit('close')
        }
    }
}
</script>

<style scoped>
    .modal{

        width: 450px;
        height: 200px;
        padding: 10px;
        margin: 15% auto;
        background: white;
        border-radius: 10px;
    }

    .back {
        top: 0;
        position: fixed;
        background: rgba(0,0,0,0.5);
        width: 100%;
        height: 100%;
    }

    h1{
        margin-top: 10%;
        color:#7289da;
        font-size: 2em;
    }


    #p-desc{
        font-style: italic;
    }


    #p-args{
        font-weight: bold;
    }

    .darkmode{
        background: black;
        color: white;

    }

    .darkmode h1{
        color: white;
    }


</style>