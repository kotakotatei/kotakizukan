<template>
  <ul class="list">
    <li class="list__item">
      <p class="catch">キャッチ</p>
      <div class="name">
        <h2 class="name__main">なまえ</h2>
        <p class="name__sub">英名</p>
      </div>
      <accordion>
        <div class="inner" slot="body">
          <img class="image" src="../assets/images/item/1.jpg" alt="なまえ">
          <dl class="info">
            <dt class="info__title">平均寿命または時代（地質時代）</dt>
            <dd class="info__text">紹介テキスト紹介テキスト</dd>
          </dl>
          <dl class="info">
            <dt class="info__title">こたきコメント</dt>
            <dd class="info__text">紹介テキスト紹介テキスト</dd>
          </dl>
        </div>
      </accordion>
    </li>
  </ul>
</template>

<script>
import accordion from '../components/accordion'

export default {
  name: 'creatureList',
  components: {
    accordion
  },
  data () {
    return {
      creature: [
        {
          id: 1,
          category: 'contemporary',
          name: 'クサガメ',
          engName: 'Chinese pond turtle',
          copy: '飼いやすさNo.1',
          life: '20年～40年',
          comment: ''
        },
        {
          id: 2,
          category: 'contemporary',
          name: 'ヘルマンリクガメ',
          engName: "Herman's tortoise",
          copy: '癒やしのかたまり',
          life: '30年～50年',
          comment: ''
        },
        {
          id: 3,
          category: 'contemporary',
          name: 'アカハライモリ',
          engName: 'Japanese fire belly newt',
          copy: 'エサも扱いやすくて手軽',
          life: '10年以上',
          comment: ''
        },
        {
          id: 4,
          category: 'contemporary',
          name: 'ミナミイボイモリ',
          engName: 'Emperor newt',
          copy: 'かわいすぎない？',
          life: '10～20年',
          comment: ''
        },
        {
          id: 5,
          category: 'contemporary',
          name: 'フトアゴヒゲトカゲ',
          engName: 'Central bearded dragon',
          copy: '現代の小さな草食恐竜',
          life: '6～8年',
          comment: ''
        },
        {
          id: 6,
          category: 'contemporary',
          name: 'イエアメガエル',
          engName: "White's tree frog",
          copy: 'でもカエルもかわいいよね',
          life: '15～20年',
          comment: ''
        },
        {
          id: 7,
          category: 'contemporary',
          name: 'ヒョウモントカゲモドキ',
          engName: 'Common leopard gecko',
          copy: '爬虫類界のアイドル',
          life: '10年',
          comment: ''
        },
        {
          id: 8,
          category: 'contemporary',
          name: 'ボールニシキヘビ',
          engName: 'Ball python',
          copy: 'こたきが飼いたいランキング1位',
          life: '15～20年',
          comment: ''
        },
        {
          id: 9,
          category: 'contemporary',
          name: 'コーンスネーク',
          engName: 'Corn snake',
          copy: '小さくて飼いやすそう',
          life: '10～15年',
          comment: ''
        },
        { 
          id: 10,
          category: 'ancient',
          name: 'アノマロカリス',
          engName: 'Anomalocaris canadensis（カナダ産のアノマロカリス）',
          copy: 'カンブリアモンスター界のアイドル！',
          life: '約5億2,500万～約5億0,500万年前（古生代カンブリア紀前期終盤～中期）',
          comment: '好物はやわらかい三葉虫。古生物が好きな方はもちろん、そうでない方も知ってる方の多いカンブリアモンスター界のアイドル！この時代ではかなり大きい方のいきもの（約1m）！プール付きの豪邸じゃないと飼えないか…'
         },
        { 
          id: 11,
          category: 'ancient',
          name: 'オパビニア',
          engName: 'Opabinia regalis',
          copy: 'オフィスに常駐（ぬいぐるみ）',
          life: '約5億500万年前（古生代カンブリア紀中期後半）',
          comment: ''
         },
        { 
          id: 12,
          category: 'ancient',
          name: 'ハルキゲニア',
          engName: 'Hallucigenia',
          copy: '想像図が不安定すぎる',
          life: '約5億2,500万- 約5億0,500万年前（古生代カンブリア紀前期中盤）',
          comment: ''
         },
        { 
          id: 13,
          category: 'ancient',
          name: 'ミクロラプトル',
          engName: 'Microraptor',
          copy: 'めっちゃファンタジー',
          life: '1億2800万～1億2600万年前（白亜紀前期）',
          comment: ''
         },
      ]
    }
  }
}
</script>

<style src="../assets/scss/list.scss" lang="scss" scoped></style>
