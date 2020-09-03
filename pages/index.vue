<template>
 <div id="app">
   
  
    <button type="button" @click="shuffle">Shuffle</button>
    <button type="button" @click="move">Move</button>
  <transition-group tag="div" name="list">
   
   <!-- <p v-for="(item,index) in list" :key="item.cla">{{item.cla}}</p> :class="item.cla"-->
   
    <component v-for="(item,index) in list" :is="item.comp" :class="item.cla" :style="styles" :key="item.cla" width=100 height=100>
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
    {comp:SampleSvg1,cla:"svg1"},
    {comp:SampleSvg2,cla:"svg2"},
    {comp:SampleSvg3,cla:"svg3"},
    {comp:SampleSvg4,cla:"svg4"},
    {comp:SampleSvg5,cla:"svg5"},
    {comp:SampleSvg6,cla:"svg6"}
    ],
      styles:{
       '--top1': '200px',
       '--top2': '350px',
       '--top3': '500px',
       '--top4': '200px',
       '--top5': '350px',
       '--top6': '500px',
       '--left1': '200px',
      '--left2': '200px',
       '--left3': '200px',
       '--left4': '350px',
       '--left5': '350px',
       '--left6': '350px'
      },
      toplist:[
         '200px',
         '350px',
         '500px',
         '200px',
         '350px',
         '500px'
      ],
      leftlist:[
         '200px',
         '200px',
         '200px',
         '350px',
         '350px',
         '350px'
      ], 
    

    }
  },
 computed:{
  /*  styles:function(){
      return{
      '--top': '300px',
      '--left': '300px' }
      },
  */

 },

    

  methods:{
    random:function(max){
      return Math.floor(Math.random() * (max + 1))
    },
    
    shuffle:function(){
     
      for(let i = this.toplist.length-1 ; i > 0; i--){
    let r = Math.floor(Math.random() * (i + 1));
    let tmptop = this.toplist[i];
    let tmpleft = this.leftlist[i];
    this.toplist[i]= this.toplist[r];
    this.leftlist[i]= this.leftlist[r];
    this.toplist[r] = tmptop;
    this.leftlist[r] = tmpleft;
    }
    let s=0;
    for(let key in this.styles){
    if (s<6){
    this.styles[key]=this.toplist[s]
    } else {
    this.styles[key]=this.leftlist[s-6]
    }
    s++;
    }
    },
    

  move:function(){
      this.styles={'--top1': '400px','--top2': '600px','--top3': '0px',
      '--left2': '400px' }
      console.log(this.styles['--top1']);
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
   top: var(--top1);
   left: var(--left1);
}
.svg2{
   
   position: absolute;
   top: var(--top2);
   left: var(--left2);
}
.svg3{
   
   position: absolute;
   top: var(--top3);
   left: var(--left3);
}
.svg4{
   
   position: absolute;
   top: var(--top4);
   left: var(--left4);
}
.svg5{
   
   position: absolute;
   top: var(--top5);
   left: var(--left5);
}
.svg6{
   
   position: absolute;
   top: var(--top6);
   left: var(--left6);
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