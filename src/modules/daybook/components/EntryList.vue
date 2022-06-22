<template>
  <div class="entry-list-container ">
    <div class="px-2 pt2">
      <input type="text"
      class="form-control"
      placeholder="Buscar entrada">
    </div>
  </div>

  <div class="entry-scrollarea">
    <entry-y
    v-for="item in 100" :key="item"/>
  </div>
</template>

<script>
import  {defineAsyncComponent} from 'vue'
export default {
  components:{
    EntryY: defineAsyncComponent(() => import('./EntryY.vue'))
  }

}
</script>

<style lang="scss" scoped>

.entry-list-container{
  border-right: 1px solid #2c3e50;
  height: calc( 23vh - 120px );
}

.entry-scrollarea{
  height: calc( 100vh - 110px );
  overflow: scroll;
}
</style>