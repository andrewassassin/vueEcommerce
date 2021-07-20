<template>
<div id="Product">
  <section id="productSection " class="py-5">
    <div class="container">
      <h2 class="text-center mb-4 list-joy">產品列表</h2>
        <div class="row justify-content-center">
          <div v-for="item in productList" class="col-md-6" :key="item.key">
            <div class="card my-5 mx-5">
              <img :src="`${item.img}`" class="card-img-top">
              <form :id="`${item.id}`" v-on:submit.prevent="submitme($event)" class="mt-3 card-body">
                <h5 class="card-title" >
                    {{item.title}}
                </h5>
                <p class="card-text">
                    商品價格: ${{item.price}}
                </p>
                <div class="form-group">
                    <label>購買數量</label>
                    <input :id="`amount${item.id}`" class="form-control" type="number" min="1" max="20" required>
                </div>
                <div class="form-group">
                    <button class="btn btn-primary"  type="submit">
                        加入購物車
                    </button>
                </div>
              </form>
            </div>
          </div>
        </div>
    </div>
  </section>
   <Modal v-if="isClickCart === true" :itemList="itemList" @closeBtn="closeModal" @clearItemList="clearItem" />
</div>
</template>

<script>
// import $ from 'jquery'
import Modal from '@/components/Modal'
export default {
  name: 'Product',
  components: {
    Modal
  },
  data: function () {
    return {
      productList: [
        {
          id: '1',
          title: 'Edifier A100',
          price: 18900,
          img: '../static/img/001.jpg'
        },
        {
          id: '2',
          title: 'Edifier A200',
          price: 24900,
          img: '../static/img/002.jpg'
        },
        {
          id: '3',
          title: 'Klipsch The Sixes',
          price: 18900,
          img: '../static/img/003.jpg'
        },
        {
          id: '4',
          title: 'Edifier S350DB',
          price: 8500,
          img: '../static/img/004.jpg'
        }
      ],
      cart: '',
      itemList: []
    }
  },
  props: {
    isClickCart: Boolean
  },
  methods: {
    submitme (event) {
      const targetId = event.currentTarget.id
      let amount = event.target[0].value
      amount = parseInt(amount)
      const product = this.productList.find(product => {
        // 找到產品的id == pid 的資料
        return product.id === targetId
      })

      const item = {
        ...product,
        amount
      }
      this.itemList.push(item)
    },
    clearItem (value) {
      // this.itemList = []
      this.itemList = value
    },
    closeModal () {
      this.$emit('closeBtn')
    }
  }
}
</script>
