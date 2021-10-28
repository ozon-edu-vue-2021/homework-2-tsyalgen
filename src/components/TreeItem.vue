<template>
  <div>
    <li>
      <div
          :class="isFolder ? 'bold' : isLink ? 'link' : ''"
          @click="click">
        {{ data.name }}
        <span v-if="isFolder">[{{ isOpen ? '-' : '+' }}]</span>
      </div>
      <ul v-if="isOpen">
        <TreeItem
            v-for="(root, index) in data.contents"
            :key="index"
            :data="root"
        ></TreeItem>
      </ul>
    </li>
  </div>
</template>

<script>

export default {
  name: 'TreeItem',
  props: {
    data: {
      required: true,
      default: () => {}
    }
  },
  data() {
    return {
      isOpen: false
    };
  },
  computed: {
    isFolder() {
      return this.data.contents && this.data.contents.length;
    },
    isLink() {
      return this.data.type === 'link'
    }
  },
  methods: {
    click() {
      if (this.isFolder) {
        this.isOpen = !this.isOpen;
      } else {
        document.querySelectorAll('.selected').forEach(el =>{
          el.classList.remove('selected')
        })
        this.$el.classList.add('selected')
      }
    }
  },
}
</script>

<style scoped>
li{
  list-style: none;
}
.bold{
  font-weight: bold;
}
.link{
  font-style: italic;
}
.selected{
  text-decoration: underline;
}
</style>
