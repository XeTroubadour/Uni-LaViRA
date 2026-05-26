<script lang="ts" setup>
import SectionWrapper from '../SectionWrapper.vue';
import { ref } from 'vue';

const activeTab = ref('vlnce');
const tabs = [
  { key: 'vlnce', label: 'VLN-CE (R2R & RxR)' },
  { key: 'openuav', label: 'OpenUAV (UM)' },
  { key: 'hm3d', label: 'HM3D / OVON / EQA' },
];
</script>

<template>
  <SectionWrapper id="results" title="Results" wide>
    <div class="table-center">
    <div class="table-card">
      <!-- Tab switcher -->
      <div class="tab-bar">
        <button
          v-for="t in tabs" :key="t.key"
          :class="['tab-btn', { active: activeTab === t.key }]"
          @click="activeTab = t.key"
        >{{ t.label }}</button>
      </div>

      <!-- Table 2: VLN-CE R2R & RxR -->
      <div v-show="activeTab === 'vlnce'" class="table-scroll">
        <table class="paper-table t-vlnce">
          <thead>
            <tr class="header-group">
              <th rowspan="2">Method</th>
              <th colspan="4" class="group-border">VLN-CE R2R Val-Unseen</th>
              <th colspan="4">VLN-CE RxR Val-Unseen</th>
            </tr>
            <tr>
              <th class="group-border-left">NE↓</th><th>OSR↑</th><th>SR↑</th><th>SPL↑</th>
              <th>NE↓</th><th>SR↑</th><th>SPL↑</th><th>nDTW↑</th>
            </tr>
          </thead>
          <tbody>
            <tr class="section-row"><td colspan="9">Supervised Learning (Training Method)</td></tr>
            <tr><td class="method">NaVid</td><td>5.47</td><td>49.1</td><td>37.4</td><td>35.9</td><td>8.41</td><td>34.5</td><td>23.8</td><td>—</td></tr>
            <tr><td class="method">Uni-NaVid</td><td>5.58</td><td>53.3</td><td>47.0</td><td>42.7</td><td>6.24</td><td>48.7</td><td>40.9</td><td>—</td></tr>
            <tr><td class="method">NaVILA</td><td>5.22</td><td>62.5</td><td>54.0</td><td>49.0</td><td>6.77</td><td>49.3</td><td>44.0</td><td>58.8</td></tr>
            <tr><td class="method">StreamVLN</td><td>4.98</td><td>64.2</td><td>56.9</td><td>51.9</td><td>6.22</td><td>52.9</td><td>46.0</td><td>61.9</td></tr>
            <tr><td class="method">NavFoM</td><td>5.01</td><td>64.9</td><td>56.2</td><td>51.2</td><td>5.51</td><td>57.4</td><td>49.4</td><td>60.2</td></tr>
            <tr><td class="method">JanusVLN</td><td>4.78</td><td>65.2</td><td>60.5</td><td>56.8</td><td>6.06</td><td>56.2</td><td>47.5</td><td>62.1</td></tr>
            <tr><td class="method">OmniNav</td><td>3.74</td><td>74.6</td><td>69.5</td><td>66.1</td><td>3.77</td><td>73.6</td><td>62.0</td><td>—</td></tr>
            <tr><td class="method">InternVLA-N1</td><td>4.83</td><td>63.3</td><td>58.2</td><td>54.0</td><td>5.91</td><td>53.5</td><td>46.1</td><td>65.3</td></tr>
            <tr><td class="method">ABot-N0</td><td>3.78</td><td>70.8</td><td>66.4</td><td>63.9</td><td>3.83</td><td>69.3</td><td>60.0</td><td>—</td></tr>
            <tr><td class="method">SPAN-Nav</td><td>4.07</td><td>75.3</td><td>66.3</td><td>59.3</td><td>4.20</td><td>69.7</td><td>60.1</td><td>67.9</td></tr>
            <tr class="section-row zeroshot"><td colspan="9">Zero-Shot (Training-Free)</td></tr>
            <tr><td class="method">InstructNav</td><td>6.89</td><td>47.0</td><td>31.0</td><td>24.0</td><td>—</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">Open-Nav</td><td>6.70</td><td>23.0</td><td>19.0</td><td>16.1</td><td>—</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">CA-Nav</td><td>7.58</td><td>48.0</td><td>25.3</td><td>10.8</td><td>10.4</td><td>19.0</td><td>6.0</td><td>13.5</td></tr>
            <tr><td class="method">SmartWay</td><td>7.01</td><td class="second">51.0</td><td>29.0</td><td>22.5</td><td>—</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">GC-VLN</td><td>7.30</td><td>41.8</td><td>33.6</td><td>16.3</td><td class="second">8.80</td><td class="second">33.8</td><td>13.8</td><td>—</td></tr>
            <tr><td class="method">LaViRA</td><td>6.54±0.27</td><td>48.7±2.1</td><td class="second">38.3±0.6</td><td>28.3±0.9</td><td>—</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">HiMemVLN</td><td>6.65</td><td>36.0</td><td>30.0</td><td>26.9</td><td>—</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">Three-Step Nav</td><td class="second">5.87</td><td>39.0</td><td>34.0</td><td class="second">29.1</td><td>9.21</td><td>22.0</td><td class="second">16.1</td><td class="second">45.7</td></tr>
            <tr class="row-ours"><td class="method">Uni-LaViRA (Ours)</td><td>3.66±0.26</td><td>73.7±1.2</td><td>60.7±2.1</td><td>47.7±1.6</td><td>6.48±0.14</td><td>51.3±2.3</td><td>34.0±1.9</td><td>53.7±0.6</td></tr>
          </tbody>
        </table>
      </div>

      <!-- Table 3: OpenUAV UM -->
      <div v-show="activeTab === 'openuav'" class="table-scroll">
        <table class="paper-table t-openuav">
          <thead>
            <tr class="header-group">
              <th rowspan="2">Method</th>
              <th colspan="4" class="group-border">Full</th>
              <th colspan="4" class="group-border">Easy</th>
              <th colspan="4">Hard</th>
            </tr>
            <tr>
              <th class="group-border-left">NE↓</th><th>OSR↑</th><th>SR↑</th><th>SPL↑</th>
              <th class="group-border-left">NE↓</th><th>OSR↑</th><th>SR↑</th><th>SPL↑</th>
              <th>NE↓</th><th>OSR↑</th><th>SR↑</th><th>SPL↑</th>
            </tr>
          </thead>
          <tbody>
            <tr class="section-row"><td colspan="13">Supervised Learning (Training Method)</td></tr>
            <tr><td class="method">Random Action</td><td>203</td><td>0.00</td><td>0.00</td><td>0.00</td><td>158</td><td>0.00</td><td>0.00</td><td>0.00</td><td>266</td><td>0.00</td><td>0.00</td><td>0.00</td></tr>
            <tr><td class="method">Fixed Action</td><td>180</td><td>2.61</td><td>0.52</td><td>0.39</td><td>133</td><td>4.28</td><td>0.89</td><td>0.67</td><td>248</td><td>0.25</td><td>0.00</td><td>0.00</td></tr>
            <tr><td class="method">CMA</td><td>142</td><td>10.0</td><td>2.30</td><td>2.16</td><td>102</td><td>14.3</td><td>3.57</td><td>3.33</td><td>197</td><td>4.03</td><td>0.50</td><td>0.50</td></tr>
            <tr><td class="method">TravelUAV</td><td>139</td><td>20.8</td><td>4.18</td><td>3.84</td><td>103</td><td>22.8</td><td>4.63</td><td>4.24</td><td>189</td><td>17.9</td><td>3.53</td><td>3.28</td></tr>
            <tr><td class="method">NavFoM</td><td>125</td><td>19.0</td><td>6.30</td><td>5.68</td><td>102</td><td>20.1</td><td>6.77</td><td>6.04</td><td>171</td><td>15.7</td><td>5.36</td><td>4.97</td></tr>
            <tr><td class="method">LongFly</td><td>108</td><td>30.3</td><td>11.3</td><td>9.32</td><td>78.6</td><td>34.3</td><td>13.0</td><td>10.3</td><td>148</td><td>24.9</td><td>9.02</td><td>7.98</td></tr>
            <tr><td class="method">AerialVLA</td><td>67.4</td><td>52.9</td><td>37.6</td><td>28.2</td><td>45.0</td><td>58.5</td><td>41.9</td><td>29.7</td><td>99.1</td><td>45.1</td><td>31.5</td><td>26.1</td></tr>
            <tr><td class="method">SpatialFly</td><td>104</td><td>30.4</td><td>13.6</td><td>11.1</td><td>72.9</td><td>34.3</td><td>16.1</td><td>12.7</td><td>146</td><td>25.1</td><td>10.2</td><td>9.04</td></tr>
            <tr class="section-row zeroshot"><td colspan="13">Zero-Shot (Training-Free)</td></tr>
            <tr class="row-ours"><td class="method">Uni-LaViRA (Ours)</td><td>84.29±11.20</td><td>67.33±5.51</td><td>40.00±3.46</td><td>30.37±2.23</td><td>77.05±7.40</td><td>68.75±3.61</td><td>39.58±2.09</td><td>27.95±3.18</td><td>90.96±14.88</td><td>66.03±7.83</td><td>40.38±8.21</td><td>32.60±5.94</td></tr>
          </tbody>
        </table>
      </div>

      <!-- Table 4: HM3D-v2, HM3D-OVON, MP3D-EQA -->
      <div v-show="activeTab === 'hm3d'" class="table-scroll">
        <table class="paper-table t-hm3d">
          <thead>
            <tr class="header-group">
              <th rowspan="2">Method</th>
              <th colspan="2" class="group-border">HM3D-v2</th>
              <th colspan="2" class="group-border">HM3D-OVON</th>
              <th>EQA</th>
            </tr>
            <tr>
              <th class="group-border-left">SR↑</th><th>SPL↑</th>
              <th class="group-border-left">SR↑</th><th>SPL↑</th>
              <th>ACC↑</th>
            </tr>
          </thead>
          <tbody>
            <tr class="section-row"><td colspan="6">Supervised Learning (Training Method)</td></tr>
            <tr><td class="method">EQA(w/GT)</td><td>—</td><td>—</td><td>—</td><td>—</td><td>46.0</td></tr>
            <tr><td class="method">DD-PPO</td><td>27.9</td><td>14.2</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">Habitat-Web</td><td>57.6</td><td>23.8</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">PIRLNav</td><td>70.4</td><td>34.1</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">OVRL-v2</td><td>64.7</td><td>28.1</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">NaviLLM</td><td>—</td><td>—</td><td>—</td><td>—</td><td>44.5</td></tr>
            <tr><td class="method">DAgRL+OD</td><td>—</td><td>—</td><td>37.1</td><td>19.9</td><td>—</td></tr>
            <tr><td class="method">Uni-NaVid</td><td>73.7</td><td>37.1</td><td>39.5</td><td>19.8</td><td>47.3</td></tr>
            <tr><td class="method">NavFoM</td><td>—</td><td>—</td><td>43.6</td><td>31.3</td><td>—</td></tr>
            <tr><td class="method">FiLM-Nav</td><td>77.0</td><td>41.3</td><td>40.8</td><td>24.4</td><td>—</td></tr>
            <tr><td class="method">OmniNav</td><td>—</td><td>—</td><td>59.2</td><td>33.2</td><td>—</td></tr>
            <tr><td class="method">ABot-N0</td><td>—</td><td>—</td><td>54.0</td><td>30.5</td><td>—</td></tr>
            <tr class="section-row zeroshot"><td colspan="6">Zero-Shot (Training-Free)</td></tr>
            <tr><td class="method">L3MVN</td><td>54.2</td><td>25.5</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">VLFM</td><td>62.6</td><td>31.0</td><td class="second">38.5</td><td class="second">22.2</td><td>—</td></tr>
            <tr><td class="method">OpenFMNav</td><td>54.9</td><td>24.4</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">InstructNav</td><td>58.0</td><td>20.9</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">SG-Nav</td><td>54.0</td><td>24.9</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">ApexNav</td><td class="second">76.2</td><td>38.0</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">DSCD-Nav</td><td>73.0</td><td class="second">38.7</td><td>—</td><td>—</td><td>—</td></tr>
            <tr><td class="method">ReMemNav</td><td>67.8</td><td>36.6</td><td>—</td><td>—</td><td>—</td></tr>
            <tr class="row-ours"><td class="method">Uni-LaViRA (Ours)</td><td>77.7±2.1</td><td>46.1±1.8</td><td>60.0±6.1</td><td>40.5±1.1</td><td>54.7±2.3</td></tr>
          </tbody>
        </table>
      </div>

    </div>
    </div>
  </SectionWrapper>
