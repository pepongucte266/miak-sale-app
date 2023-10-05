<style lang="scss" src="./PopupCustomerList.scss"></style>
<template>
  <q-dialog
    ref="dialogRef"
    persistent
    @hide="onDialogHide"
    :maximized="true"
    transition-hide="slide-left"
    transition-show="slide-right"
  >
    <q-layout view="hHr LpR lFf" container>
      <q-card class="dialog-customer-list-card hide-scrollbar q-pb-lg">
        <!-- dialog Header -->
        <q-card-section>
          <div class="row justify-between items-center q-mb-lg">
            <div class="row justify-between items-center">
              <q-icon
                name="keyboard_backspace"
                size="sm"
                @click="onDialogCancel"
              />
              <div class="text-h6 text-center q-ml-lg">Clients</div>
            </div>
            <!-- Thêm mới -->
            <q-btn
              no-wrap
              no-caps
              class="btn-add-new"
              label="Add new"
              @click="onOKClick"
              size="lg"
            />
          </div>
          <!-- Tìm kiếm -->
          <q-input
            outlined
            bottom-slots
            v-model="search"
            placeholder="Search"
            class="search-input"
            hide-bottom-space
            rounded
          >
            <template v-slot:prepend>
              <q-icon name="search" />
            </template>
          </q-input>
        </q-card-section>
        <q-card-section>
          <div v-for="char in CONSTANT.ListAtoZ" :key="char">
            <div
              v-if="
                customers.find(
                  (item) => item.CustomerName[0].toUpperCase() == char
                )
              "
            >
              <q-item-label class="q-pa-none" header>{{ char }}</q-item-label>
              <q-item
                class="contact-item q-my-md"
                v-for="(customer, index) in customers.filter(
                  (item) => item.CustomerName[0].toUpperCase() == char
                )"
                :key="index"
              >
                <q-item-section avatar>
                  <q-icon color="primary" text-color="white" name="people" />
                </q-item-section>
                <q-item-section>
                  <q-item-label class="ellipsis">{{
                    customer.CustomerName
                  }}</q-item-label>
                  <q-item-label caption lines="2">{{
                    customer.Tel
                  }}</q-item-label>
                </q-item-section>
                <q-item-section side top>
                  <q-btn size="12px" flat dense round icon="more_vert" />
                </q-item-section>
              </q-item>
            </div>
          </div>
        </q-card-section>
      </q-card>
      <!-- place QPageScroller at end of page -->
      <q-page-scroller
        position="bottom-right"
        :scroll-offset="100"
        :offset="[8, 8]"
        :expand="true"
      >
        <q-btn fab icon="keyboard_arrow_up" dense color="purpleapp" />
      </q-page-scroller>
    </q-layout>
  </q-dialog>
</template>

<script setup>
import { ref, reactive } from 'vue';
import { useDialogPluginComponent } from 'quasar';
import CONSTANT from 'src/common/constant';
defineEmits([...useDialogPluginComponent.emits]);

var search = ref('');
var customers = reactive([
  {
    CustomerName: 'VeheAeheAehe',
    Tel: '0981703726',
  },
  {
    CustomerName: 'Aeheasasdadas',
    Tel: '0981703726',
  },
  {
    CustomerName: 'Behehrhgsdfsd',
    Tel: '0981703726',
  },
  {
    CustomerName: 'CeasdhasdasdaseCeasdhasdasdase',
    Tel: '0981703726',
  },
  {
    CustomerName: 'AeheAeheAehe',
    Tel: '0981703726',
  },
  {
    CustomerName: 'Vũ Thái Sơn',
    Tel: '0981703726',
  },
  {
    CustomerName: 'Behehrhgsdfsd',
    Tel: '0981703726',
  },
  {
    CustomerName: 'CeasdhasdasdaseCeasdhasdasdase',
    Tel: '0981703726',
  },
  {
    CustomerName: 'AeheAeheAehe',
    Tel: '0981703726',
  },
  {
    CustomerName: 'eeheasasdadas',
    Tel: '0981703726',
  },
  {
    CustomerName: 'Behehrhgsdfsd',
    Tel: '0981703726',
  },
  {
    CustomerName: 'CeasdhasdasdaseCeasdhasdasdase',
    Tel: '0981703726',
  },
  {
    CustomerName: 'feheAeheAehe',
    Tel: '0981703726',
  },
  {
    CustomerName: 'Aeheasasdadas',
    Tel: '0981703726',
  },
  {
    CustomerName: 'mehehrhgsdfsd',
    Tel: '0981703726',
  },
  {
    CustomerName: 'CeasdhasdasdaseCeasdhasdasdase',
    Tel: '0981703726',
  },
]);

const { dialogRef, onDialogHide, onDialogOK, onDialogCancel } =
  useDialogPluginComponent();

function onOKClick() {
  onDialogOK();
}
</script>
