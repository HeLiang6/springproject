<template>
    <div class="wrapper" ref="wrapper">
        <slot></slot>
    </div>
</template>
<script>
import BScroll from "better-scroll"
export default {
    name:"Bscroll",
   mounted() {
    this.scroll = new BScroll(this.$refs.wrapper, {
      probeType: 1,
      tap:true,
      click:true
    });    
    },
    methods:{
        handleScrollTo(y){
            this.scroll.scrollTo(0,y,300)
        },
        handleScrollStart(cb){
            this.scroll.on("scroll",({x,y})=>{
                if(y>30){
                    cb()
                }
            })
        }
    }
}
</script>
<style>
    .wrapper{
        height: 100%;
    }
</style>


