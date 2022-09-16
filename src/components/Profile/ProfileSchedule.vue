<template>
  <el-row class="info-block calendar-info" tag="div">
    <el-col>
      <el-row justify="space-between" align="middle">
        <div class="title">
          Tháng {{ currentMonth }},
          {{ currentYear }}
        </div>
        <el-button-group>
          <el-button
            :icon="ArrowLeftBold"
            @click="() => (weekNum = weekNum - 1)"
          />
          <el-button
            :icon="ArrowRightBold"
            @click="() => (weekNum = weekNum + 1)"
          />
        </el-button-group>
      </el-row>
    </el-col>
    <el-col class="calendar-picker">
      <el-row
        justify="space-between"
        :style="{ maxWidth: '400px', marginLeft: 'auto', marginRight: 'auto' }"
      >
        <!-- <el-space :size="16"> -->
        <el-row
          v-for="(date, index) in dayInWeekList"
          :key="index"
          class="week-cell"
        >
          <el-col class="week-day">
            {{ weekDays[moment(date).weekday()] }}</el-col
          >
          <el-col class="week-date">
            <el-button
              circle
              :class="{
                active: moment(date).date() - moment(selectedDate).date() === 0,
                'outside-month': moment(date).month() !== currentMonth,
              }"
              @click="handleSelectDate(date)"
              >{{ moment(date).date() }}</el-button
            >
          </el-col>
        </el-row>
        <!-- </el-space> -->
      </el-row>
    </el-col>
    <el-col>
      <el-space
        :size="0"
        direction="vertical"
        class="info-group lecture-list"
        fill
      >
        <el-space
          :size="12"
          v-for="(lecture, index) in lectureList"
          :key="index"
          alignment="center"
          :class="{ 'lecture-item': true, warning: lecture.upcoming }"
        >
          <div v-if="lecture.upcoming" class="icon-wrapper warning">
            <BellRedIcon />
          </div>
          <div class="icon-wrapper" v-else>
            <BellPurpleIcon />
          </div>
          <el-row class="flex-fill" style="row-gap: 12px">
            <el-col class="lecture-name">
              {{ lecture.name }}
            </el-col>
            <el-col>
              <el-row justify="space-between">
                <el-space :size="6" class="lecture-time" alignment="center">
                  <el-icon :size="13"><Clock /></el-icon> {{ lecture.time }}
                </el-space>
                <el-space class="lecture-type">
                  <VideoIcon />
                  <span>Lớp học online</span>
                </el-space>
              </el-row>
            </el-col>
          </el-row>
        </el-space>
      </el-space>
      <el-col>
        <el-button class="add-reminder">
          <el-space :size="8"> <RoundPlusIcon /> Thêm nhắc nhở </el-space>
        </el-button>
      </el-col>
    </el-col>
  </el-row>
</template>

<script lang="ts" setup>
import {
  BellRedIcon,
  BellPurpleIcon,
  VideoIcon,
  RoundPlusIcon,
} from "@/assets/images";
import { ArrowLeftBold, ArrowRightBold, Clock } from "@element-plus/icons-vue";
import { computed, ref } from "vue";
import moment from "moment";

const getWeekNum = (date: Date) => {
  return moment(date).week();
};
const getWeekDaysByWeekNumber = (weeknumber: number) => {
  const date = moment()
    .isoWeek(weeknumber || 1)
    .startOf("week");
  let weeklength = 7;
  const result = [];
  while (weeklength--) {
    result.push(date.toDate());
    date.add(1, "day");
  }
  return result;
};

const weekDays = ["T2", "T3", "T4", "T5", "T6", "T7", "CN"];
const weekNum = ref(getWeekNum(new Date()) - 1);
const dayInWeekList = computed(() => getWeekDaysByWeekNumber(weekNum.value));
const selectedDate = ref(new Date());

const lectureList = ref([
  { time: "12:00", name: "Lớp học Toán online", type: 1, upcoming: true },
  { time: "12:00", name: "Lớp học Toán online", type: 1, upcoming: false },
  { time: "12:00", name: "Lớp học Toán online", type: 1, upcoming: false },
  { time: "12:00", name: "Lớp học Toán online", type: 1, upcoming: false },
]);

const currentMonth = computed(() => moment(dayInWeekList.value[0]).month());
const currentYear = computed(() => moment(dayInWeekList.value[0]).year());
const handleSelectDate = (date: Date) => {
  //   const monthVal = moment(date).month();
  //   const weekVal = getWeekNum(date);
  //   if (monthVal !== moment(selectedDate.value).month()) weekNum.value = weekVal;
  selectedDate.value = date;
};
</script>

<style lang="scss">
.calendar-info {
  padding-bottom: 16px !important;
  .el-button-group {
    border-radius: 6px;
    .el-button {
      background: #f3f5fb;
      width: 28px;
      &:not(:active) {
        color: #130f26;
      }
      &:first-child {
        padding: 8px 10px 8px 15px;
      }
      &:nth-child(2) {
        padding: 8px 15px 8px 10px;
      }
    }
  }

  .calendar-picker {
    .week-cell {
      text-align: center;
      .week-day {
        color: $gray3h;
        font-size: 11px;
        line-height: 16px;
      }
      .week-date {
        button {
          width: 24px;
          height: 24px;
        }
        button span {
          color: $gray02;
          font-weight: 600;
          font-size: 11px;
          line-height: 16px;
        }

        button.active {
          span {
            color: white;
          }
          background: #6d79e8;
          box-shadow: 0px 4px 14px rgba(61, 92, 173, 0.28);
        }

        button:not(.active).outside-month {
          span {
            color: $gray3h;
          }
        }
      }
    }
  }
  .icon-wrapper {
    background: $violet03;
    &.warning {
      background: #fff1f4;
    }
    border-radius: 20px;
    width: 54px;
    height: 54px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .lecture-item {
    padding: 8px 0;
    border-bottom: 2px solid $gray05;
    &:last-child {
      border-bottom: none;
    }
    .el-space__item:nth-child(2) {
      flex: 1 1;
    }
    .lecture-name {
      font-weight: 500;
      font-size: 14px;
      line-height: 18px;
      color: $gray01;
    }

    .lecture-type {
      color: $gray3h;
      font-weight: 400;
      font-size: 13px;
      line-height: 16px;
    }
    .lecture-time {
      font-weight: 600;
      font-size: 13px;
      line-height: 16px;
      color: $gray3h;
      display: flex;
      align-items: center;
    }

    &.warning {
      .lecture-time {
        color: #ff0e33;
      }
    }
  }

  .add-reminder {
    width: 100%;
    height: 36px;
    color: $violet01;
    background-color: $violet03;
    border-radius: 6px;
    margin-top: 24px;
  }
}
</style>
