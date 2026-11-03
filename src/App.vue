<template>
  <div class="selection:bg-[#8b261b]/20 selection:text-[#8b261b] min-h-screen font-serif" style="background: linear-gradient(to bottom, #fff8e8, #f2e4c2); color: #2c1e16;">
    
    <!-- 頂部功能列 -->
    <header class="w-full px-6 py-3 flex justify-between items-center text-xs tracking-widest text-[#4a3a31]/75 border-b border-[#2c1e16]/10 relative">
      <!-- 左上側：English 語言切換 -->
      <div class="flex items-center space-x-6">
        <div class="relative group cursor-pointer">
          <span class="hover:text-[#8b261b] transition-colors flex items-center gap-1">English</span>
          <div class="absolute left-0 top-full mt-2 w-48 bg-[#fff8e8] border border-[#2c1e16]/30 p-3 shadow-lg opacity-0 invisible group-hover:opacity-100 group-hover:visible transition-all duration-300 z-50 text-center">
            <p class="text-[#8b261b] tracking-widest text-xs">尚未支持此語言。</p>
          </div>
        </div>
        <span @click="currentTab = 'qa'" class="hover:text-[#8b261b] cursor-pointer transition-colors">Ｑ&Ａ</span>
      </div>

      <!-- 右上側：登入系統 -->
      <div class="flex items-center space-x-6">
        <div class="relative group cursor-pointer">
          <div class="flex items-center hover:text-[#8b261b] transition-colors py-1">
            <span>登入系統</span>
          </div>
          <div class="absolute right-0 top-full mt-2 w-64 bg-[#fff8e8] border border-[#2c1e16]/30 p-4 shadow-xl opacity-0 invisible group-hover:opacity-100 group-hover:visible transition-all duration-300 z-50 text-left" @click.stop>
            <div class="space-y-3">
              <div class="text-xs text-[#8b261b] tracking-widest border-b border-[#2c1e16]/20 pb-1 font-bold">墜隳樓機密通道</div>
              <div>
                <label class="block text-[10px] text-[#4a3a31] tracking-widest mb-1">代號</label>
                <input type="text" placeholder="請輸入代號..." class="w-full bg-[#fffcf5] border border-[#2c1e16]/30 px-2 py-1 text-xs text-[#2c1e16] focus:outline-none focus:border-[#8b261b]">
              </div>
              <div>
                <label class="block text-[10px] text-[#4a3a31] tracking-widest mb-1">密語</label>
                <input type="password" placeholder="請輸入密語..." class="w-full bg-[#fffcf5] border border-[#2c1e16]/30 px-2 py-1 text-xs text-[#2c1e16] focus:outline-none focus:border-[#8b261b]">
              </div>
              <button type="button" @click="alertLogin" class="w-full bg-[#2c1e16] text-[#e8dcb8] py-1 text-xs tracking-widest hover:bg-[#8b261b] transition-colors">
                驗證通行
              </button>
              <p class="text-[10px] text-[#8b261b]/80 tracking-wider text-center pt-1">該功能並未開啟，純屬擺設。</p>
            </div>
          </div>
        </div>
      </div>
    </header>

    <!-- 標題與導覽面板 -->
    <div class="pt-6 pb-4 text-center border-b border-[#2c1e16]/10 bg-[#f3e9d2]/40 backdrop-blur-sm sticky top-0 z-30">
      <div class="mb-4">
        <h1 class="text-3xl md:text-4xl tracking-[0.4em] ml-[0.4em] font-bold text-[#2c1e16]">
          暮燁墜隳樓
        </h1>
        <p class="mt-2 text-[#be0016] tracking-[0.6em] text-[10px] opacity-85 ml-[0.6em]">
          ʍʏʐɦʊɨ𐔌՞ ܸ.ˬ.ܸ՞𐦯
        </p>
      </div>

      <!-- 橫向導覽按鈕 -->
      <nav class="flex justify-center flex-wrap gap-x-8 md:gap-x-12 gap-y-2 px-4">
        <button v-for="tab in tabs" :key="tab.id" @click="currentTab = tab.id"
                :class="['text-sm md:text-base tracking-[0.25em] relative py-1 transition-all', currentTab === tab.id ? 'text-[#8b261b]' : 'text-[#4a3a31] hover:text-[#8b261b]']">
          {{ tab.name }}
          <span :class="['absolute bottom-0 left-0 w-full h-[1.5px] bg-[#8b261b] transition-transform duration-300', currentTab === tab.id ? 'scale-x-100' : 'scale-x-0']"></span>
        </button>
      </nav>
    </div>

    <!-- 主內容渲染區 -->
    <main class="py-16 px-6 sm:px-12 max-w-5xl mx-auto min-h-[50vh]">
      
      <!-- 1. 組織介紹 -->
      <div v-if="currentTab === 'history'" class="max-w-4xl mx-auto space-y-16 animate-fade-in">
        <div class="flex flex-col items-center mb-16">
          <h2 class="text-2xl tracking-[0.3em] text-[#2c1e16] mb-4">組織介紹</h2>
          <div class="w-12 h-[1px] bg-[#8b261b]"></div>
        </div>
        
        <div class="space-y-16">
          <div class="flex flex-col md:flex-row gap-8 items-start">
            <div class="md:w-1/4 text-right border-r border-[#2c1e16]/20 pr-6 pb-4">
              <span class="text-[#8b261b] tracking-widest text-lg">營運宗旨</span>
            </div>
            <div class="md:w-3/4 space-y-3">
              <h3 class="text-xl tracking-widest mb-3 text-[#2c1e16]">妖不虛榮枉少年</h3>
              <p class="text-[#4a3a31] leading-loose text-justify">人為什麼要幹活？是為了金錢？是的是的，您答對了，就是這麼簡單。</p>
              <p class="text-[#4a3a31] leading-loose text-justify">金錢是我們的血液，是我們的氧氣，沒有它，我們就無法呼吸。</p>
              <p class="text-[#4a3a31] leading-loose text-justify">加入暮燁墜隳樓，和我們一起沒心沒肺的搞錢，才是您人生的正軌！</p>
            </div>
          </div>

          <div class="flex flex-col md:flex-row gap-8 items-start">
            <div class="md:w-1/4 text-right border-r border-[#2c1e16]/20 pr-6 pb-4">
              <span class="text-[#8b261b] tracking-widest text-lg">立場聲明</span>
            </div>
            <div class="md:w-3/4 space-y-3">
              <h3 class="text-xl tracking-widest mb-3 text-[#2c1e16]">誰有錢我站誰</h3>
              <p class="text-[#4a3a31] leading-loose text-justify">暮燁墜隳樓，簡稱「墜隳樓」。</p>
              <p class="text-[#4a3a31] leading-loose text-justify">浮於苦境上空的情報組織，主營情報交換。</p>
              <p class="text-[#4a3a31] leading-loose text-justify">不屬於正邪兩道，不受任何勢力管轄。</p>
              <p class="text-[#4a3a31] leading-loose text-justify">只要禍事可能波及我們，對我們無利益，我們就跑！</p>
            </div>
          </div>

          <div class="flex flex-col md:flex-row gap-8 items-start">
            <div class="md:w-1/4 text-right border-r border-[#2c1e16]/20 pr-6 pb-4">
              <span class="text-[#8b261b] tracking-widest text-lg">荒唐事跡</span>
            </div>
            <div class="md:w-3/4 space-y-3">
              <h3 class="text-xl tracking-widest mb-3 text-[#2c1e16]">副樓主賣藝不賣身</h3>
              <p class="text-[#4a3a31] leading-loose text-justify">墜隳樓給人一種不正經酒樓的感覺。</p>
              <p class="text-[#4a3a31] leading-loose text-justify">副樓主總穿得像花魁一樣，讓人總想問他到底是做什麼的。</p>
            </div>
          </div>
        </div>
      </div>

      <!-- 2. 成員組成 (使用 MemberCard 迴圈渲染) -->
      <div v-else-if="currentTab === 'members'" class="max-w-5xl mx-auto animate-fade-in">
        <div class="flex flex-col items-center mb-16">
          <h2 class="text-2xl tracking-[0.3em] text-[#2c1e16] mb-4">核心成員</h2>
          <div class="w-12 h-[1px] bg-[#8b261b]"></div>
        </div>
        <div class="grid md:grid-cols-2 gap-x-12 gap-y-16">
          <MemberCard v-for="(item, index) in membersData" :key="index" :member="item" />
        </div>
      </div>

      <!-- 3. 業務提供 (使用 ServiceCard 迴圈渲染) -->
      <div v-else-if="currentTab === 'services'" class="max-w-5xl mx-auto animate-fade-in">
        <div class="flex flex-col items-center mb-16">
          <h2 class="text-2xl tracking-[0.3em] text-[#2c1e16] mb-4">業務範疇</h2>
          <div class="w-12 h-[1px] bg-[#8b261b]"></div>
        </div>
        <div class="grid md:grid-cols-3 gap-12">
          <ServiceCard v-for="srv in servicesData" :key="srv.id" :service="srv" />
        </div>
      </div>

      <!-- 4. 聯絡我們 -->
      <div v-else-if="currentTab === 'contact'" class="max-w-3xl mx-auto animate-fade-in">
        <div class="flex flex-col items-center mb-16">
          <h2 class="text-2xl tracking-[0.3em] text-[#2c1e16] mb-4">寒鴉傳信</h2>
          <div class="w-12 h-[1px] bg-[#8b261b]"></div>
          <p class="mt-4 text-[#4a3a31] tracking-widest text-sm">留下委託，本樓專員將於暗處與您接洽</p>
        </div>
        <form class="space-y-10" @submit.prevent="alert('密函已透過暗線送出，請靜候回音。')">
          <div class="grid md:grid-cols-2 gap-10">
            <input type="text" placeholder="尊姓大名" required class="w-full bg-transparent border-b border-[#2c1e16]/30 py-3 text-[#2c1e16] tracking-widest focus:outline-none focus:border-[#8b261b] placeholder-[#2c1e16]/30">
            <input type="text" placeholder="聯繫暗號" required class="w-full bg-transparent border-b border-[#2c1e16]/30 py-3 text-[#2c1e16] tracking-widest focus:outline-none focus:border-[#8b261b] placeholder-[#2c1e16]/30">
          </div>
          <select class="w-full bg-transparent border-b border-[#2c1e16]/30 py-3 text-[#2c1e16] tracking-widest focus:outline-none focus:border-[#8b261b] cursor-pointer">
            <option value="" disabled selected class="bg-[#f2e4c2]">請選擇委託性質...</option>
            <option value="1" class="bg-[#f2e4c2]">情報出售</option>
            <option value="2" class="bg-[#f2e4c2]">神醫聖手</option>
            <option value="3" class="bg-[#f2e4c2]">特殊服務</option>
          </select>
          <textarea rows="4" placeholder="請簡述您的需求，本樓恪守保密原則..." required class="w-full bg-transparent border-b border-[#2c1e16]/30 py-3 text-[#2c1e16] tracking-widest focus:outline-none focus:border-[#8b261b] resize-none placeholder-[#2c1e16]/30"></textarea>
          <div class="text-center pt-8">
            <button type="submit" class="border border-[#2c1e16] text-[#2c1e16] hover:bg-[#2c1e16] hover:text-[#e8dcb8] px-12 py-3 tracking-[0.3em] transition-all duration-500">
              遞交密函
            </button>
          </div>
        </form>
      </div>

      <!-- 5. 組織公告 -->
      <div v-else-if="currentTab === 'announcement'" class="max-w-4xl mx-auto animate-fade-in">
        <div class="flex flex-col items-center mb-16">
          <h2 class="text-2xl tracking-[0.3em] text-[#2c1e16] mb-4">組織公告</h2>
          <div class="w-12 h-[1px] bg-[#8b261b]"></div>
        </div>
        <div class="space-y-8">
          <div class="border-b border-[#2c1e16]/15 pb-6">
            <div class="text-[#8b261b] text-xs tracking-widest mb-2">永久置頂</div>
            <h3 class="text-xl tracking-widest mb-2 text-[#2c1e16]">【招募】大荒眾妖想搞錢的，墜隳樓歡迎你.ᐟ.ᐟ</h3>
            <p class="text-[#4a3a31] text-sm leading-relaxed">帶著你的才能，加入墜隳樓，和我們一起虛榮.ᐟ.ᐟ</p>
          </div>
        </div>
      </div>

      <!-- 6. 常見問答 -->
      <div v-else-if="currentTab === 'qa'" class="max-w-3xl mx-auto animate-fade-in">
        <div class="flex flex-col items-center mb-16">
          <h2 class="text-2xl tracking-[0.3em] text-[#2c1e16] mb-4">常見問答</h2>
          <div class="w-12 h-[1px] bg-[#8b261b]"></div>
        </div>
        <div class="space-y-6 text-sm text-[#4a3a31]">
          <div><strong class="text-[#2c1e16]">Q: 如何確認委託已被接單？</strong><br>A: 本樓將於三日內透過您留下的聯繫暗號做出回覆。</div>
          <div><strong class="text-[#2c1e16]">Q: 委託費用如何結算？</strong><br>A: 依照執行對象收取黃金白銀、珍稀礦石甚至...幾頓飯就能解決。</div>
        </div>
      </div>

    </main>

    <!-- 頁尾 -->
    <footer class="py-12 text-center text-[#4a3a31]/60 text-xs tracking-widest border-t border-[#2c1e16]/10">
      <p>© 2026 暮燁墜隳樓 All Rights Reserved.</p>
    </footer>

  </div>
