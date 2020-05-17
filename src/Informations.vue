<template>
  <div>
    <form>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <app-Form @submit="isSubmited=$event" @data="userData=$event" v-if="!isSubmited"></app-Form>
        </div>
      </div>
    </form>
    <hr />
    <div class="row" v-if="isSubmited">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <div class="panel panel-info">
          <div class="panel-heading">
            <h4>Girdiğiniz Bilgier</h4>
          </div>
          <div class="panel-body">
            <p>Ad: {{userData.name}}</p>
            <p>Soyad: {{userData.surname}}</p>
            <p>Telefon Numarası: {{userData.telno}}</p>
            <p>E-mail: {{userData.email}}</p>
            <p>Doğum Yeri: {{userData.selectedCity}}</p>
            <p>Doğum Tarihi: {{userData.selectedDay}} {{userData.selectedMonth}} {{userData.selectedYear}}</p>
            <p>Cinsiyet: {{userData.gender}}</p>

            <div class="row">
              <div class="col-md-12">
                <button @click="isSubmited = false" class="btn btn-primary">Yeni Form Doldur!</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Form from "./Form";
import { eventBus } from "./main";
export default {
  components: {
    appForm: Form
  },
  data() {
    return {
      userData: {
        name: "",
        email: "",
        password: "",
        gender: ""
      },
      isSubmited: false
    };
  }
};
</script>

<style>
</style>