</template>

<style scoped>
.table-card {
  display: inline-block;
  background: var(--bg-card);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-md);
  padding: 20px;
  max-width: 100%;
}

.table-center {
  display: flex;
  justify-content: center;
}

/* Tab bar */
.tab-bar {
  display: flex;
  justify-content: center;
  gap: 4px;
  margin-bottom: 16px;
  border-bottom: 1px solid var(--border-subtle);
  padding-bottom: 12px;
}
.tab-btn {
  padding: 6px 16px;
  font-size: 14px;
  color: var(--text-secondary);
  background: transparent;
  border: none;
  border-radius: var(--radius-sm);
  cursor: pointer;
  transition: all var(--transition-fast);
}
.tab-btn:hover {
  color: var(--text-primary);
}
.tab-btn.active {
  color: var(--accent);
  background: var(--accent-subtle);
}

/* Scroll wrapper */
.table-scroll {
  overflow-x: auto;
}

/* =============================================
   Paper-style booktabs table (dark theme)
   ============================================= */
.paper-table {
  width: auto;
  margin: 0 auto;
  border-collapse: collapse;
  border-spacing: 0;
  font-size: 13px;
  line-height: 1.4;
  color: var(--text-primary);
  white-space: nowrap;
  border: none;
}

/* All cells: reset */
.paper-table th,
.paper-table td {
  padding: 5px 10px;
  text-align: center;
  border: none;
  background: transparent;
}

