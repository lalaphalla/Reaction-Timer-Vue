//Multiple component
<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{ sale: theme === 'sale'}">
            <!-- <h1> {{ header }} </h1>
            <p> {{text}} </p> -->
            <slot></slot>
            <div class="action">
                <slot name="links"></slot>
            </div>
        </div>        
    </div>
</template>

<script>
export default {
    props: ['header','text', 'theme', 'showModal']
    ,
    methods: {
        closeModal(){
            //Custom Event
            //Emitting a close event
            //this.props.showModal = !this.props.showModal
            this.$emit('close')
        }
    },
}


</script>

<style>
    .modal{
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: #fff;
        border-radius: 20px;
    }
    .backdrop{
        top: 0;
        position: fixed;
        background: rgba(0,0,0,0.5);
        width: 100%;
        height: 100%;
    }

    .modal.sale{
        background: crimson;
        color: white;
    }
    .modal.modal.sale h1{
        color: #fff;
    }
    .modal .actions{
        text-align: center;
        margin: 30px 0 10px 0;    
    }
    a{
        text-decoration: none;
        background: #333;
        color: #fff;    
        padding: .5rem 2rem;
        border-radius: 20px;
        margin: 10px;

    }

</style>