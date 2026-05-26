<script lang="ts" setup>
import SectionWrapper from '../SectionWrapper.vue';

const tableData = [
  { benchmark: 'VLN-CE R2R',  sr: '60.7±2.1',  osr: '73.7±1.2',    ne: '3.66±0.26',    spl: '47.7±1.6',  ndtw: '—',        acc: '—' },
  { benchmark: 'VLN-CE RxR',  sr: '51.3±2.3',  osr: '—',           ne: '6.48±0.14',    spl: '34.0±1.9',  ndtw: '53.7±0.6', acc: '—' },
  { benchmark: 'HM3D-v2',     sr: '77.7±2.1',  osr: '—',           ne: '—',            spl: '46.1±1.8',  ndtw: '—',        acc: '—' },
  { benchmark: 'HM3D-OVON',   sr: '60.0±6.1',  osr: '—',           ne: '—',            spl: '40.5±1.1',  ndtw: '—',        acc: '—' },
  { benchmark: 'MP3D-EQA',    sr: '—',         osr: '—',           ne: '—',            spl: '—',         ndtw: '—',        acc: '54.7±2.3' },
  { benchmark: 'OpenUAV-UM',  sr: '40.00±3.46', osr: '67.33±5.51', ne: '84.29±11.20',  spl: '30.37±2.23', ndtw: '—',        acc: '—' },
]
</script>

<template>
  <SectionWrapper id="results" title="Results" wide>
    <div class="table-card">
      <p class="table-caption">Uni-LaViRA results across six benchmarks (100-episode stratified subset, mean±std over three seeds).</p>
      <el-table :data="tableData" scrollbar-always-on>
        <el-table-column prop="benchmark" label="Benchmark" width="150" fixed />
        <el-table-column prop="sr" label="SR↑" min-width="120" />
        <el-table-column prop="osr" label="OSR↑" min-width="120" />
        <el-table-column prop="ne" label="NE↓" min-width="130" />
        <el-table-column prop="spl" label="SPL↑" min-width="120" />
        <el-table-column prop="ndtw" label="nDTW↑" min-width="120" />
        <el-table-column prop="acc" label="ACC↑" min-width="120" />
      </el-table>
    </div>
  </SectionWrapper>
</template>

<style scoped>
.table-card {
  background: var(--bg-card);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-md);
  padding: 20px;
  overflow: hidden;
}

.table-caption {
  font-size: 13px;
  color: var(--text-secondary);
  margin: 0 0 12px;
}

/* Table dark theme */
:deep(.el-table) {
  --el-table-bg-color: transparent;
  --el-table-tr-bg-color: transparent;
  --el-table-header-bg-color: var(--bg-secondary);
  --el-table-row-hover-bg-color: var(--bg-card-hover);
  --el-table-border-color: var(--border-subtle);
  --el-table-text-color: var(--text-primary);
  --el-table-header-text-color: var(--text-heading);
  --el-table-current-row-bg-color: var(--bg-card-hover);
  color: var(--text-primary);
  font-size: 14px;
}
:deep(.el-table th.el-table__cell) {
  background-color: var(--bg-secondary) !important;
  color: var(--text-heading);
  border-bottom-color: var(--border-subtle);
}
:deep(.el-table td.el-table__cell) {
  border-bottom-color: var(--border-subtle);
}
:deep(.el-table--enable-row-hover .el-table__body tr:hover > td.el-table__cell) {
  background-color: var(--bg-card-hover) !important;
}

/* Scrollbar */
:deep(.el-scrollbar__thumb) {
  background-color: var(--text-tertiary);
}

/* Fixed column shadow for dark theme */
:deep(.el-table__fixed::before) {
  background-color: var(--border-subtle) !important;
}
</style>
