<template>
    <div>
        <p> {{title}} Reaction time: {{ score }} ms</p>
        <p class="rank"> {{rank}} </p>
    </div>
</template>

<script>
    export default {
        props: ['title', 'score'],
        data(){
            return{
                rank: null,
            }
        }
        ,
        mounted() {
            if(this.score <250){
                this.rank = 'Assasin Spped'
            } else if(this.score < 400){
                this.rank = 'Ninja Speed'
            } else {
                this.rank = 'Snail Speed ... '
            }
        }
    }
</script>

<style>
    .rank{
        font-size: 20px;
        color: #676;
        font-weight: 500;
    }
</style>