<template>
  <div class="sidebar-container">
    <ul class="sidebar-links">
      <li v-for="(item, i) in sidebarItems" :key="i">
        <SidebarGroup
            v-if="item.type === 'group'"
            :item="item"
            :first="i === 0"
            :open="i === openGroupIndex"
            :collapsable="item.collapsable || item.collapsible"
            @toggle="toggleGroup(i)"
          />
      </li>
    </ul>
  </div>
</template>

<script>
import { isActive, resolveSidebarItems } from './util'
import SidebarGroup from './SidebarGroup.vue'

export default {
  components: { SidebarGroup },
  data () {
    return {
      openGroupIndex: 0
    }
  },
  computed: {
    sidebarItems: function() {
      return resolveSidebarItems(
        this.$page,
        this.$page.regularPath,
        this.$site,
        this.$localePath
      );
    }
  },

  created () {
    this.refreshIndex()
  },
  watch: {
    '$route' () {
      this.refreshIndex()
    }
  },
  methods: {
    refreshIndex () {
      const index = resolveOpenGroupIndex(
        this.$route,
        this.sidebarItems
      )
      if (index > -1) {
        this.openGroupIndex = index
      }
    },
    toggleGroup (index) {
      this.openGroupIndex = index === this.openGroupIndex ? -1 : index
    },
    isActive (page) {
      return isActive(this.$route, page.regularPath)
    }
  }
}

function resolveOpenGroupIndex (route, items) {
  for (let i = 0; i < items.length; i++) {
    const item = items[i]
    if (item.type === 'group' && item.children.some(c => isActive(route, c.path))) {
      return i
    }
  }
  return -1
}
</script>

<style scoped>
.sidebar-container {
  position: fixed;
  overflow: auto;
  -webkit-overflow-scrolling: touch;
  background-color: rgba(255,255,255,1);
  font-size: 0.9rem;
  padding: 1rem 1.4rem;
  z-index: 30;
  transition: all 400ms;
}
@media screen and (min-width: 752px) {
  .sidebar-container {
    top: 0;
    bottom: 0;
    right: 0;
    min-width: 300px;
    box-shadow: 0px 5px 30px 0px rgba(0,0,0,0.2);
  }
}
@media screen and (max-width: 751px) {
  .sidebar-container {
    top: 0;
    bottom: 0;
    right: 0;
    width: 65%;
    box-shadow: 0px 5px 30px 0px rgba(0,0,0,0.2);
  }
}
</style>
