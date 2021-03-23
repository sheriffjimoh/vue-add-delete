<template>
        <div id="app">
          <!-- using v-html directive to  render html tag -->
          <!-- using v-if v-else v-else-if directive for a decision making -->
          <!-- using v-show directive  display element on a check for a small amount of data-->
          <!-- using v-text directive use to display text/content -->
          <!-- using v-once directiive to run code once -->
          <!-- using v-for directive for looping  (hero,index)  (value,key) -->
          <!-- using v-bind directive to bind values -->
          <!-- using v-model directive  v-model.trim v-model.lazy -->
          <!-- using v-on/@click directive for an event handler  -->
         
           <div class="datas">
             <h1>DC Heros</h1>

              <ul v-for="(hero, index) in Dcheros "  :key="index">
              <li> <span class="span"> {{hero.name}} </span>   <button v-on:click="removehero(index)">x</button></li>
            
            
              </ul>
            
              <form @submit.prevent="addHero">
                  <input type="text"   v-model.lazy="newHero" placeholder="Type hero name here">
                  <button  type="submit">Add Hero</button>
              </form>
           </div>
       </div>
</template>

<script>

export default {


  methods:{

    addHero(){
    if(this.newHero !==" "){
    this.Dcheros.unshift({ name:this.newHero});
    this.newHero =" ";
    }

    },

    removehero(index){
    if(this.Dcheros.length > 1){

     this.Dcheros = this.Dcheros.filter((hero, i) => i !==index);
    
    }else{
      alert('add new hero');
    }
   
    }

  


  
  },


  data(){
  
    return{
  
      newHero:" ",
      Dcheros:[
       { name:'Superman', age:30},
       { name:'Batman',age:20},
       {name:'Ironman',age:29},
        {name:'Flash',age:30}, 
      ]
       
    };
  }

  // data(){
  //   return{
  //     msg: '<h1> the is a message</h1>',
  //     isShowing:true,
  //     count:0, 
  //   };
  // },

  // mounted(){
  //   setInterval(() => {
  //     this.count++;
  //   }, 1000);
  // },
}
</script>

<style>

  *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body{
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }


  #app{

    padding-top: 5rem;
    
  }

  .datas{
    background-color: aquamarine;
    padding: 40px;
  }
  

  .datas h1{
    text-align: center;
    padding: 10px;
  }
  ul {
    list-style-type:none;
    padding:10px;
  }

  ul li{
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
    font-size: 20px;
  }

  ul li button{
    float: right;
    padding:7px;
    font-size: 17px;

    background-color: rgb(167, 6, 6);  
    color: cornsilk;
    border: none;

  }

  form{
    padding-top:30px;
  }


  form input{
    padding: 9px;
    border: none;
  }

  form button {
    padding: 9px;
    border: none;
  }

 .span{
   text-transform: capitalize;
 }

</style>
