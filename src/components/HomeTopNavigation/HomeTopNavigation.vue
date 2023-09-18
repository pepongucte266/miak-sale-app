<template>
  <q-header elevated class="home-top-header">
    <q-toolbar class="d-flex justify-between">
      <div class="home-top-header-left">
        <q-icon name="qr_code_scanner" size="sm" />
      </div>
      <div class="home-top-header-center">
        <q-icon name="chevron_left" size="sm" />
        2023
        <q-icon name="chevron_right" size="sm" />
      </div>
      <div class="home-top-header-right">
        <q-icon name="search" size="sm" />
        <q-icon name="notifications_none" size="sm" />
      </div>
    </q-toolbar>
    <q-toolbar
      class="home-month-picker scroll hide-scrollbar d-flex justify-around q-x-none"
    >
      <q-chip
        v-for="month in listMonth"
        :key="month.value"
        class="home-month-icon"
        :class="month.isSelected ? 'selected' : ''"
        :label="month.label"
        dark
        dense
      ></q-chip>
    </q-toolbar>
  </q-header>
</template>

<style lang="scss" scoped src="./HomeTopNavigation.scss"></style>
<script setup>
import { reactive } from 'vue';
var listMonth = reactive([
  { label: 'All', value: 'All', isSelected: true },
  { label: 'Jan', value: 'Jan', isSelected: false },
  { label: 'Feb', value: 'Feb', isSelected: false },
  { label: 'Mar', value: 'Mar', isSelected: false },
  { label: 'Apr', value: 'Apr', isSelected: false },
  { label: 'May', value: 'May', isSelected: false },
  { label: 'Jun', value: 'Jun', isSelected: false },
  { label: 'Jul', value: 'Jul', isSelected: false },
  { label: 'Aug', value: 'Aug', isSelected: false },
  { label: 'Sep', value: 'Sep', isSelected: false },
  { label: 'Oct', value: 'Oct', isSelected: false },
]);
</script>
