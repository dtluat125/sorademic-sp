<template>
  <el-row class="info-block news-info" tag="div">
    <el-col>
      <el-row justify="space-between" align="middle">
        <div class="title">Có thể bạn quan tâm</div>
      </el-row>
    </el-col>
    <el-col>
      <el-space :size="8" direction="vertical" class="info-group" fill>
        <el-space
          :size="10"
          alignment="center"
          v-for="(news, index) in newsList"
          :key="index"
          class="news-wrapper"
        >
          <el-space
            class="flex-fill"
            direction="vertical"
            :size="12"
            alignment="start"
            fill
          >
            <el-col class="news-name">{{ news.name }}</el-col>
            <el-col class="news-details d-flex align-items-center w-100">
              <el-space :size="4">
                <el-avatar :size="18">N</el-avatar>
                <span>{{ news.author }}</span>
              </el-space>
              <span class="ms-2">{{ news.postedDate }}</span>
            </el-col>
          </el-space>
          <div class="cover-image"></div>
        </el-space>
      </el-space>
    </el-col>
  </el-row>
</template>

<script lang="ts" setup="">
import { ref } from "vue";

const newsList = ref([
  {
    name: "Lớp học môn Toán nâng cao chất lượng cao năm 2022",
    author: "Nguyễn Vân Anh",
    postedDate: "7h trước",
    coverImage: "",
  },
  {
    name: "Lớp học môn Toán nâng cao chất lượng cao năm 2022",
    author: "Nguyễn Vân Anh",
    postedDate: "7h trước",
    coverImage: "",
  },
  {
    name: "Lớp học môn Toán nâng cao chất lượng cao năm 2022",
    author: "Nguyễn Vân Anh",
    postedDate: "7h trước",
    coverImage: "",
  },
  {
    name: "Lớp học môn Toán nâng cao chất lượng cao năm 2022",
    author: "Nguyễn Vân Anh",
    postedDate: "7h trước",
    coverImage: "",
  },
]);
</script>

<style lang="scss">
.news-info {
  .news-name {
    color: $gray01;
    font-weight: 500;
    font-size: 14px;
    line-height: 18px;
  }
  .news-details {
    span {
      font-weight: 400;
      font-size: 11px;
      line-height: 16px;
      color: $gray3h;
    }
  }
  .cover-image {
    width: 66px;
    height: 66px;
    border-radius: 14px;
    background-color: $gray05;
    margin-right: -10px;
  }
  .news-wrapper {
    padding: 8px 0 10px;
    justify-content: space-between;
  }
}
</style>
