<style lang="scss" src="./PopupAddInvoice.scss"></style>
<template>
  <q-dialog
    class="dialog-add-invoice"
    ref="dialogRef"
    @hide="onDialogHide"
    :maximized="true"
    transition-hide="slide-down"
    transition-show="slide-up"
  >
    <q-card class="dialog-add-invoice-card hide-scrollbar">
      <!-- dialog Header -->
      <q-card-section>
        <q-icon
          class="fixed-top-left absolute-top-left q-pt-md q-pl-md"
          name="close"
          size="sm"
          @click="onDialogCancel"
        />
        <div class="text-h6 text-center">Create a new invoice</div>
      </q-card-section>

      <!-- Thông tin địa chỉ -->
      <q-card-section>
        <div class="add-invoice-block invoice-infomation q-pa-md">
          <div class="row items-center">
            <span class="number-icon">1</span>
            <span class="title"> Invoice Information </span>
          </div>
          <div class="invoice-date">#27 - 16/09/2023</div>
        </div>
      </q-card-section>

      <!-- Thoong tin khách hàng -->
      <q-card-section>
        <div
          class="add-invoice-block client-data q-pa-md"
          :class="!isShowClientData ? 'row' : ''"
        >
          <div class="row items-center justify-between full-width">
            <div class="row items-center text-h6">
              <span
                class="number-icon"
                :class="!isShowClientData ? 'active' : ''"
                @click="isShowClientData = !isShowClientData"
                >2</span
              >
              <span class="title">Client Data</span>
            </div>
            <q-btn
              no-wrap
              no-caps
              align="around"
              class="btn-contacts"
              rounded
              icon="people"
              size="sm"
              label="Contacts"
              @click="openPopupCustomerList"
            />
          </div>
          <div v-show="isShowClientData" class="client-data-body q-pt-lg">
            <div class="row no-wrap justify-between q-pb-lg">
              <q-input
                outlined
                v-model="invoiceData.CustomerName"
                label="Customer name"
                stack-label
                dense
                class="client-data-input col-12"
              />
            </div>
            <div class="row no-wrap justify-between q-pb-lg">
              <q-input
                outlined
                v-model="invoiceData.Tel"
                label="Phone number"
                stack-label
                dense
                class="client-data-input col-12"
              />
            </div>
            <div class="row no-wrap justify-between q-pb-lg">
              <q-input
                outlined
                v-model="invoiceData.CompanyName"
                label="Company name"
                stack-label
                dense
                class="client-data-input col-8"
              />
              <q-input
                outlined
                dense
                v-model="invoiceData.CompanyType"
                class="client-data-input col-3"
                label="Type"
                stack-label
              />
            </div>
            <div class="row no-wrap justify-between q-pb-lg">
              <q-input
                outlined
                v-model="invoiceData.VATID"
                label="VAT ID"
                stack-label
                dense
                class="client-data-input col-12"
              />
            </div>
            <div class="row no-wrap justify-between q-pb-lg">
              <q-input
                outlined
                v-model="invoiceData.Address"
                label="Address"
                stack-label
                dense
                autogrow
                maxlength="300"
                class="client-data-input hehe col-12"
              />
            </div>
          </div>
          <div v-show="isShowClientData" class="client-data-footer">
            <div class="row justify-between">
              <q-checkbox
                indeterminate-value="false"
                v-model="isSaveContact"
                label="Save contact"
                size="sm"
                class="ckb-save-contact"
              />
              <q-btn
                no-wrap
                no-caps
                size="lg"
                class="btn-continue"
                label="Continue"
              />
            </div>
          </div>
          <div v-if="isShowClientData" class="row justify-center items-center">
            <q-btn
              flat
              :ripple="false"
              icon="expand_less"
              @click="isShowClientData = false"
            />
          </div>
        </div>
      </q-card-section>

      <!-- Thông tin hàng hóa và thanh toán -->
      <q-card-section>
        <div class="add-invoice-block invoice-infomation q-pa-md">
          <div class="row items-center">
            <span class="number-icon">3</span>
            <span class="title"> Items </span>
          </div>
          <span class="text-red">Add Items Now</span>
        </div>
      </q-card-section>

      <!-- Thông tin hàng hóa và thanh toán -->
      <q-card-section>
        <div class="add-invoice-block invoice-infomation payment-info q-pa-md">
          <div class="row items-center">
            <span class="number-icon">4</span>
            <span class="title">Payment </span>
          </div>
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
            label="Create"
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
import { ref, reactive } from 'vue';
import { useQuasar } from 'quasar';
// import component
import PopupCustomerList from 'src/components/PopupCustomerList/PopupCustomerList.vue';

// const props = defineProps({
//   // ...your custom props
// });

defineEmits([...useDialogPluginComponent.emits]);

const $q = useQuasar();
const { dialogRef, onDialogHide, onDialogOK, onDialogCancel } =
  useDialogPluginComponent();

var invoiceData = reactive({
  CustomerName: 'Vũ Thái Sơn',
  Tel: '0981703726',
  CompanyName: 'MISA JSC',
  VATID: '09876564535',
  Address: 'N03-T1 Ngoại Giao Đoàn',
  CompanyType: 'Service',
});
/**Có lưu thông tin khách hàng hay không */
var isSaveContact = ref(true);
/**Có hiển thị thông tin kh hay không */
var isShowClientData = ref(true);
// this is part of our example (so not required)
function onOKClick() {
  onDialogOK();
}

function openPopupCustomerList() {
  $q.dialog({
    component: PopupCustomerList,
  });
  return true;
}
</script>
