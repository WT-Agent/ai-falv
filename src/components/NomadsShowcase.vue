<template>
  <section class="nomads-showcase-section">
    <div class="showcase-header">
      <div class="header-left">
        <h2 class="showcase-title">法律咨询与合同合规实战模板库</h2>
        <p class="showcase-subtitle">精选劳动纠纷、合同诊断、家事分割与侵权维权案例，点击“一键套用”生成专业报告</p>
      </div>
      <span class="showcase-badge">已收录 {{ showcaseItems.length }} 个法律合规模板</span>
    </div>

    <div class="showcase-grid">
      <div 
        v-for="item in showcaseItems" 
        :key="item.id" 
        class="glass-card showcase-card"
      >
        <div class="card-header">
          <span class="scenario-tag">{{ item.tag }}</span>
          <span class="usage-count">{{ item.usageCount }} 次应用</span>
        </div>

        <div class="card-content">
          <h3 class="item-title">{{ item.title }}</h3>
          <p class="item-prompt">“{{ item.prompt }}”</p>
        </div>

        <div class="card-action">
          <button class="apply-btn" @click="applyTemplate(item)">
            <span>一键套用</span>
            <svg class="arrow-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="5" y1="12" x2="19" y2="12"></line>
              <polyline points="12 5 19 12 12 19"></polyline>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const emit = defineEmits<{
  (e: 'apply-template', payload: { prompt: string; legalType?: string; legalField?: string; roleIdentity?: string }): void;
}>();

export interface ShowcaseItem {
  id: string;
  tag: string;
  title: string;
  prompt: string;
  legalType?: string;
  legalField?: string;
  roleIdentity?: string;
  usageCount: string;
}

const showcaseItems = computed<ShowcaseItem[]>(() => [
  {
    id: 'falv-1',
    tag: '劳动维权',
    title: '公司无故辞退 N+1 赔偿与加班费维权',
    prompt: '公司在未进行提前通知的情况下口头辞退员工，且拒绝支付加班费与年终奖。请梳理劳动仲裁所需证据链清单、诉讼请求计算方式及庭审答辩要点。',
    legalType: '劳动纠纷与加班赔偿维权',
    legalField: '劳动合同法',
    roleIdentity: '劳动者员工',
    usageCount: '68.5k'
  },
  {
    id: 'falv-2',
    tag: '租赁纠纷',
    title: '商业房屋租赁合同违约与押金扣留诊断',
    prompt: '房东在合同到期后以墙面磨损为由拒绝退还 2 万元押金，且擅自断水断电。请分析租赁合同违约责任条款，提供催告函模板及维权诉讼策略。',
    legalType: '商业合同诊断与条款修改',
    legalField: '民商法',
    roleIdentity: '个人消费者',
    usageCount: '54.2k'
  },
  {
    id: 'falv-3',
    tag: '货款催收',
    title: '企业买卖合同拖欠货款律师函与诉讼策略',
    prompt: '买方拖欠 50 万元货款超过 6 个月，合同约定诉讼管辖地为乙方所在地。请评估诉讼保全可行性、利息违约金计算及律师函起草要点。',
    legalType: '商业合同诊断与条款修改',
    legalField: '公司法',
    roleIdentity: '公司法务CFO',
    usageCount: '49.1k'
  },
  {
    id: 'falv-4',
    tag: '隐私侵权',
    title: '个人隐私侵权与网络名誉权索赔方案',
    prompt: '某网络平台未经允许公开个人身份信息与肖像，造成恶劣影响。请出具侵权事实认定、证据电子固化方法、精神损害抚慰金索赔依据及发函要求。',
    legalType: '消费维权与侵权赔偿方案',
    legalField: '民商法',
    roleIdentity: '个人消费者',
    usageCount: '42.8k'
  },
  {
    id: 'falv-5',
    tag: '婚姻家事',
    title: '婚前协议与婚后共同财产分割合规诊断',
    prompt: '拟定婚前房产出资与婚后按揭还贷权益划分协议，确保协议具备法律效力且不违反公序良俗，并分析争议解决预防机制。',
    legalType: '婚姻家事与财产分割咨询',
    legalField: '民商法',
    roleIdentity: '个人消费者',
    usageCount: '37.6k'
  },
  {
    id: 'falv-6',
    tag: '知产合规',
    title: '软件开发外包合同知识产权归属与免责诊断',
    prompt: '评估软件外包开发合同中的交付验收标准、源码知识产权归属条款、侵犯第三方专利权免责声明及争议解决管辖条款。',
    legalType: '商业合同诊断与条款修改',
    legalField: '知识产权法',
    roleIdentity: '企业HR',
    usageCount: '35.3k'
  }
]);

function applyTemplate(item: ShowcaseItem) {
  emit('apply-template', {
    prompt: item.prompt,
    legalType: item.legalType,
    legalField: item.legalField,
    roleIdentity: item.roleIdentity
  });
}
</script>

<style scoped>
.nomads-showcase-section {
  margin-top: 2rem;
  width: 100%;
}

.showcase-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 1.25rem;
  padding-bottom: 0.75rem;
  border-bottom: 1px solid var(--card-border);
}

.showcase-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--text-primary);
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.showcase-subtitle {
  font-size: 0.825rem;
  color: var(--text-secondary);
  margin-top: 0.25rem;
}

.showcase-badge {
  font-size: 0.75rem;
  color: #a5b4fc;
  background: rgba(99, 102, 241, 0.12);
  border: 1px solid rgba(99, 102, 241, 0.25);
  padding: 4px 10px;
  border-radius: 20px;
}

.showcase-grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 1.25rem;
}

@media (min-width: 640px) {
  .showcase-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .showcase-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

.showcase-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  padding: 1.25rem;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--card-border);
  border-radius: 14px;
  transition: all 0.25s ease;
}

.showcase-card:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(99, 102, 241, 0.4);
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.75rem;
}

.scenario-tag {
  font-size: 0.75rem;
  font-weight: 600;
  padding: 3px 8px;
  border-radius: 6px;
  background: rgba(168, 85, 247, 0.15);
  color: #c084fc;
  border: 1px solid rgba(168, 85, 247, 0.3);
}

.usage-count {
  font-size: 0.75rem;
  color: var(--text-secondary);
}

.card-content {
  margin-bottom: 1rem;
  flex: 1;
}

.item-title {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.4rem;
}

.item-prompt {
  font-size: 0.825rem;
  color: var(--text-secondary);
  line-height: 1.45;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  font-style: italic;
}

.card-action {
  padding-top: 0.75rem;
  border-top: 1px solid rgba(255, 255, 255, 0.04);
}

.apply-btn {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  padding: 0.5rem 1rem;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.3);
  border-radius: 8px;
  color: #a5b4fc;
  font-size: 0.825rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

.showcase-card:hover .apply-btn {
  background: var(--primary-gradient);
  border-color: transparent;
  color: white;
}

.arrow-icon {
  width: 14px;
  height: 14px;
  transition: transform 0.2s ease;
}

.apply-btn:hover .arrow-icon {
  transform: translateX(3px);
}
</style>
