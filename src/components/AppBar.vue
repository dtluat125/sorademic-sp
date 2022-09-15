<template>
  <div class="app-bar-container">
    <el-row justify="space-between" align="middle" class="app-bar">
      <div>
        <el-space wrap :size="24">
          <Logo class="logo" />
          <el-input
            class="w-50 m-2 bar-input"
            size="large"
            placeholder="Tìm kiếm..."
            :prefix-icon="Search"
          />
        </el-space>
      </div>
      <div>
        <el-space wrap :size="24">
          <el-button class="noti-wrapper" :circle="true">
            <el-badge :value="123" class="noti-count" :max="999">
              <el-icon color=" #6D79E8" :size="23"><BellFilled /></el-icon>
            </el-badge>
          </el-button>
          <el-space wrap :size="4">
            <el-avatar :size="50" :src="avatar" />
            <span><strong>Phuong Anh</strong> </span>
          </el-space>
        </el-space>
      </div>
    </el-row>
  </div>
</template>

<script lang="ts" setup>
import { Logo, avatar } from "@/assets/images";
import { Search, BellFilled } from "@element-plus/icons-vue";
</script>

<style lang="scss">
.app-bar-container {
  background: rgba(255, 255, 255, 0.3);
  border-bottom: 1px solid rgba(245, 245, 249, 0.6);
  backdrop-filter: blur(26px);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  margin: auto;
  z-index: 10;
  width: 100vw;
}
.app-bar {
  height: 90px;
  max-width: 1440px;
  margin: 0px auto;
  padding: 0 72px;

  .bar-input {
    .el-input__wrapper {
      background-color: transparent;
      > span {
        color: #6d6f81;
      }
      > *::placeholder {
        color: #464962;
      }
      &:not(.is-focus) {
        box-shadow: none;
      }
    }
  }

  .noti-wrapper {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #f2f1ff;
    border: none;
  }
  .noti-count {
    .el-badge__content {
      background: #ff0e33;
      border: none;
      font-weight: 600;
      font-size: 9px;
      line-height: 16px;
    }
  }
}
</style>
