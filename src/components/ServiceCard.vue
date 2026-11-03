<template>
  <div class="relative border border-[#2c1e16]/20 p-8 bg-[#fff8e8]/60 hover:bg-[#2c1e16]/[0.02] transition-colors">
    <div class="text-[#8b261b]/30 text-5xl mb-4 font-light italic">{{ service.id }}</div>
    <h3 class="text-2xl text-[#2c1e16] tracking-widest mb-1">{{ service.title }}</h3>
    <p class="text-[#4a3a31] text-sm tracking-widest mb-8 border-b border-[#2c1e16]/10 pb-4" v-html="service.subtitle"></p>
    <ul class="space-y-6">
      <li v-for="(item, idx) in service.items" :key="idx" class="text-sm tracking-widest">
        <!-- 第一行：帶有小菱形圖標的主要文字 -->
        <div class="flex items-center text-[#4a3a31]">
          <span class="w-1.5 h-1.5 bg-[#8b261b]/60 rotate-45 mr-4 flex-shrink-0"></span>
          <span>{{ item.main }}</span>
        </div>
        <!-- 第二行：不帶項目符號、自動換行的 edited by 備註 -->
        <div v-if="item.sub" class="text-xs text-[#8b261b]/80 ml-6 mt-1 italic">
          {{ item.sub }}
        </div>
      </li>
    </ul>
  </div>
</template>

<script setup>
defineProps({
  service: {
    type: Object,
    required: true
  }
})
</script>