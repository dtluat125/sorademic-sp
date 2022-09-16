<template>
  <div class="profile-container">
    <el-row class="profile-header">
      <el-col
        class="background"
        :style="{ backgroundImage: `url(${defaultBg})` }"
      >
      </el-col>
      <el-row class="profile-info-wrapper">
        <el-col class="profile-info">
          <el-row
            justify="space-between"
            tag="div"
            :style="{ marginLeft: '-20px' }"
          >
            <el-space :size="16" alignment="flex-start">
              <el-row class="avatar-wrapper" justify="center" align="middle">
                <el-avatar :size="154" :src="profileImg">
                  <div v-if="!profileImg">NA</div>
                </el-avatar>
              </el-row>
              <el-row>
                <el-col class="name">Nguyễn Văn Anh Anh 12309</el-col>
                <div class="point">120 điểm</div>
              </el-row>
            </el-space>
            <div>
              <el-button class="edit-btn">
                <el-space :size="8">
                  <el-icon :size="22"><SmallPenIcon /></el-icon> Chỉnh sửa trang
                </el-space>
              </el-button>
            </div>
          </el-row>
          <el-row justify="center">
            <el-space class="nav-group" :size="20" wrap>
              <el-button
                :class="{ 'nav-button': true, active: activeTab === 1 }"
                @click="activeTab = 1"
              >
                <el-space :size="10">
                  <el-icon :size="20"><NoteIcon /></el-icon> Thông tin
                </el-space>
              </el-button>
              <el-button
                :class="{ 'nav-button': true, active: activeTab === 2 }"
                @click="activeTab = 2"
              >
                <el-space :size="10">
                  <el-icon :size="20"><SaveIcon /></el-icon> Lưu trữ
                </el-space>
              </el-button>
              <el-button
                :class="{ 'nav-button': true, active: activeTab === 3 }"
                @click="activeTab = 3"
              >
                <el-space :size="10">
                  <el-icon :size="20"><WorkIcon /></el-icon> Học tập
                </el-space>
              </el-button>
              <el-button
                :class="{ 'nav-button': true, active: activeTab === 4 }"
                @click="activeTab = 4"
              >
                <el-space :size="10">
                  <el-icon :size="20"><SettingIcon /></el-icon> Thiết lập
                </el-space>
              </el-button>
            </el-space>
            <el-button class="search-button">
              <el-icon :size="16">
                <Search />
              </el-icon>
            </el-button>
          </el-row>
        </el-col>
      </el-row>
    </el-row>
    <div class="profile-body">
      <ProfileInfo />
    </div>
  </div>
</template>

<script lang="ts" setup>
import {
  defaultBg,
  SmallPenIcon,
  NoteIcon,
  SaveIcon,
  WorkIcon,
  SettingIcon,
} from "@/assets/images";
import { Search } from "@element-plus/icons-vue";
import { ref } from "vue";
import ProfileInfo from "@/components/Profile/ProfileInfo.vue";
const profileImg = ref("");
const activeTab = ref(1);
</script>

<style lang="scss" scoped>
@import "@/styles/custom-var.scss";
.profile-container {
  .background {
    min-height: 400px;
    height: auto;
    background: #f2f1ff;
    background-repeat: no-repeat;
    background-position: 50% calc(50% + 45px);
  }

  .profile-info-wrapper {
    background-color: white;
    min-height: 200px;
    width: 100%;
  }

  .profile-body {
    max-width: 1440px;
    padding: 16px 72px;
    margin: 0 auto;
    box-sizing: border-box;
  }
  .profile-info {
    max-width: 1440px;
    padding: 16px 72px;

    margin: auto;
    box-shadow: 0px 1px 0px rgba(49, 51, 96, 0.1);
    > div:first-child {
      margin-bottom: 12px;
    }
    .el-avatar {
      background-color: #d9d8ff;
      font-weight: 500;
      font-size: 64px;
    }
    .avatar-wrapper {
      width: 170px;
      height: 170px;
      border-radius: 50%;
      background-color: white;
      transform: translateY(-60px);
    }
    .name {
      font-weight: 700;
      font-size: 32px;
      line-height: 48px;
    }
    .point {
      background: #fff1f4;
      border-radius: 12px;
      padding: 4px 12px;
      font-size: 15px;
      color: #ff647c;
    }

    .edit-btn {
      background-color: #6d79e8;
      border-radius: 6px;
      color: white;
      size: 15px;
      font-weight: 300;
      padding: 8px 15px;
      height: auto;
    }
  }

  .nav-group {
    position: relative;
  }

  .nav-button {
    padding: 6px 16px;
    height: auto;
    font-weight: 400;
    font-size: 17px;
    line-height: 24px;
    border-radius: 22px;
    background-color: $gray05;
    color: $gray03;

    :deep(path),
    :deep(circle) {
      stroke: $gray03;
    }
    border: none;

    &.active {
      background-color: $primaryColor;
      color: white;
      font-weight: 600;
      :deep(path),
      :deep(circle) {
        stroke: white;
      }
    }
  }

  .search-button {
    background-color: $gray05;
    border-radius: 8px;
    border: none;
    padding: 9px;
    position: absolute;
    top: 0;
    right: 16px;
  }
}
</style>
