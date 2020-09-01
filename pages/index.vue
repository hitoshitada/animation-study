<template>
 <div id="app">
   
  
    <button type="button" @click="shuffle">Shuffle</button>
    
  <transition-group tag="div" name="list">
   
   <!-- <p v-for="(item,index) in list" :key="item.cla">{{item.cla}}</p> :class="item.cla"-->
   
    <component v-for="(item,index) in list" :is="item.comp" class="svga" :style="styles" :key="item.cla" width=100 height=100>
    </component> 
      
  </transition-group>
 </div>
</template>

<script>
import SampleSvg1 from '@/assets/spaceship.svg';
import SampleSvg2 from '@/assets/archive-2.svg';
import SampleSvg3 from '@/assets/animated_icons-02.svg';
import SampleSvg4 from '@/assets/UFO.svg';
import SampleSvg5 from '@/assets/coffee.svg';
import SampleSvg6 from '@/assets/post.svg';

export default {
  components: {
    SampleSvg1,
    SampleSvg2,
    SampleSvg3,
     SampleSvg4,
     SampleSvg5,
     SampleSvg6,
  },
  data:function(){
    return{
    maxId: 3,
    list: [
    {comp:SampleSvg1,cla:"svga"},
    {comp:SampleSvg2,cla:"svg2"},
    {comp:SampleSvg3,cla:"svg3"},
    {comp:SampleSvg4,cla:"svg4"},
    {comp:SampleSvg5,cla:"svg5"},
    {comp:SampleSvg6,cla:"svg6"}
    ],
        
    

    }
  },
 computed:{
    styles:function(){
      return{
      '--top': '200px',
      '--left': '300px' }
      },


 },

    

  methods:{
    random:function(max){
      return Math.floor(Math.random() * (max + 1))
    },
    
    shuffle:function(){
     
      for(let i = this.list.length - 1; i > 0; i--){
    let r = Math.floor(Math.random() * (i + 1));
    let tmp = this.list[i].comp;
    this.list[i].comp= this.list[r].comp;
    this.list[r].comp = tmp;
    let tmp2 = this.list[i].cla;
    this.list[i].cla= this.list[r].cla;
    this.list[r].cla = tmp2;

}
    },
    },
  }

</script>
<style scoped>

body {
  padding: 20px;
  font-size: 18px;
  font-family: sans-serif;
}


.list-position{
  display:flex;
}


.svg1{
   position: absolute;
  top:  100px;
  left: 200px;
}

.svg2{
   position: absolute;
  top:  250px;
  left: 200px;
}
.svg3{
   position: absolute;
  top:  400px;
  left: 200px;
}
.svg4{
   position: absolute;
  top:  100px;
  left: 350px;
}
.svg5{
   position: absolute;
  top:  250px;
  left: 350px;
}
.svg6{
   position: absolute;
  top:  400px;
  left: 350px;
}




.svga{
   --top: 200px;
   --left: 400px;
   position: absolute;
   top: var(--top);
   left: var(--left);
  
}

button {
  padding: 8px 30px;
  border-width: 0;
  background-color: #505050;
  color: #fff;
  font-family: inherit;
  font-size: inherit;
  cursor: pointer;
  transition: opacity 100ms ease-out;
}

button:hover {
  opacity: 0.7;
}

ul {
  position: relative;
  padding-top: 18px;
  width: 420px;
}

li {
  display: block;
  margin-top: 8px;
  padding: 8px 12px;
  width: 100%;
  background-color: #e5e5e5;
}

.list-enter-active,
.list-leave-active,
.list-move
{
    transition: opacity 1s, transform 1s;

}

 

.list-enter {
  opacity: 0;
  transform: translateX(200px) scaleY(0.5);
}

.list-enter-to {
  opacity: 1;
  transform: translateX(0) scaleY(1);
}

.list-leave-active {
  position: absolute;
}

.list-leave-to {
  opacity: 0;
  transform: scaleY(0);
  transform-origin: center top;
}


</style>