</template>

<script setup>
import { ref } from 'vue'
import MemberCard from './components/MemberCard.vue'
import ServiceCard from './components/ServiceCard.vue'

const currentTab = ref('history')

const tabs = [
  { id: 'history', name: '組織介紹' },
  { id: 'members', name: '成員組成' },
  { id: 'services', name: '業務提供' },
  { id: 'contact', name: '聯絡我們' },
  { id: 'announcement', name: '組織公告' }
]

// 核心成員模擬資料
const membersData = ref([
  {
    name: '晏朝景',
    title: '御珩公子',
    quote: '跟我交換情報，或是死守秘密？',
    info: '畢方｜28歲｜187cm｜男',
    desc: '個性清冷的情報商，墜隳樓之主。行蹤成謎，組織內部都不一定聯絡得上他。樓主總撐著血紅色傘，傘柄是畢方浮雕，內藏青中帶紅的軟劍，傘緣綴飾黃色符紙，月光下更添詭異。'
  },
  {
    name: '豔赨閣',
    title: '馭蘅公子',
    quote: '你那解藥藥力，比我的毒發快？',
    info: '赤鱬｜24歲｜178cm｜男',
    desc: '本名葬荒，墜隳樓代樓主。藥師，酷愛製毒和調香。樓主不在時由其坐鎮指揮。手持物為天秤象徵裁決，金髮紫衣，穿得跟痾...行首似的。不過豔副樓主真的不賣身（再次強調）。'
  },
  {
    name: '赩赫',
    title: '緋燁染霄',
    quote: '怎麼不笑了呀，是不喜歡笑嗎？',
    info: '鬼車｜22歲｜184cm｜男',
    desc: '身法詭異的殺手，貪吃並且話癆。手持物為刃扇。偏好在目標享用美食時下手，為了不浪費食物(其實就是他想蹭一頓)會把東西吃光，一面優雅用餐一面出言嘲諷目標。'
  },
  {
    name: '肂㱙',
    title: '萌燁絨樞',
    quote: '你手上亮晶晶能可以給我嗎？',
    info: '猼訑｜16歲｜158cm｜女',
    desc: '冷兵器專家，擅長各種兵器的製造設計及維護。晏朝景的傘劍、赩赫的刃扇皆為其手筆。最近正在考慮改造葬荒的藥秤或泠澈的醫典？'
  },
  {
    name: '泠澈',
    title: '寒燁極淵',
    quote: '你的死因也未必不能是解剖。',
    info: '文鰩｜26歲｜193cm｜男',
    desc: '醫術高超神祕莫測，不愛露面的醫者，墜隳樓最大外快來源。關於此人目前記載不多。'
  }
])

