<template>
<div class="warpper">
  <div class="wrapper-comtent">
    <section>
      <div class="container">



        <!--first modelka-->
        <button class="btn btnPrimary" @click="modalFirst = !modalFirst">Show first modal</button>
        <modals
        title="First modal"
        v-show="modalFirst"
        @close="modalFirst = false"
        >

        <div slot="body">
          <p>Text Text Text Text</p>
          <button class="btn btnPrimary" @click="modalFirst = !modalFirst">Well Done!</button>
        </div>
        </modals>








        <!--second modelka-->


        <button class="btn btnPrimary" @click="modalSecond.show = !modalSecond.show">Show modal with form</button>
        <modals
        title="Modal with form"
        v-show="modalSecond.show"
        @close="modalSecond.show = false"
        >


      <!--BODY-->
        <div slot="body">
          <form @submit.prevent="submitSecondForm">
            <label>Name:</label>
            <input type="text" required v-model="modalSecond.name"> 
            <label>Email:</label>
            <input type="email" required v-model="modalSecond.email"> 
            <button class="btn btnPrimary">Submit!</button>
          </form>
        </div>
        </modals>


      </div>
    </section>
  

  </div>
</div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default{
  Comments:{modals},
  data (){
    return{
      modalFirst: false,
      modalSecond:{
        show: false, 
        name: '',
        email:''
      }
    }
  },
  methods:{
    submitSecondForm () {
      console.log({
        name: this.modalSecond.name,
        email: this.modalSecond.email
      })
      this.modalSecond.name = ''
      this.modalSecond.email = ''
      this.modalSecond.show = false

    }
  } 
}



export default {
  name: 'Home',
  components: {
    HelloWorld
  }
}
</script>
