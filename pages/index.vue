<template>
  <div>
    <div v-for="data in datas">
      <span v-if="data" v-html="data.content"></span>
    </div>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      datas: [],
    };
  },
  created() {
    this.loaddata();
  },
  methods: {
    loaddata() {
      try {
        this.$axios
          .$get(
            "@apostrophecms/page/cl5gokd0x0004hneud4t8c2he:en:published?apikey=myapikey1029384756"
          )
          .then((res) => {
            if ("main" in res) {
              this.datas = res.main.items;
            }
            console.log(this.datas);
          });
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
