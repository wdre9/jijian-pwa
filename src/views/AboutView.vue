<template>
  <div class="page page--plain">
    <van-nav-bar
      title="关于"
      left-text="返回"
      left-arrow
      fixed
      placeholder
      @click-left="router.back()"
    />

    <div class="page__inner">
      <div class="card hero">
        <div class="hero__logo">计</div>
        <div class="hero__name">计件工资记账</div>
        <div class="hero__ver">版本 {{ version }} · 移动端 Web App（PWA）</div>
        <div class="hero__badges">
          <van-tag round plain type="primary">纯本地存储</van-tag>
          <van-tag round plain type="success">离线可用</van-tag>
          <van-tag round plain type="warning">无需登录</van-tag>
        </div>
      </div>

      <div class="card">
        <div class="card__head">
          <div class="card__title">功能一览</div>
        </div>
        <div class="feat" v-for="f in features" :key="f.t">
          <div class="feat__t">{{ f.t }}</div>
          <div class="feat__d">{{ f.d }}</div>
        </div>
      </div>

      <div class="card">
        <div class="card__head">
          <div class="card__title">安装到手机桌面</div>
        </div>
        <div class="steps">
          <div class="step">
            <div class="step__no">安卓</div>
            <div class="step__d">
              用 Chrome / 夸克 / UC 打开本页 → 等页面加载完成 → 浏览器菜单（或底部弹出提示）选择
              「添加到主屏幕 / 安装应用」。
            </div>
          </div>
          <div class="step">
            <div class="step__no">iPhone</div>
            <div class="step__d">
              用 Safari 打开本页 → 点击底部分享按钮 → 选择「添加到主屏幕」→ 确认。
            </div>
          </div>
          <div class="step">
            <div class="step__no">说明</div>
            <div class="step__d">
              安装后图标会出现在桌面，点开即用全屏界面；不安装也可以直接用浏览器打开使用。
            </div>
          </div>
        </div>
      </div>

      <div class="card">
        <div class="card__head">
          <div class="card__title">数据与隐私</div>
        </div>
        <div class="privacy">
          <p>
            全部数据（计件记录、产品、工序、工人、设置）都保存在你这台设备的浏览器本地数据库（IndexedDB）中，
            <b>不会上传到任何服务器</b>，也没有账号与登录。
          </p>
          <p>
            因此：清理浏览器数据 / 卸载浏览器 / 使用无痕模式会导致数据丢失，请定期在「数据与导出」里
            <b>导出备份</b>保存到手机文件或微信收藏。
          </p>
          <p>换手机时：在新手机打开同一网址 → 「数据与导出」→ 导入备份（.json）即可完整恢复。</p>
        </div>
      </div>

      <div class="card">
        <div class="card__head">
          <div class="card__title">使用小贴士</div>
        </div>
        <div class="privacy">
          <p>1. 先在「产品与工序」把产品和每道工序的单件工价建好，之后记账只要点两下。</p>
          <p>2. 首页快捷区点工序卡片即可快速记账，数量默认 1 件，可直接改数量。</p>
          <p>3. 忘记填工人也不要紧，记录仍会计入总额，只是不参与按人统计。</p>
          <p>4. 统计页可切换本周 / 本月 / 自定义区间，并支持导出统计长图发群。</p>
        </div>
      </div>

      <div class="foot">
        <div>由 Marvis File Agent 构建交付</div>
        <div style="margin-top: 4px">数据仅保存在本机 · 请定期备份</div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useRouter } from 'vue-router'

const router = useRouter()
const version = '1.0.0'

const features = [
  { t: '快速记账', d: '选产品 → 选工序 → 填数量，单价自动带出，3 秒完成一笔记账' },
  { t: '计件明细', d: '按天分组查看，支持关键词搜索、时间筛选、多选删除、批量导出' },
  { t: '产品与工序', d: '产品下挂多道工序，每道工序独立工价，可排序、可停用' },
  { t: '统计汇总', d: '日/周/月/自定义区间，产品占比、工序排行、工人排行、班次对比、月度趋势' },
  { t: '数据与导出', d: 'Excel（明细 + 5 张汇总表）、CSV、JSON 备份与还原、演示数据' },
  { t: '本地优先', d: '全部数据离线保存在本机，无需注册登录，不上传服务器' }
]
</script>

<style scoped>
.hero {
  text-align: center;
  padding: 22px 16px;
}

.hero__logo {
  width: 56px;
  height: 56px;
  border-radius: 16px;
  margin: 0 auto 10px;
  background: linear-gradient(180deg, #3b82f6, #1d4ed8);
  color: #fff;
  font-size: 26px;
  font-weight: 700;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 6px 16px rgba(37, 99, 235, 0.28);
}

.hero__name {
  font-size: 17px;
  font-weight: 700;
  color: var(--app-text);
}

.hero__ver {
  font-size: 12px;
  color: var(--app-text-3);
  margin-top: 4px;
}

.hero__badges {
  display: flex;
  justify-content: center;
  gap: 6px;
  margin-top: 12px;
}

.feat {
  padding: 9px 0;
  border-bottom: 1px solid var(--app-line);
}

.feat:last-child {
  border-bottom: none;
}

.feat__t {
  font-size: 13px;
  font-weight: 600;
  color: var(--app-text);
}

.feat__d {
  font-size: 12px;
  color: var(--app-text-3);
  line-height: 1.6;
  margin-top: 3px;
}

.steps {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.step {
  display: flex;
  gap: 10px;
}

.step__no {
  flex-shrink: 0;
  font-size: 11px;
  font-weight: 600;
  color: var(--app-primary);
  background: var(--app-primary-weak);
  border-radius: 6px;
  padding: 2px 7px;
  height: 20px;
  line-height: 16px;
}

.step__d {
  font-size: 12px;
  color: var(--app-text-2);
  line-height: 1.7;
}

.privacy p {
  font-size: 12px;
  color: var(--app-text-2);
  line-height: 1.75;
  margin: 0 0 8px;
}

.privacy b {
  color: var(--app-text);
}

.foot {
  text-align: center;
  font-size: 11px;
  color: var(--app-text-3);
  padding: 14px 0 10px;
}
</style>
