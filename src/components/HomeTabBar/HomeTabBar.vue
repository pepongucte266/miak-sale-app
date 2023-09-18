<style lang="scss" scoped src="./HomeTabBar.scss"></style>
<template>
  <q-footer elevated class="bg-white text-white">
    <q-toolbar style="height: 42px" class="d-flex justify-around">
      <q-btn
        :ripple="false"
        no-caps
        stack
        flat
        text-color="greyapp"
        icon="grid_view"
        label="Home"
        class="tab-bar-btn"
      />
      <q-btn
        :ripple="false"
        no-caps
        stack
        flat
        text-color="greyapp"
        icon="description"
        label="Docs"
        class="tab-bar-btn"
      />
      <q-btn
        round
        no-caps
        stack
        outline
        size="xl"
        icon="add"
        class="relative-position tab-bar-btn-add"
        @click="emit('openPopupAddInvoice')"
      />
      <q-btn
        :ripple="false"
        no-caps
        stack
        flat
        text-color="greyapp"
        icon="person"
        label="Profile"
        class="tab-bar-btn"
      />
      <q-btn
        :ripple="false"
        no-caps
        stack
        flat
        text-color="greyapp"
        icon="settings"
        label="settings"
        class="tab-bar-btn"
      />
    </q-toolbar>
  </q-footer>
</template>

<script setup lang="ts">
const emit = defineEmits(['openPopupAddInvoice']);
</script>
