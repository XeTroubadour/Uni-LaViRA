<script>
import Title from './sections/Title.vue'
import Abstract from './sections/Abstract.vue'
import BibTeX from './sections/BibTeX.vue'
import Video from './sections/Video.vue'
import Table from './sections/Table.vue'
import FigureSection from './sections/FigureSection.vue'

export default {
  components: {
    Title,
    Abstract,
    BibTeX,
    Video,
    Table,
    FigureSection,
  }
}
</script>

<template>
  <Title/>
  <Video/>
  <Abstract/>
  <FigureSection id="overall" title="Overall" src="uni-lavira/teasor.png" alt="Overall architecture" />
  <FigureSection id="pipeline" title="Pipeline" src="uni-lavira/pipeline.png" alt="Pipeline" />
  <Table/>
  <BibTeX/>
</template>
