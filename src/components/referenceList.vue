<template>
  <dl class="list">
    <dt class="list__title">参考にさせていただきました</dt>
    <dd class="list__item" 
    v-for="(list, index) in reference" v-bind:key="index">
    <a class="link" v-bind:href="list.url" target="_blank">{{ list.title }}</a>
    </dd>
  </dl>
</template>

<script>

export default {
  name: 'referenceList',
  data () {
    return {
      reference: [
        {
          title: '基礎から学ぶ Vue.js',
          url: 'https://cr-vue.mio3io.com/',
        },
        {
          title: '古生物のサイズが実感できる！ リアルサイズ古生物図鑑　古生代編',
          url: 'https://gihyo.jp/book/2018/978-4-7741-9913-9',
        },
        {
          title: 'わけあって絶滅しました。世界一おもしろい絶滅したいきもの図鑑',
          url: 'https://www.diamond.co.jp/book/9784478104200.html',
        },
        {
          title: 'Newton別冊 「生命」とは何かいかに進化してきたのか―最初の生命から哺乳類まで（絶版？）',
          url: 'https://www.newtonpress.co.jp/separate/back_biology.html',
        },
        {
          title: 'ペットナビ',
          url: 'https://petraku.com/',
        },
        {
          title: 'Pet Pedia',
          url: 'https://petpedia.net/',
        },
        {
          title: 'Wikipedia',
          url: 'https://ja.wikipedia.org/wiki/%E3%83%A1%E3%82%A4%E3%83%B3%E3%83%9A%E3%83%BC%E3%82%B8',
        },
      ]
    }
  },
}
</script>

<style src="../assets/scss/reference.scss" lang="scss" scoped></style>
