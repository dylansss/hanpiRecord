<template>
  <div>
    <div v-if="tab === 2">
      <div v-for="item in list" :key="item">
        <img @click="changeFold(item)" />
        <div v-if="!item.fold" :ref="item.id" style="display: none">
          <div v-for="p in item.children" :key="p.id"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list: [],
    };
  },
  method: {
    changeFold(item) {
      item.isFold = !item.isFold;
      this.$refs[item.id][0].style.display = "block";

      const tar = list.findIndex((i) => i.id === item.id);
      list[tar].isFold = !i.isFold;
    },
  },
};
</script>
