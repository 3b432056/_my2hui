<template>
  <div class="flex group">
    <!-- 豎排名字 -->
    <div class="w-16 flex-shrink-0 flex justify-center border-r border-[#2c1e16]/20 pr-4 mr-6">
      <h3 class="text-3xl text-[#2c1e16] tracking-widest group-hover:text-[#8b261b] transition-colors" style="writing-mode: vertical-rl;">
        {{ member.name }}
      </h3>
    </div>
    <!-- 成員詳細介紹 -->
    <div class="flex flex-col justify-center">
      <div class="inline-block border border-[#2c1e16]/30 px-3 py-1 mb-4 w-max text-sm text-[#4a3a31] tracking-widest">
        {{ member.title }}
      </div>
      <p class="text-[#8b261b] italic mb-3 tracking-widest text-lg">「{{ member.quote }}」</p>
      <p v-for="(desc, idx) in member.details" :key="idx" class="text-[#4a3a31] leading-loose text-justify text-sm">
        {{ desc }}
      </p>
    </div>
  </div>
</template>

<script setup>
// 接收父元件傳進來的 member 資料物件
defineProps({
  member: {
    type: Object,
    required: true
  }
})
</script>