/* toprule: thick line at very top of table */
.paper-table {
  border-top: 2px solid rgba(255,255,255,0.6);
}

/* midrule: thin line below thead */
.paper-table thead {
  border-bottom: 1px solid rgba(255,255,255,0.4);
}

/* bottomrule: thick line at very bottom */
.paper-table tbody {
  border-bottom: 2px solid rgba(255,255,255,0.6);
}

/* Header cells */
.paper-table th {
  font-weight: 600;
  color: var(--text-heading);
}

/* Method column: left-aligned + right vertical line (LaTeX l|) */
.paper-table thead tr:first-child th:first-child {
  text-align: left;
  border-right: 1px solid rgba(255,255,255,0.25);
}
.paper-table td.method {
  text-align: left;
  font-weight: 500;
  border-right: 1px solid rgba(255,255,255,0.25);
}

/* Vertical lines between benchmark groups (LaTeX |) — headers */
.group-border {
  border-left: 1px solid rgba(255,255,255,0.25);
}
.group-border-left {
  border-left: 1px solid rgba(255,255,255,0.25);
}
/* Vertical lines — data rows: VLN-CE table (l|cccc|cccc) col 2 and 6 */
.paper-table.t-vlnce td:nth-child(2),
.paper-table.t-vlnce td:nth-child(6) {
  border-left: 1px solid rgba(255,255,255,0.25);
}
/* OpenUAV table (l|cccc|cccc|cccc) col 2, 6, 10 */
.paper-table.t-openuav td:nth-child(2),
.paper-table.t-openuav td:nth-child(6),
.paper-table.t-openuav td:nth-child(10) {
  border-left: 1px solid rgba(255,255,255,0.25);
}
/* HM3D table (l|cc|cc|c) col 2, 4, 6 */
.paper-table.t-hm3d td:nth-child(2),
.paper-table.t-hm3d td:nth-child(4),
.paper-table.t-hm3d td:nth-child(6) {
  border-left: 1px solid rgba(255,255,255,0.25);
}

/* Section header rows (rowcolor in LaTeX) — midrule above, no vertical lines */
.section-row td {
  padding: 5px 10px;
  font-weight: 600;
  font-size: 12px;
  text-align: center;
  color: var(--text-secondary);
  background: rgba(255, 255, 255, 0.05);
  border-top: 1px solid rgba(255,255,255,0.4);
  border-left: none !important;
  border-right: none !important;
  border-bottom: none !important;
}
.section-row.zeroshot td {
  background: rgba(100, 200, 255, 0.06);
}

/* Second-best: underline */
.second {
  text-decoration: underline;
}

/* Ours row: accent color */
.row-ours td {
  color: var(--accent);
  font-weight: 600;
}
.row-ours td.method {
  font-weight: 700;
}

/* Hover */
.paper-table tbody tr:not(.section-row):hover td {
  background: rgba(255, 255, 255, 0.03);
}
.paper-table tbody tr.row-ours:hover td {
  background: rgba(207, 115, 89, 0.08);
}
</style>
