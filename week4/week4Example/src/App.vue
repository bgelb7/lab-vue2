<script>
import Cart1 from './components/Cart1.vue'

import Footerbar from './components/Footerbar.vue'
import Navbar from './components/Navbar.vue'



export default {
  name: 'App',
  components: {
    Cart1,
    Navbar,
    Footerbar,

  },
  data() {
    return {


    }

  },


}
</script>


<template>
  <div id="app">
    <Navbar />
    <Cart1 />
    <Footerbar />
  </div>
  <!--
    <ul>
      <li>
        {{ items[0].name }}
      </li>
      <li>
        {{ items[1].name }}
      </li>
      <li>
        {{ items[2].name }}
      </li>
      <li>
        {{ items[3].name }}
      </li>
      <li>
        {{ items[4].name }}
      </li>
      <li>
        {{ items[5].name }}
      </li>
      <li>
        {{ items[6].name }}
      </li>
      <li>
        {{ items[7].name }}
      </li>
      <li>
        {{ items[8].name }}
      </li>
      <li>
        {{ items[9].name }}
      </li>
    </ul>
  </div>-->
</template>


<style>

</style>


