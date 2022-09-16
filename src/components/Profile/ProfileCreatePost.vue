<template>
  <el-row class="info-block create-post" tag="div" style="row-gap: 15px">
    <el-col>
      <el-row align="middle">
        <el-avatar :size="40" class="mr-1" style="margin-right: 8px" />
        <div class="flex-fill">
          <el-input placeholder="Phuong Anh ơi, bạn đang nghĩ gì thế??" />
        </div>
      </el-row>
    </el-col>
    <el-col>
      <el-space class="button-group" :size="40" wrap>
        <el-button circle><DocumentIcon /></el-button>
        <el-button circle><ImageIcon /></el-button>
        <el-button circle><div class="icon-text-wrapper">?</div></el-button>
        <el-button class="post-button">Đăng ngay</el-button>
      </el-space>
    </el-col>
  </el-row>
</template>

<script lang="ts" setup>
import { DocumentIcon, ImageIcon } from "@/assets/images";
</script>
<style lang="scss" scoped>
.create-post {
  padding: 20px !important;
  :deep(.el-input__wrapper) {
    background: $gray05;
    padding: 12px 15px 14px;
    height: 40px;
  }
  :deep(input) {
    height: auto;
    ::placeholder {
      font-weight: 400;
      font-size: 14px;
      line-height: 20px;
      color: #6d6f81;
    }
  }
  .button-group {
    width: 100%;
    justify-content: flex-end;
    :deep(.el-button.is-circle) {
      width: 48px;
      height: 48px;
    }
    :deep(.el-space__item) {
      &:nth-child(1) {
        button:not(:active) {
          background-color: $green03;
        }
      }
      &:nth-child(2) {
        button:not(:active) {
          background-color: $red03;
        }
      }
      &:nth-child(3) {
        button:not(:active) {
          background-color: $violet03;
          font-weight: 700;
          font-size: 15px;
          line-height: 160%;
          color: $violet01;
        }
        margin-right: 60px !important;
      }
      &:last-child {
        margin-right: 0px !important;
      }
    }
    .post-button {
      background-color: $violet01;
      border-radius: 6px;
      color: #ffffff;
      font-weight: 600;
      font-size: 15px;
      height: 40px;
    }
  }
}
</style>
