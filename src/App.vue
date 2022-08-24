<template>
  <div >
      <div class="box">
          <div class="red" ref="red"></div>
          <div class="yellow" ref="yellow"></div>
          <div class="green" ref="green"></div>
      </div>

  </div>
</template>

<script>





export default {
    data(){
      return {

      }
    },
    methods:{
       hld(){
        this.$refs.red.style.backgroundColor = 'red'
        setTimeout(() => {
        this.$refs.red.style.backgroundColor = ''
        this.$refs.yellow.style.backgroundColor = 'yellow'
        }, 3000);
        setTimeout(() => {
        this.$refs.red.style.backgroundColor = ''
        this.$refs.yellow.style.backgroundColor = ''
        this.$refs.green.style.backgroundColor = 'green'

        }, 4000);
        setTimeout(()=>{
          this.$refs.green.style.backgroundColor = ''
          this.hld()
        },7000)
      },
      //promise方法
      PromiseHDL(seconds){
          return new Promise((resolve)=>{
              setTimeout(()=> resolve(),seconds)
          })
      },
      async PromiseHDLopen(){
        this.$refs.red.style.backgroundColor = 'red'
        await this.PromiseHDL(3000)
        this.$refs.red.style.backgroundColor = ''
        this.$refs.yellow.style.backgroundColor = 'yellow'
        await this.PromiseHDL(1000)
        this.$refs.red.style.backgroundColor = ''
        this.$refs.yellow.style.backgroundColor = ''
        this.$refs.green.style.backgroundColor = 'green'
        await this.PromiseHDL(3000)
        this.$refs.green.style.backgroundColor = ''
        this.PromiseHDLopen()
      }


    },
    mounted(){
      // this.hld()
      this.PromiseHDLopen()
    }


}
</script>

<style >
   .box {
        display: flex;
        justify-content: space-around;
        align-items: center;
        width: 600px;
        height: 200px;
        border-radius: 15px;
        background-color: #333333;
   }
   .red,
   .green,
   .yellow {
        width: 160px;
        height: 160px;
        border-radius: 90px;
        background-color: #fff;
   }
</style>
