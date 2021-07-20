<template>
    <form v-on:submit.prevent="submitme" >
       <h5 class="card-title">
           {{item.title}}
       </h5>
       <p class="card-text">
           商品價格: ${{item.price}}
       </p>
       <div class="form-group">
           <label>購買數量</label>
           <input id="amountInput${product.id}" class="form-control" type="number" min="1" max="20" required>
       </div>
       <div class="form-group">
           <button class="btn btn-primary" type="submit">
               加入購物車
           </button>
       </div>
    </form>
</template>
<script>
export default {
  data: function () {
    return {
      productList: [
        {
          id: '1',
          title: 'Edifier A100',
          price: 18900,
          img: 'https://picsum.photos/id/999/1200/600'
        },
        {
          id: '2',
          title: 'Edifier A200',
          price: 24900,
          img: 'https://picsum.photos/id/999/1200/600'
        }
      ]
    }
  },
  methods: {
    submitme () {
      // console.log('近來嚕~~')
      console.log('近來嚕~~')
    }
  }
}
</script>
