<script lang="ts" setup>

import { ElIcon } from 'element-plus'
import { Document, Files, MagicStick, Film, Link as LinkIcon } from '@element-plus/icons-vue'

// Badge
const badge = 'Technical Report'

// 标题
const titleLine1 = 'Uni-LaViRA: Language-Vision-Robot Actions'
const titleLine2 = 'Translation for Unified Embodied Navigation'

// 副标题
const subtitle = ''

// 作者清单
const authors = [
  { name: "Hongyu Ding", homepage: "#", flags: "1,2,*" },
  { name: "Sizhuo Zhang", homepage: "#", flags: "3,*" },
  { name: "Ziming Xu", homepage: "#", flags: "1,*" },
  { name: "Jinwen Guo", homepage: "#", flags: "1" },
  { name: "Hongxiu Liu", homepage: "#", flags: "1" },
  { name: "Xingzhi Cheng", homepage: "#", flags: "1" },
  { name: "Zixuan Chen", homepage: "#", flags: "1" },
  { name: "Haifei Qi", homepage: "#", flags: "4" },
  { name: "Duo Wang", homepage: "#", flags: "4" },
  { name: "Hao Xu", homepage: "#", flags: "1" },
  { name: "Jieqi Shi", homepage: "#", flags: "1,†" },
  { name: "Yifan Zhang", homepage: "#", flags: "2,†" },
  { name: "Jing Huo", homepage: "#", flags: "1,†" },
  { name: "Jian Cheng", homepage: "#", flags: "2" },
  { name: "Yang Gao", homepage: "#", flags: "1" },
  { name: "Jiebo Luo", homepage: "#", flags: "5" },
]

// 单位清单
const affiliations = [
  { flag: "1", name: "Nanjing University" },
  { flag: "2", name: "Institute of Automation, Chinese Academy of Sciences" },
  { flag: "3", name: "Beihang University" },
  { flag: "4", name: "BMW (Nanjing) Information Technology Co., Ltd." },
  { flag: "5", name: "University of Rochester" },
]

// 脚注
const footnote = "* Equal contribution    † Corresponding authors"

// 按钮
const buttons = [
  { name: "arXiv", href: "https://arxiv.org/abs/2605.27582", icon: Document },
  { name: "Code", href: "https://github.com/NJU-R-L-Group-Embodied-Lab/lavira-code", icon: Files },
  { name: "BibTeX", href: "#bibtex", icon: LinkIcon },
]

// 统计数字（已移除）
const stats = []

</script>

<template>
  <section id="overview" class="hero">
    <div class="hero-inner">

      <!-- Title -->
      <div class="hero-title-block">
        <div class="hero-title-line1">Uni-LaViRA</div>
        <div class="hero-title-line2">Language–Vision–Robot Actions Translation</div>
        <div class="hero-title-line3">for Unified Embodied Navigation</div>
      </div>

      <!-- Subtitle -->
      <p v-if="subtitle" class="hero-subtitle">{{ subtitle }}</p>

      <!-- Authors -->
      <div class="hero-authors">
        <template v-for="(author, idx) in authors" :key="author.name">
          <a :href="author.homepage" class="author-link">
            {{ author.name }}<sup v-if="author.flags">{{ author.flags }}</sup>
          </a>
          <span v-if="idx < authors.length - 1" class="author-sep">,&nbsp;</span>
        </template>
      </div>

      <!-- Affiliations -->
      <div class="hero-affiliations">
        <template v-for="(aff, idx) in affiliations" :key="aff.flag">
          <span class="affiliation">
            <sup>{{ aff.flag }}</sup>{{ aff.name }}
          </span>
          <span v-if="idx < affiliations.length - 1" class="aff-sep">&nbsp;&nbsp;</span>
        </template>
      </div>

      <!-- Footnote -->
      <div class="hero-footnote">{{ footnote }}</div>

      <!-- Buttons -->
      <div class="hero-buttons">
        <a v-for="btn in buttons" :key="btn.name" :href="btn.href" class="hero-btn">
          <el-icon :size="16"><component :is="btn.icon" /></el-icon>
          <span>{{ btn.name }}</span>
        </a>
      </div>

      <!-- Stats -->
      <div class="hero-stats">
        <div v-for="stat in stats" :key="stat.label" class="stat-card">
          <div class="stat-value">{{ stat.value }}</div>
          <div class="stat-label">{{ stat.label }}</div>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.hero {
  padding: 100px 24px 16px;
  text-align: center;
}

