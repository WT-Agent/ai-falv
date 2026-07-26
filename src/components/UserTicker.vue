<template>
  <div class="glass-card ticker-card">
    <div class="ticker-wrapper">
      <div v-for="(item, index) in tickerItems" :key="index" class="ticker-item">
        <span>{{ item.text }}</span>
        <span style="color: var(--success-color); font-weight: bold;">[方案生成完成]</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const tickerItems = ref([
  { text: '用户 138****9281 完成了互联网公司无故辞退 N+1 赔偿诉讼证据链方案' },
  { text: '用户 177****4019 完成了商业房屋租赁合同违约责任与押金退还条款修改' },
  { text: '用户 189****3320 完成了软件开发外包合同付款节点与知识产权归属诊断' },
  { text: '用户 131****8829 生成了婚前房产协议与财产分割法律合规建议' },
  { text: '用户 153****1290 完成了电商消费纠纷欺诈三倍赔偿维权起诉状要点' },
]);
</script>
