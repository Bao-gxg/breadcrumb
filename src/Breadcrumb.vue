<template>
  <nav class="breadcrumb is-small has-succeeds-separator" aria-label="breadcrumbs" v-if="list.length">
    <ul>
      <router-link tag="li" v-for="(crumb, key) in list" :to="crumb.path" :key="key" aria-current="page" exact>
        <a>{{ showName(crumb) }}</a>
      </router-link>
    </ul>
  </nav>
</template>

<script>
export default {

  props: {
    list: {
      type: Array,
      required: true,
      default: () => [],
    },
  },

  methods: {
    isLast(index) {
      return index === this.list.length - 1;
    },

    showName(item) {
      return (item.meta && item.meta.label) || item.name;
    },
  },
};
</script>

