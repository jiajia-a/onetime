<template>
  <div>
	<input class="one" type="text" placeholder="请输入..." v-model="search"/>
  <button @click="onsearch">搜索</button>
	<table>
		<tr v-for="item in searchData" :key="item">
			<td>{{item.name}}</td>
			<td>{{item.status}}</td>
		</tr>
	</table>

  <ul>
    <li>{{searchText}}</li>
  </ul>
</div>

</template>

<script>

export default {
  data: function () {
    return {
      search: '',
      result:'',//搜索的结果
      products: [
        {name: '大娃', status: '力大无穷'},
        {name: '二娃', status: '千里眼顺风耳'},
        {name: '三娃', status: '刀枪不入'},
      ]
    }
  },
  computed: {
    searchData: function () {
      var search = this.search
      if (search) {
        return this.products.filter(product => {
          return Object.keys(product).some(key =>{
            return String(product[key]).indexOf(search) > -1
          })
        })
      }
      return this.products
    }
  },
  methods: {
    onsearch(value){
      if(!value){
        return false
      }else{
        
      }
    }
  },
}

</script>
