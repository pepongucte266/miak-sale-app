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
    <q-card class="dialog-customer-list-card hide-scrollbar">
      <!-- dialog Header -->
      <q-card-section>
        <div class="row justify-between items-center">
          <div class="row justify-between items-center">
            <q-icon
              name="keyboard_backspace"
              size="sm"
              @click="onDialogCancel"
            />
            <div class="text-h6 text-center q-ml-lg">Clients</div>
          </div>

          <q-btn
            no-wrap
            no-caps
            class="btn-add-new"
            label="Add new"
            @click="onOKClick"
            size="lg"
          />
        </div>
      </q-card-section>

      <!-- buttons example -->
      <q-card-actions
        class="fixed fixed-bottom bg-white add-invoice-card-action"
      >
        <div class="row justify-between items-center fit q-pa-md">
          <span class="save-as-draft">Save as draft</span>
          <q-btn
            no-wrap
            no-caps
            size="lg"
            class="btn-create"
            label="save"
            @click="onOKClick"
            disable
          />
        </div>
      </q-card-actions>
    </q-card>
  </q-dialog>
</template>

<script setup>
import { useDialogPluginComponent } from 'quasar';
defineEmits([...useDialogPluginComponent.emits]);

const { dialogRef, onDialogHide, onDialogOK, onDialogCancel } =
  useDialogPluginComponent();

function onOKClick() {
  onDialogOK();
}
</script>
