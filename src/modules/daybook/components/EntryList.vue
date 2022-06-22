<template>
  <div class="entry-list-container">
    <div class="px-2 pt2">
      <input 
      type="text" 
      class="form-control" 
      placeholder="Buscar entrada" 
      v-model="term"      
      />
    </div>
  </div>

  <div class="entry-scrollarea">
    <entry-y 
    v-for="entry in entriesByTerm" 
    :key="entry.id" 
    :entry=entry
    />
  </div>
</template>

<script>
import { defineAsyncComponent } from "vue";
import { mapGetters } from 'vuex'

export default {
  components: {
    EntryY: defineAsyncComponent(() => import("./EntryY.vue")),
  },
  computed:{
     ...mapGetters('journal',[
      'getEntriesByTerm'
    ]),
    entriesByTerm(){
      return this.getEntriesByTerm(this.term)
    }
  },
  data(){
    return{
      term:'',
    }

  }
};
</script>

<style lang="scss" scoped>
.entry-list-container {
  border-right: 1px solid #2c3e50;
  height: calc(23vh - 120px);
}

.entry-scrollarea {
  height: calc(100vh - 110px);
  overflow: scroll;
}
</style>
