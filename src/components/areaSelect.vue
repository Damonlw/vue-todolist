<template>
  <div class="area-select">
      <select v-model="onProvince">
          <option v-for="item in items">{{item.name}}</option>
      </select>
      <select v-model="onCity">
          <option  v-for="city in selectionCity">{{city.name}}</option>
      </select>
      <select v-model="onArea">
          <option v-for="area in selectionArea">{{area}}</option>
      </select>
  </div>
</template>

<script>
export default {
  name: 'area-select',
  data () {
    return {
        onProvince: '福建省',
        onCity: '',
        onArea: '',
        items:[
            { 'name': '福建省', 'city':[{'name':'福州市', 'area':['鼓楼区','台江区','仓山区','马尾区','晋安区']},
                                     {'name':'龙岩市', 'area':['新罗区','永定区']},
                                     {'name':'漳州市', 'area':['芗城区','龙文区']},
                                     {'name':'厦门市', 'area':['同安区','翔安区','集美区','海沧区','湖里区','思明区']}]},
            { 'name': '广东省', 'city':[{'name':'广州市', 'area':['越秀区','海珠区','荔湾区','天河区','白云区']},
                                     {'name':'深圳市', 'area':['罗湖区','福田区','南山区','盐田区','宝安区']}]}
        ]
    }
  },
  computed:{
      selectionCity: function(){
          this.selectionCity = []
          for (let province of this.items) {
              if (this.onProvince === province.name) {
                  this.onCity = province.city[0].name
                  return province.city
              }
          }
      },
      selectionArea: function(){
          this.selectionArea = []
          if (this.selectionCity) {
              for (let city of this.selectionCity) {
                  if (this.onCity === city.name) {
                      this.onArea = city.area[0]
                      return city.area
                  }
              }
          }
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.area-select{
    width: 200px;
    margin: 7px auto;
}
</style>
