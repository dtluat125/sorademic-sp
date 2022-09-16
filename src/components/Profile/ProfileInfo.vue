<template>
  <el-row class="profile-info-container" :gutter="16">
    <el-col :md="6">
      <el-space :size="16" direction="vertical" fill class="block-group">
        <el-row class="info-block" tag="div">
          <el-col>
            <el-row justify="space-between" align="middle">
              <div class="title">Thông tin</div>
              <el-button link class="edit-outline-btn">
                <el-space :size="8">
                  <PenIcon />
                  <span> Chỉnh sửa</span>
                </el-space>
              </el-button>
            </el-row>
          </el-col>
          <el-col>
            <el-space :size="10" direction="vertical" class="info-group" fill>
              <el-row align="middle">
                <el-space :size="10" wrap>
                  <LocationIcon class="icon" />
                  <span class="label">Sống tại</span>
                  <span class="value">Hà Nội</span>
                </el-space>
              </el-row>
              <el-row align="middle">
                <el-space :size="10" wrap>
                  <LocationIcon class="icon" />
                  <span class="label">Sinh ngày</span>
                  <span class="value">20/10/1998</span>
                </el-space>
              </el-row>
              <el-row align="middle">
                <el-space :size="10" wrap>
                  <LocationIcon class="icon" />
                  <span class="label">Trường</span>
                  <span class="value">Trường THCS Nguyễn Du</span>
                </el-space>
              </el-row>
              <el-row align="middle">
                <el-space :size="10" wrap>
                  <LocationIcon class="icon" />
                  <span class="label">Môn học yêu thích</span>
                </el-space>
              </el-row>
              <el-row justify="center">
                <el-space :size="8">
                  <div class="tag">Toán</div>
                  <div class="tag">Vật lý</div>
                  <div class="tag">Hóa học</div>
                </el-space>
              </el-row>
            </el-space>
          </el-col>
        </el-row>

        <el-row class="info-block friend-list">
          <el-col>
            <el-row justify="space-between" align="middle">
              <div class="title">Danh sách bạn bè</div>
              <el-button link>
                <el-icon :size="15"><Search /></el-icon>
              </el-button>
            </el-row>
            <el-row
              ><span class="friend-count-text">12.000 bạn bè</span></el-row
            >
          </el-col>
          <el-col>
            <el-space
              :size="16"
              direction="vertical"
              class="friend-group w-100"
              fill
            >
              <el-row
                align="middle"
                v-for="(item, index) in [1, 2, 3, 4, 5]"
                :key="index"
              >
                <el-space :size="8" wrap>
                  <el-badge is-dot class="avatar-with-status">
                    <el-avatar :size="40" src="''">
                      <img
                        src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/82/190615_%E7%8E%8B%E6%99%B0_%E6%AD%A6%E6%B1%89%E4%B8%AA%E5%B7%A1_%EF%BC%881%EF%BC%89.jpg/1200px-190615_%E7%8E%8B%E6%99%B0_%E6%AD%A6%E6%B1%89%E4%B8%AA%E5%B7%A1_%EF%BC%881%EF%BC%89.jpg"
                        alt=""
                      />
                    </el-avatar>
                  </el-badge>
                  <el-row align="middle">
                    <el-col>
                      <span class="friend-name">Nguyễn Thúy An</span></el-col
                    >
                    <el-col
                      ><span class="friend-helper-text">
                        50 bạn chung
                      </span></el-col
                    >
                  </el-row>
                </el-space>
              </el-row>
              <el-row class="w-100">
                <el-button class="see-all w-100">Xem tất cả</el-button>
              </el-row>
            </el-space>
          </el-col>
        </el-row>
      </el-space>
    </el-col>
    <el-col :md="12"
      ><el-space :size="16" direction="vertical" fill class="block-group">
        <ProfileCreatePost />
      </el-space>
    </el-col>
    <el-col :md="6">
      <el-space :size="16" direction="vertical" fill class="block-group">
        <ProfileSchedule />
        <ProfileMayCare />
      </el-space>
    </el-col>
  </el-row>
</template>

<script lang="ts" setup>
import { LocationIcon, PenIcon } from "@/assets/images";
import ProfileSchedule from "@/components/Profile/ProfileSchedule.vue";
import { Search } from "@element-plus/icons-vue";
import ProfileMayCare from "@/components/Profile/ProfileMayCare.vue";
import ProfileCreatePost from "@/components/Profile/ProfileCreatePost.vue";
</script>

<style lang="scss" scoped>
@import "@/styles/custom-var.scss";
.profile-info-container {
  :deep(.el-button) {
    &:not(:active) {
      border-color: transparent;
    }
  }
}
.block-group {
  width: 100%;
  :deep(.info-block) {
    row-gap: 20px;
    background: #ffffff;
    box-shadow: 0px 5px 52px rgba(0, 0, 0, 0.04);
    border-radius: 16px;
    padding: 15px 20px 40px;
    min-width: 300px;
    .title {
      font-weight: 600;
      font-size: 20px;
      line-height: 32px;
    }
    .edit-outline-btn {
      color: $primaryColor;
      font-size: 15px;
      :deep(path),
      :deep(circle) {
        stroke: $primaryColor;
      }
    }
    .info-group {
      font-size: 14px;
      width: 100%;
      .label {
        color: $gray03;
      }
      .value {
        color: $gray01;
      }
    }
  }
  :deep(.tag) {
    background-color: $violet03;
    border-radius: 12px;
    font-weight: 500;
    font-size: 14px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: $violet01;
    padding: 6px 16px;
    white-space: nowrap;
  }
}

.friend-list {
  .friend-count-text {
    color: $violet01;
    font-size: 15px;
    line-height: 150%;
  }

  .friend-name {
    font-weight: 600;
    font-size: 13px;
    line-height: 16px;
    color: $gray01;
  }
  .friend-helper-text {
    color: #6d6f81;
    font-size: 11px;
    line-height: 16px;
  }

  .avatar-with-status {
    :deep(.el-badge__content) {
      background-color: $violet01;
      bottom: -3px;
      top: unset;
      right: 10px;
      height: 8px;
      width: 8px;
    }
  }
  .el-button.see-all {
    width: 100%;
    background: $violet03;
    border-radius: 6px;
    font-weight: 600;
    font-size: 15px;
    line-height: 160%;
    color: $violet01;
    &:not(:active) {
      border-color: transparent;
    }
    padding: 8px;
    height: auto;
  }
}
</style>
