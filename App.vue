<template>
  <div>
    <div class="main-container">
      <ToEncryp
              v-bind:info="info"
              v-on:change_text="change_text"
      />

      <ToDecryp
              v-bind:encr_txt="encr_txt"
      />
    </div>
    <div class="buttons">
        <button class="btn btn-success" v-on:click="decryptxt">Расшифровать</button>
        <button class="btn btn-primary" v-on:click="copytxt">Скопировать</button>
        <button class="btn btn-danger" v-on:click="cleantxt">Очистить</button>
    </div>
  </div>
</template>

<script>
  import ToEncryp from './components/ToEncryp.vue'
  import ToDecryp from './components/ToDecryp.vue'

export default {
  name: 'app',
  components: {
    ToEncryp, ToDecryp
  },
  data(){
    return{
      info:'',
      encr_txt:''
    }
  },

  methods:{
    change_text(text){
      let result='';
       for(let i=0; i<text.length; i++){
         let num = text[i].charCodeAt(0);
         num+=3;
         result+=String.fromCharCode(num);
       }
      this.encr_txt = result;
    },

    decryptxt(){
      let text = document.querySelector('.main-area').value;
      let result='';
      for(let i=0; i<text.length; i++){
        let num = text[i].charCodeAt(0);
        num-=3;
        result+=String.fromCharCode(num);
      }
      this.encr_txt = result;
    },

    copytxt(){
      let t = document.querySelector('.decryp-area');
      t.select();
      document.execCommand('copy');
    },

     cleantxt() {
         document.querySelector('.main-area').value='';
         this.encr_txt = '';
     }
  }
}
</script>

<style>
  .main-container{
    display: flex;
  }
 .buttons{
   display: flex;
   align-items: baseline;
   padding: 0 10px;
 }
 .btn{
     margin-right: 10px;
 }
  @media screen and (max-width: 980px){
      .main-container{
          flex-direction: column;
      }
      .word-part{
          width:94%;
          margin: 10px auto;
          height: 40vh;
          min-height: 40vh;
      }

      .buttons{
          width:94%;
          justify-content: center;
          margin: 10px auto;
          padding: 0;
      }

      .decryp-area{
          height: 40vh;
      }
  }
</style>