// 業務提供模擬資料（結構已完美對應 ServiceCard.vue）
const servicesData = ref([
  {
    id: '01',
    title: '情報出售',
    subtitle: '我們不收沒用的東西<br>像你的命感覺就挺不值錢',
    items: [
      { main: '一份情報僅售賣一次（有商德的好嗎！）', sub: '' },
      { main: '可用其他機密交換', sub: '' },
      { main: '故事讓我滿意', sub: 'edited by 豔赨閣' },
      { main: '也收珍稀礦石！', sub: 'edited by 肂㱙' }
    ]
  },
  {
    id: '02',
    title: '神醫聖手',
    subtitle: '疑難雜症他信手拈來',
    items: [
      { main: '各種疾病診斷+治療', sub: '' },
      { main: '心理疾病也能醫', sub: '' },
      { main: '藥物開發', sub: '' },
      { main: '安神香訂製', sub: 'edited by 豔赨閣' }
    ]
  },
  {
    id: '03',
    title: '特殊服務',
    subtitle: '您能想到的 我們努力達成',
    items: [
      { main: '🈶花錢買兇', sub: '' },
      { main: '🈶雇保鑣', sub: '' },
      { main: '🈶防禦機關工事', sub: '' },
      { main: '🈶專屬武器設計', sub: '' }
    ]
  }
])

function alertLogin() {
  alert('此功能未開啟，純屬裝飾擺設。')
}
</script>