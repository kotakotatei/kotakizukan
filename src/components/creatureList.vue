<template>
  <transition-group tag="ul" class="list" name="list" mode="out-in">
    <li class="list__item" 
    v-for="(list, index) in creature" v-bind:key="index" 
    v-if="list.category == currentCategory">
      <p class="copy">{{ list.copy }}</p>
      <div class="name">
        <h2 class="name__main">{{ list.name }}</h2>
        <p class="name__sub">{{ list.engName }}</p>
      </div>
      <accordion>
        <div class="inner" slot="body">
          <img class="image" v-bind:src="getImg(index)" v-bind:alt="list.name">
          <dl class="info">
            <dt class="info__title" v-if="list.category == 'contemporary'">平均寿命</dt>
            <dt class="info__title" v-if="list.category == 'ancient'">生きていた時代（地質時代）</dt>
            <dd class="info__text">{{ list.life }}</dd>
          </dl>
          <dl class="info">
            <dt class="info__title">こたきコメント</dt>
            <dd class="info__text">{{ list.comment }}</dd>
          </dl>
        </div>
      </accordion>
    </li>
  </transition-group>
</template>

<script>
import accordion from '../components/accordion'

export default {
  name: 'creatureList',
  components: {
    accordion
  },
  props: ['currentCategory'],
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
          comment: `かわいい500円玉サイズから4年くらいで20cm以上まで成長…！
          するので、大きくなったときの飼育場所は考えておいたほうがよいね。
          でもすごく強くて飼いやすいので、幼少期だけ気をつけてあげればベランダで飼って氷が張っちゃっても元気でした。
          こたきの実家のクサガメは弟と同い年でピチピチの22歳。`
        },
        {
          id: 2,
          category: 'contemporary',
          name: 'ヘルマンリクガメ',
          engName: "Herman's tortoise",
          copy: '癒やしのかたまり',
          life: '30年～50年',
          comment: `このまったり感がかわいい…！
          大きさや飼いやすさから、リクガメのなかでは初心者向けらしいけど、
          温度管理とかの環境もエサも、クサガメよりは圧倒的に手がかかるし、
          寿命もとっても長いから結構覚悟がいりそう…！でもかわいい`
        },
        {
          id: 3,
          category: 'contemporary',
          name: 'ボールパイソン',
          engName: 'Ball python',
          copy: 'こたきが飼いたいランキング1位',
          life: '15～20年',
          comment: `和名ボールニシキヘビ。表題のとおり、一番飼いたい。
          ニシキヘビ独特のもっちりとしたからだ、ピット器官、つぶらな瞳…初めて触れたあの日に完全に虜になってしまった…！
          が、そのもっちりした体型がゆえに、同じ長さの別のヘビよりも圧倒的に体積が大きくて、
          そのぶん大きなケージもいるし、長い拒食があったり、初心者向けってちょいちょいネットで見かけるけど実は意外と初心者向けではないと思う…むむ…
          エサはマウスで、やっぱり細い体の種類のヘビよりも大きなものを食べるみたい。`
        },
        {
          id: 4,
          category: 'contemporary',
          name: 'コーンスネーク',
          engName: 'Corn snake',
          copy: '小さくて飼いやすそう',
          life: '10～15年',
          comment: `…ということがあり（ボールパイソン参照）もっと初心者向けのヘビはいないのか…
          と検索するとすぐに出てくるのがコーンスネーク。別名アカダイショウ。
          長さも2mいくのはまれだそうで、からだもシュッとスレンダーなので、
          体積が少なくてそのぶんケージも小さくてよさそう。性質や環境への順応性の高さから、最も飼いやすいヘビだそうです！
          エサはマウスで、私は昆虫よりマウスのが全然平気！飼える！！
          「やめて！遊びにいけなくなる（こた母）「イモリくらいにしときなよ（こた父）」」`
        },
        {
          id: 5,
          category: 'contemporary',
          name: 'アカハライモリ',
          engName: 'Japanese fire belly newt',
          copy: 'エサも扱いやすくて手軽',
          life: '10年以上',
          comment: `水槽の中でまったり過ごしたり、エサを食べたり、
          エサくれるの？って寄ってくるのがほんとにかわいい…
          エサも人工のもの（じゃない場合はエビとか赤虫）でよいし、水槽の管理もあんまり大変じゃないみたいです（こた父談）
          こたきの実家では深めの水槽の上の方にちょこっと足場をつくっていて、熱帯魚も一緒に飼っている。
          ヘビはエサが大変だからイモリくらいにしといたら？（こた父）`
        },
        {
          id: 6,
          category: 'contemporary',
          name: 'ミナミイボイモリ',
          engName: 'Emperor newt',
          copy: 'かわいすぎない？ちっちゃいドラゴン',
          life: '10～20年',
          comment: `こちらもイモリだけど、水の中で過ごさずに基本陸上で虫とかを食べて生きます。
          野生では標高1000～2000ｍの高地にいるので、
          比較的寒さに強い（でも10度以下にならないように）けど夏はすずしくしてあげないとね。
          ケージも小さめで大丈夫そうだし、とにかくこのかわいさが魅力だけど、
          人工飼料に餌付いてくれなかった場合エサが昆虫になるのがな…！`
        },
        {
          id: 7,
          category: 'contemporary',
          name: 'イエアメガエル',
          engName: "White's tree frog",
          copy: 'でもカエルもかわいいよね',
          life: '15～20年',
          comment: `もっちり、緑色でほどよいサイズ感の「ザ・カエル」な見た目が魅力。絵本から出てきたみたいでかわいい…
          野生では木の上で生活するので、登れるような枝とかがいるそうです。でも蓋とか気をつけないと脱走しそう…
          ケージの高さはいるけど、イモリ同様準備するものも少なくて飼いやすそう。
          だがエサはやっぱり昆虫！こたきの実家ではシュレーゲルアオガエル（と思われる）近いカエルを飼っていて、
          ミルワームを食べてるみたいです。コオロギはいやだけどミルワームくらいならいいかな…`
        },
        {
          id: 8,
          category: 'contemporary',
          name: 'ヒョウモントカゲモドキ',
          engName: 'Common leopard gecko',
          copy: '爬虫類界のアイドル！',
          life: '10年',
          comment: `新垣結衣が飼っていて一気に話題になった印象のあるヒョウモントカゲモドキ（通称レオパ）。
          こたきの初めての出会いは横浜の爬虫類カフェだったけど、そのあざとい表情に一発で心を打ち抜かれましたね…さすがアイドル…
          大きさもほどよくて、すばしっこくなくて（かわいい）、特別な照明もいらず、なによりハンドリングができる…！
          飼育しやすさとかわいさの両立がすごい。でもエサは昆虫！`
        },
        { 
          id: 9,
          category: 'ancient',
          name: 'アノマロカリス',
          engName: 'Anomalocaris canadensis（カナダ産のアノマロカリス）',
          copy: 'カンブリアモンスター界のアイドル！',
          life: '約5億2,500万～約5億0,500万年前（古生代カンブリア紀前期終盤～中期）',
          comment: `好物はやわらかい三葉虫。
                  古生物が好きな方はもちろん、そうでない方も知ってる方の多いカンブリアモンスター界のアイドル！
                  この時代ではかなり大きい方のいきもの（約1m）！プール付きの豪邸じゃないと飼えないか…`
         },
        { 
          id: 10,
          category: 'ancient',
          name: 'オパビニア',
          engName: 'Opabinia regalis',
          copy: 'オフィスに常駐（ぬいぐるみ）',
          life: '約5億500万年前（古生代カンブリア紀中期後半）',
          comment: `私のデスクに訪れたことのある方は見たことがあるかも…
          なんでそんなに目も口も飛び出してるの？目立ちたかったの？やりすぎちゃったの？だから絶滅しちゃったの？
          という感じが魅力。ていうか飛び出してるのは口じゃなくて腕だそうで、
          これでつかんで体の下側にある口にはこぶんだって。すごい非効率！
          ぬいぐるみは大きいけど本物は10cmくらい。
          ぬいぐるみは、前職の面接のとき机においてあって、一発で名前を言い当てたらくれました。`
         },
        { 
          id: 11,
          category: 'ancient',
          name: 'ハルキゲニア',
          engName: 'Hallucigenia',
          copy: '想像図が不安定すぎる',
          life: '約5億2,500万- 約5億0,500万年前（古生代カンブリア紀前期中盤）',
          comment: `数多くの古生物研究者を悩ませてきた「幻惑するもの」という意味の名前のいきもの。
          当初は上も下も前も後ろもわからなくて、そもそもこれって1つの生物なの？という状態で、
          一番最初に世に出ていた想像図は上下逆で、丸い頭がついた不思議な形。
          次の想像図では上下が逆になり、（トゲトゲが足ではなく背面になった）、
          さらに一番最近では前後も逆で、ようやく目と口が確認された。（頭だと思われてたのが実はおしりからでた内蔵）
          大きさは3cmくらい。`
         },
      ]
    }
  },
  methods: {
    getImg(index) {
      return require('../assets/images/item/' + this.creature[index].id + '.jpg');
    }
  }
}
</script>

<style src="../assets/scss/list.scss" lang="scss" scoped></style>
