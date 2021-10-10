<template>
  <div class="filter">
    <div class="item" @click="filter('')">
      All
    </div>
    <div class="item alive" @click="filter('Alive')">
      Alive
    </div>
    <div class="item dead" @click="filter('Dead')">
      Dead
    </div>
    <div class="item unknown" @click="filter('unknown')">
      Unknown
    </div>
  </div>
</template>

<script>
import { useStore } from 'vuex'
export default {
  setup(){
    const store = useStore();
    
    const filter = ((status) => {
      store.dispatch('filterByStatus', status);
    });

    return { 
      filter
    }
  }
}
</script>

<style lang="scss">
.filter {
  width: 400px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  border-radius: 10px;
  overflow: hidden;
  .item {
    padding: 1rem 0.5rem;
    background-color: var(--background-card);
    text-align: center;
    cursor: pointer;
    &:hover {
      color: var(--text-orange);
    }
  }
  .alive {
    &:hover {
      color: var(--text-green);
    }
  }
  .dead {
    &:hover {
      color: var(--text-red);
    }
  }
  .unknown {
    &:hover {
      color: var(--text-gray);
    }
  }
}
</style>