<template>
  <div id="app">
     <nav id="navBar" class="navbar navbar-expand-sm navbar-light fixed-top">
        <i class="fas fa-audio-description fa-3x mx-3"></i>
        <a class="navbar-brand" href="/">
            Vue購物車
        </a>
        <button class="navbar-toggler d-lg-none" type="button" data-toggle="collapse" data-target="#collapsibleNavId"
            aria-controls="collapsibleNavId" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="collapsibleNavId">
            <ul class="navbar-nav ml-auto">
                <li class="nav-item">
                     <button v-on:click.prevent="clickMe($event)" class="btn btn-primary"  type="click">
                        購物車
                    </button>
                </li>
            </ul>
        </div>
    </nav>
    <Header />
    <!-- productSection -->
    <Product :isClickCart="isClickCartBtn" @closeBtn="closeModal" />
        <keep-alive>
            <router-view/>
        </keep-alive>
  </div>
</template>

<script>
import Product from '@/components/Product'
import Header from '@/components/Header'
import Modal from '@/components/Modal'
export default {
  name: 'App',
  data () {
    return {
      isClickCartBtn: false
    }
  },
  components: {
    Product,
    Header,
    Modal
  },
  methods: {
    clickMe () {
      console.log('click')
      this.isClickCartBtn = true
    },
    closeModal () {
      this.isClickCartBtn = false
    }
  }
}

</script>

<style lang="scss">
body {
  margin: 0;
  padding-top:56px;
}

.navbar {
  box-shadow: 0px 5px 10px rgba(0, 0, 0, .2);
  background:  rgba(170, 100, 9, 0.904);
  z-index: 99;
}

#navLinkItem {
    position: relative;
}

@import "~bootstrap/scss/bootstrap";

</style>
