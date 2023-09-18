<template>
  <HomeTopNavigation></HomeTopNavigation>
  <HomeTabBar @openPopupAddInvoice="openPopupAddInvoice"></HomeTabBar>
</template>
<style lang="scss"></style>
<script setup>
import HomeTabBar from 'src/components/HomeTabBar/HomeTabBar.vue';
import HomeTopNavigation from 'src/components/HomeTopNavigation/HomeTopNavigation.vue';
import PopupAddInvoice from 'src/components/PopupAddInvoice/PopupAddInvoice.vue';
import { useQuasar } from 'quasar';
const $q = useQuasar();
/**
 *Mô tả: Hàm hiển thị popup tạo hóa đơn
 *created by: VTSON 05-09-05
 */
function openPopupAddInvoice() {
  // show popup hiển thị hóa đơn
  $q.dialog({
    component: PopupAddInvoice,
  });
}
</script>
