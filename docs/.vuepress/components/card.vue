<template>
    <div class="card">
        <div v-if="card.title" class="card__title">
            <span>{{ card.title }}</span>
        </div>
        <div v-if="card.attr" class="card__attr">
            <div v-for="( item, index ) in card.attr" :key="index" class="attr">
                <div class="attr__name">
                    {{ item.name }}
                </div>
                <div class="attr__content">
                    {{ item.content }}
                </div>
            </div>
        </div>

        <div class="card__property">
            <div v-for="( item, index ) in card.property" :key="index" class="property">
                <div class="property__name">
                    <i> {{ '&lt;' + item.name + '&gt;' }}</i>
                </div>
                <div class="property__content">
                    {{ item.content }}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        chapter: {
            type: String,
            default: () => { return {} }
        },
        property: {
            type: String,
            default: ''
        }
    },
    data() {
        return {
            card: {}
        }
    },
    created() {
        let card = ()=>{}
        if (this.chapter === 'chapter2') {
            card = () => Promise.resolve(require('../../comConfig/chapter2'))
        }
        card().then( _ => {
            this.card = _[this.property]
        })
    },
}
</script>

<style scoped>
.card {
  width: 100%;
  margin: 0 auto;
  border: 1px solid green;
  padding: 20px 50px;
}
.card__title {
  text-align: center;
  font-weight: bolder;
  font-size: 28px;
  margin-bottom: 30px;
}
.card__attr {
  margin-bottom: 30px;
}
.card__attr .attr {
  display: flex;
}
.card__attr .attr__name {
  width: 200px;
  font-weight: bolder;
  font-size: 17px;
  line-height: 30px;
}
.card__attr .attr__content {
  width: 1000px;
  line-height: 30px;
}
.card__property .property__name {
  margin: 20px 0 0 0;
}
.card__property .property__content {
  margin-left: 50px;
  line-height: 25px;
  word-break: keep-all;
}

</style>