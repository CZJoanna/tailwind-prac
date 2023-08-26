<template>
  <!-- v-for -->
  <div
    un-flex="~ items-center justify-between"
    un-m="b-1rem"
  >
    <div>
      <!-- 日期 -->
      <span class="text-gray">
        {{ priceInfo.date_range[0] }} ~ {{ priceInfo.date_range[1] }}
      </span>
      <!-- 星期 -->
      <div>
        <span class="bg-amber-100 p-1">日</span>
        <span class="bg-amber-100 p-1">一</span>
        <span class="bg-amber-100 p-1">二</span>
      </div>
      <!--特殊房價 -->
      <span>特殊房價：{{ priceInfo.price }}</span>
    </div>
    <div 
      un-flex="~ items-center"
      un-gap="1rem"
    >
      <IEpEditPen class="cursor-pointer" @click="$emit('edit')"/>
      <IEpDelete class="cursor-pointer" @click="$emit('delete')"/>
    </div>
  </div> 
</template>

<script setup>
const props = defineProps({
  priceInfo: {
    type: Object,
    default: () => ({})
  }
})
</script>