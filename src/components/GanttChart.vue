<template>
  <div class="ganttChart">
      <Timeline></Timeline>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import { getTwoMonthsDays, Month } from '@/utils/date';
import Timeline from '@/components/Timeline.vue';

@Component({
    components: { Timeline },
})
export default class GanttChart extends Vue {
    private get months(): Month[] {
        return getTwoMonthsDays(this.startTime.getMonth(), this.startTime.getDate());
    }

    private get startTime(): Date {
        return new Date();
    }
}
</script>

<style scoped>
.ganttChart {
    max-width: 1300px;
    display: flex;
}

.ganttChart__month {
    list-style-type: none;
    display: flex;
    flex-direction: column;
    margin: 0;
    padding: 5px;
}

.ganttChart__month:nth-child(even) {
    border-left: 1px solid black;
    border-right: 1px solid black;
}

.month__days {
    display: flex;
}

.day {
    width: 20px;
    height: 20px;
    text-align: center;
}
</style>
