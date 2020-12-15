<template>
  <form action="" @submit.prevent="submit">
    <h2>Добавление клиента</h2>
    <br />
    <h3>Личные данные</h3>
    <div class="form-group">
      <label for="surname">Фамилия *</label>
      <input
        id="surname"
        type="text"
        v-model="surname"
        placeholder="Введите фамилию"
      />
      <span class="error" v-if="!$v.surname.required && $v.surname.$dirty"
        >Это поле обязательно для заполнения</span
      >
    </div>
    <div class="form-group">
      <label for="name">Имя *</label>
      <input id="name" type="text" v-model="name" placeholder="Введите имя" />
      <span class="error" v-if="!$v.name.required && $v.name.$dirty"
        >Это поле обязательно для заполнения</span
      >
    </div>
    <div class="form-group">
      <label for="third_name">Отчество *</label>
      <input
        id="third_name"
        type="text"
        v-model="otchestvo"
        placeholder="Введите отчество"
      />
      <span class="error" v-if="!$v.otchestvo.required && $v.otchestvo.$dirty"
        >Это поле обязательно для заполнения</span
      >
    </div>
    <div class="form-group">
      <label for="date_b">Дата рождения *</label>
      <input
        id="date_b"
        type="date"
        v-model="date"
        title="Выберите дату рождения"
      />
      <span class="error" v-if="!$v.date.required && $v.date.$dirty"
        >Это поле обязательно для заполнения</span
      >
    </div>

    <div class="form-group">
      <label for="phone">Номер телефона (начиная с 7)</label>
      <input type="text" v-model="phone" placeholder="Введите номер телефона" />
      <span class="error" v-if="!$v.phone.required && $v.phone.$dirty"
        >Это поле обязательно для заполнения</span
      >
      <span
        class="error"
        v-if="(!$v.phone.maxLength || !$v.phone.minLength) & $v.phone.$dirty"
        >Номер телефона должен состоять из 11 цифр
      </span>
      <span class="error" v-if="!$v.phone.checkPhone && $v.phone.$dirty"
        >Номер телефона должен начинать с цифры 7</span
      >
    </div>

    <span class="radio-group">
      <div>
        <input type="radio" id="one" value="male" v-model="gender" />
        <label for="one"> Мужчина</label>
      </div>
      <div>
        <input type="radio" id="two" value="female" v-model="gender" />
        <label for="two"> Женщина</label>
      </div>
    </span>

    <div class="form-group">
      <label for="c_group">Группы клиентов *</label>
      <select id="c_group" v-model="clients_group" multiple>
        <option>VIP</option>
        <option>Проблемные</option>
        <option>ОМС</option>
      </select>
      <span
        class="error"
        v-if="!$v.clients_group.required && $v.clients_group.$dirty"
        >Это поле обязательно для заполнения</span
      >
    </div>

    <div class="form-group">
      <label for="doctor">Лечащий врач</label>
      <select id="doctor" v-model="doctor">
        <option>Иванов</option>
        <option>Захаров</option>
        <option>Чернышева</option>
      </select>
    </div>

    <div class="checkbox-group">
      <input type="checkbox" id="checkbox" v-model="sendSMS" />
      <label for="checkbox"> Не отпарвлять СМС</label>
    </div>

    <h3>Данные о месте жительства</h3>
    <div class="form-group">
      <label for="index">Индекс</label>
      <input
        id="index"
        type="text"
        v-model="index"
        placeholder="Введите индекс"
      />
    </div>

    <div class="form-group">
      <label for="country">Страна</label>
      <input
        id="country"
        type="text"
        v-model="country"
        placeholder="Введите страну проживания"
      />
    </div>

    <div class="form-group">
      <label for="districts">Область</label>
      <input
        id="districts"
        type="text"
        v-model="districtL"
        placeholder="Введите область проживания"
      />
    </div>

    <div class="form-group">
      <label for="city">Город*</label>
      <input
        id="city"
        type="text"
        v-model="city"
        placeholder="Введите название города проживания"
      />
      <span class="error" v-if="!$v.city.required & $v.city.$dirty"
        >Это поле обязательно для заполнения</span
      >
    </div>

    <div class="form-group">
      <label for="street">Улица</label>
      <input
        id="street"
        type="text"
        v-model="street"
        placeholder="Введите название улицы проживания"
      />
    </div>

    <div class="form-group">
      <label for="building">Номер дома</label>
      <input
        id="building"
        type="text"
        v-model="building"
        placeholder="Введите номер дома"
      />
    </div>

    <h3>Документы</h3>
    <div class="form-group">
      <label for="type">Тип документа *</label>
      <select id="type" v-model="type">
        <option v-for="option in docs_options" :key="option.id">
          {{ option.label }}
        </option>
      </select>
      <span class="error" v-if="!$v.type.required & $v.type.$dirty"
        >Это поле обязательно для заполнения</span
      >
    </div>

    <div class="form-group">
      <label for="serial">Серия документа</label>
      <input
        id="serial"
        type="text"
        v-model="serial_number"
        placeholder="Введите серию документа"
      />
    </div>

    <div class="form-group">
      <label for="d_number">Номер документа</label>
      <input
        id="d_number"
        type="text"
        v-model="number"
        placeholder="Введите номер документа"
      />
    </div>
    <div class="form-group">
      <label for="department">Кем выдан документ</label>
      <input
        id="department"
        type="text"
        v-model="department"
        placeholder="Кем выдан документ"
      />
    </div>
    <div class="form-group">
      <label for="gettingDate">Дата выдачи *</label>
      <input
        id="gettingDate"
        type="date"
        v-model="gettingDate"
        placeholder="Когда выдан документ"
      />
      <span
        class="error"
        v-if="!$v.gettingDate.required & $v.gettingDate.$dirty"
        >Это поле обязательно для заполнения</span
      >
    </div>

    <button>Добавить клиента</button>
  </form>
