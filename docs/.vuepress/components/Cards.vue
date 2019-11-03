<template>
  <div class="card">
    <div v-if="card.title" class="card__title">
      <span>{{ card.title }}</span>
    </div>

    <div v-if="card.attr" class="card__attr">
      <div v-for="( item, index ) in card.attr" :key="index" class="attr">
        <div class="attr__name">{{ item.name }}</div>
        <div class="attr__content">{{ item.content }}</div>
      </div>
    </div>

    <div class="card__property">
      <div v-for="( item, index ) in card.property" :key="index" class="property">
        <div class="property__name">
          <i>{{ '&lt;' + item.name + '&gt;' }}</i>
        </div>
        <div class="property__content">{{ item.content }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  props: ["cards"],
  data() {
    return {
      card: {}
    };
  },
  created() {
    this.getData("./cards/" + this.cards + ".json");
  },
  methods: {
    getData(url) {
      axios
        .get(url)
        .then(resp => {
          if (resp) {
            console.log(resp.data);
            this.card = resp.data;
          }
        })
        .catch(e => {
          this.card = { title: "cannot load json" };
        });
    }
  }
};
</script>

<style scoped>
.card {
  margin-top: 0.85rem;
  margin-bottom: 0.85rem;
  border-radius: 6px;
  border: 2px solid #3eaf7c;
  padding: 20px 50px;
}
.card__title {
  text-align: center;
  font-weight: bolder;
  font-size: 28px;
  margin-bottom: 30px;
}
.card__attr {
  display: flex;
  flex-direction: column;
  margin-bottom: 30px;
}
.card__attr .attr {
  display: inline-flex;
}
.card__attr .attr__name {
  width: 24%;
  font-weight: bolder;
  font-size: 17px;
  line-height: 30px;
}
.card__attr .attr__content {
  width: 76%;
  line-height: 30px;
}
.card__property .property__name {
  margin-top: 20px;
}
.card__property .property__content {
  margin-left: 50px;
  line-height: 25px;
  word-break: keep-all;
}
</style>