.hero-inner {
  max-width: 1700px;
  margin: 0 auto;
}

/* Badge */
.hero-badge {
  display: inline-block;
  padding: 4px 14px;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 1px;
  text-transform: uppercase;
  color: var(--accent);
  border: 1px solid var(--accent);
  border-radius: 20px;
  margin-bottom: 24px;
}

/* Title block */
.hero-title-block {
  margin: 0 0 20px;
  text-align: center;
}

.hero-title-line1 {
  font-family: "MyFont", -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  font-size: 86px;
  font-weight: 800;
  line-height: 1.05;
  letter-spacing: 2px;
  background: linear-gradient(135deg, #CF7359 0%, #D97E67 55%, #FFF1EC 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  text-shadow: 0 0 40px rgba(207, 115, 89, 0.15);
  margin-bottom: 10px;
}

.hero-title-line2 {
  font-family: "MyFont", -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  font-size: 38px;
  font-weight: 600;
  line-height: 1.25;
  letter-spacing: 1px;
  background: linear-gradient(135deg, #CF7359 0%, #CF7359 70%, #FFF1EC 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  margin-bottom: 4px;
}

.hero-title-line3 {
  font-family: "MyFont", -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  font-size: 38px;
  font-weight: 600;
  line-height: 1.25;
  letter-spacing: 1px;
  background: linear-gradient(135deg, rgba(207, 115, 89, 0.85) 0%, rgba(207, 115, 89, 0.7) 70%, rgba(255, 241, 236, 0.6) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

/* Subtitle */
.hero-subtitle {
  font-size: 18px;
  color: var(--text-secondary);
  margin: 0 0 32px;
  line-height: 1.6;
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
}

/* Authors */
.hero-authors {
  margin-bottom: 8px;
  font-size: 17px;
  line-height: 1.8;
}

.author-link {
  color: var(--text-primary);
  text-decoration: none;
  transition: color var(--transition-fast);
}
.author-link:hover {
  color: var(--accent);
}
.author-link sup {
  color: var(--text-tertiary);
  margin-left: 1px;
  font-size: 11px;
}

.author-sep {
  color: var(--text-tertiary);
}

/* Affiliations */
.hero-affiliations {
  margin-bottom: 6px;
  font-size: 15px;
  color: var(--text-secondary);
}
.affiliation sup {
  color: var(--text-tertiary);
  margin-right: 2px;
  font-size: 11px;
}

/* Footnote */
.hero-footnote {
  font-size: 13px;
  color: var(--text-tertiary);
  margin-bottom: 32px;
}

/* Buttons */
.hero-buttons {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 10px;
  margin-bottom: 48px;
}

.hero-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 8px 18px;
  font-size: 14px;
  font-weight: 500;
  color: var(--text-primary);
  background: var(--bg-card);
  border: 1px solid var(--border-subtle);
  border-radius: 8px;
  text-decoration: none;
  transition: all var(--transition-fast);
}
.hero-btn:hover {
  background: var(--bg-card-hover);
  border-color: var(--accent);
  color: var(--accent);
}

/* Stats */
.hero-stats {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 16px;
  max-width: 700px;
  margin: 0 auto;
}

.stat-card {
  background: var(--bg-card);
  border: 1px solid var(--border-card);
  border-radius: var(--radius-md);
  padding: 20px 12px;
  text-align: center;
}

.stat-value {
  font-size: 28px;
  font-weight: 700;
  color: var(--accent);
  margin-bottom: 4px;
}

.stat-label {
  font-size: 13px;
  color: var(--text-secondary);
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

/* Responsive */
@media (max-width: 768px) {
  .hero {
    padding: 80px 16px 32px;
  }
  .hero-title-line1 {
    font-size: 42px;
    letter-spacing: 1px;
  }
  .hero-title-line2,
  .hero-title-line3 {
    font-size: 20px;
  }
  .hero-subtitle {
    font-size: 15px;
  }
  .hero-authors {
    font-size: 15px;
  }
  .hero-stats {
    grid-template-columns: repeat(2, 1fr);
    gap: 10px;
  }
  .stat-value {
    font-size: 22px;
  }
  .hero-btn {
    padding: 7px 14px;
    font-size: 13px;
  }
}
</style>