</template>

<script>
import { required, minLength, maxLength } from "vuelidate/lib/validators";
import { checkPhone } from "../valiadtors/phone";
export default {
  data() {
    return {
      docs_options: [
        { id: 1, label: "Пасспорт" },
        { id: 2, label: "Вод. удостоверение" },
        { id: 3, label: "Свидетельство о рождении" },
      ],
      name: "",
      surname: "",
      otchestvo: "",
      date: "",
      gender: null,
      clients_group: [],
      doctor: null,
      sendSMS: false,
      phone: 7,
      index: null,
      country: null,
      districtL: null,
      city: null,
      street: null,
      building: null,
      type: [],
      serial_number: null,
      number: null,
      department: null,
      gettingDate: null,
    };
  },
  validations: {
    surname: {
      required,
    },
    name: {
      required,
    },
    otchestvo: {
      required,
    },
    date: {
      required,
    },
    phone: {
      required,
      minLength: minLength(11),
      maxLength: maxLength(11),
      checkPhone,
    },
    clients_group: {
      required,
    },
    city: {
      required,
    },
    type: {
      required,
    },
    gettingDate: {
      required,
    },
  },
  methods: {
    submit() {
      this.$v.$touch();
      if (this.$v.$invalid) {
        console.log(this.$v);
      } else {
        this.$emit("show");
        console.log("okay");
      }
    },
  },
};
</script>

<style lang="sass" scoped>
form
  margin: 3rem
  background-color: rgba(255, 255, 255, 1)
  border-radius: 5px
  padding: 2rem
  width: 500px
  display: flex
  flex-direction: column
  box-shadow: 0 3px 3px rgba(0,0,0,0.5)
  .radio-group
    margin-bottom: 1rem
    div
      display: inline-block
      margin-right: 1rem
  input
    border: 1px solid #95a5a6
    border-radius: 2px
    padding: 5px
    outline: none
    &:focus
      border: 2px solid #2980b9
      color: #2980b9
  select
    padding: 5px
    overflow: hidden
    outline: none
    &:focus
      border: 2px solid #2980b9
  button
    background-color: #0984e3
    font-size: 16px
    cursor: pointer
    border-radius: 2px
    margin: 0 auto
    padding: 10px
    width: 200px
    color: white
    border: none
    transition: 0.1s
    &:hover
      background-color: #2980b9
  h3
    margin-bottom: 1rem
  .form-group
    display: flex
    flex-direction: column
    margin-bottom: 1rem
  .checkbox-group
    margin-bottom: 1rem

.error
  color: red
</style>