<template>
  <div class="row">
    <div class="panel panel-info">
      <div class="panel-heading">
        <h4>Lütfen Form'u Doldurun!</h4>
      </div>
    </div>
    <form>
      <div class="form-group">
        <label for="kullaniciadi">Ad</label>
        <input type="text" id="name" class="form-control" v-model="userData.name" />
      </div>
      <div class="form-group">
        <label for="kullanicisoyadi">Soyad</label>
        <input type="text" id="surname" class="form-control" v-model="userData.surname" />
      </div>
      <div class="form-group">
        <label for="tel">Telefon Numarası</label>
        <input type="number" id="telno" class="form-control" v-model="userData.telno" />
      </div>
      <div class="form-group">
        <label for="email">E-mail</label>
        <input type="text" id="email" class="form-control" v-model="userData.email" />
      </div>
      <div class="from-group">
        <label>Doğum Yeri</label>
        <select class="form-control" v-model="userData.selectedCity">
          <option
            :selected="city == 'İzmir'"
            v-for="(city,index) in userData.cities"
            :key="index"
          >{{ city }}</option>
        </select>
      </div>
      <br />
      <div class="from-group">
        <label>Doğum Tarihi</label>
        <br />
        <select v-model="userData.selectedDay">
          <option v-for="(day,index) in 31" :key="index">{{ day }}</option>
        </select>
        <label></label>
        <select v-model="userData.selectedMonth">
          <option
            v-for="(month,index) in userData.months"
            :key="index"
          >{{ month }}</option>
        </select>
        <label></label>
        <select v-model="userData.selectedYear">
          <option
            v-for="(year,index) in (121)"
            :key="index"
          >{{ year+1899 }}</option>
        </select>
      </div>
      <br />
      <div class="row">
        <div class="col-md-12 form-group">
          <label>Cinsiyet</label>
          <br />
          <label>
            <input type="radio" value="erkek" v-model="userData.gender" /> Erkek
          </label>
          <label>
            <input type="radio" value="kadin" v-model="userData.gender" /> Kadın
          </label>
        </div>
      </div>
      <div class="row">
        <div class="col-md-12">
          <button @click="submit" class="btn btn-primary">Gönder!</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
import { eventBus } from "./main";
export default {
  data() {
    return {
      userData: {
        name: null,
        surname: null,
        telno: null,
        email: null,
        password: null,
        gender: null,
        cities: [
          "İstanbul",
          "Ankara",
          "Niğde",
          "İzmir",
          "Antalya",
          "Eskişehir"
        ],
        selectedCity: "İzmir",
        months: [
          "January",
          "February",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December"
        ],
        selectedDay: "1",
        selectedMonth: "January",
        selectedYear: "2020"
      },
      isSubmited: false
    };
  },
  methods: {
    submit(userData) {
      this.isSubmited = true;
      this.$emit("data", this.userData);
      this.$emit("submit", this.isSubmited);
    }
  }
};
</script>

<style>
</style>