<template>
  <div class="wrapper">
    <form class="form" @submit.prevent="submitHandler()">
      <fieldset class="form__wrapp">
        <legend class="form__legend form__legend-main">Создание клиента</legend>
        <fieldset class="form__field">
          <legend class="form__legend">Основное</legend>

          <div class="validate" :class="{ invalidate: $v.lastnameData.$error }">
            <label for="lastname">Фамилия:</label>
            <input
              type="text"
              id="lastname"
              placeholder="Введите фамилию"
              required
              v-model.trim="lastnameData"
              @blur="$v.lastnameData.$touch()"
            />
            <span v-if="$v.lastnameData.$error">
              <template v-if="!$v.lastnameData.maxLength">
                Длина фамилии не должна превышать
                {{ $v.lastnameData.$params.maxLength.max }} символов
              </template>
              <template v-else-if="!$v.lastnameData.minLength">
                Длина фамилии не должна быть меньше
                {{ $v.lastnameData.$params.minLength.min }} символов
              </template>
              <template v-else-if="!$v.lastnameData.alpha"
                >Фамилия должна содержать только буквы</template
              >
              <template v-else>Фамилия обязательна для заполнения</template>
            </span>
          </div>

          <div
            class="validate"
            :class="{ invalidate: $v.firstnameData.$error }"
          >
            <label for="firstname">Имя:</label>
            <input
              type="text"
              id="firstname"
              placeholder="Введите имя"
              required
              v-model.trim="firstnameData"
              @blur="$v.firstnameData.$touch()"
            />
            <span v-if="$v.firstnameData.$error">
              <template v-if="!$v.firstnameData.maxLength">
                Длина имени не должна превышать
                {{ $v.firstnameData.$params.maxLength.max }} символов
              </template>
              <template v-else-if="!$v.firstnameData.minLength">
                Длина имени не должна быть меньше
                {{ $v.firstnameData.$params.minLength.min }} символов
              </template>
              <template v-else-if="!$v.firstnameData.alpha"
                >Имя должно содержать только буквы</template
              >
              <template v-else>Имя обязательно для заполнения</template>
            </span>
          </div>

          <label for="middlename">Отчество:</label>
          <input type="text" id="middlename" placeholder="Введите отчество" />

          <div class="validate" :class="{ invalidate: $v.birthdayDate.$error }">
            <label for="birthday">Дата рождения:</label>
            <input
              type="text"
              id="birthday"
              placeholder="ДД.ММ.ГГГГ"
              required
              v-model="birthdayDate"
              @blur="$v.birthdayDate.$touch()"
            />
            <span v-if="$v.birthdayDate.$error">Формат даты: ДД.ММ.ГГГГ</span>
          </div>

          <div class="validate" :class="{ invalidate: $v.phoneData.$error }">
            <label for="phone_num">Номер телефона:</label>
            <input
              type="text"
              id="phone_num"
              placeholder="7 *** ** ** ***"
              required
              v-model="phoneData"
              @blur="$v.phoneData.$touch()"
            />
            <span v-if="$v.phoneData.$error"
              >Формат номера: 7 *** ** ** ***</span
            >
          </div>

          <label for="gender">Пол:</label>
          <select id="gender">
            <option value>не выбран</option>
            <option value="2">Мужской</option>
            <option value="1">Женский</option>
          </select>

          <label for="group">Группа клиентов:</label>
          <select id="group" multiple required>
            <option
              :key="index"
              :value="group"
              v-for="(group, index) in groups"
              >{{ group }}</option
            >
          </select>

          <label for="doctor">Лечащий врач:</label>
          <select id="doctor">
            <option
              :key="index"
              :value="doctor"
              v-for="(doctor, index) in doctors"
              >{{ doctor }}</option
            >
          </select>

          <label class="sms">
            Не отправлять СМС
            <input type="checkbox" id="sms" />
          </label>
        </fieldset>

        <fieldset class="form__field">
          <legend class="form__legend">Адрес</legend>

          <label for="index">Индекс:</label>
          <input type="text" id="index" placeholder="Введите индекс" />

          <label for="country">Страна:</label>
          <input type="text" id="country" placeholder="Укажите страну" />

          <label for="region">Область:</label>
          <input type="text" id="region" placeholder="Укажите область" />

          <div class="validate" :class="{ invalidate: $v.cityData.$error }">
            <label for="city">Город:</label>
            <input
              type="text"
              id="city"
              placeholder="Укажите город"
              required
              v-model="cityData"
              @blur="$v.cityData.$touch()"
            />
            <span v-if="$v.cityData.$error">
              <template v-if="!$v.cityData.alpha"
                >Название города содержит только буквы</template
              >
              <template v-else>Указание города обязательно</template>
            </span>
          </div>

          <label for="street">Улица:</label>
          <input type="text" id="street" placeholder="Укажите улицу" />

          <label for="house">Дом:</label>
          <input type="text" id="house" placeholder="Укажите номер дома" />
        </fieldset>

        <fieldset class="form__field">
          <legend class="form__legend">Паспорт</legend>

          <label for="type_doc">Тип документа:</label>
          <select id="type_doc" required>
            <option :key="index" :value="type" v-for="(type, index) in types">{{
              type
            }}</option>
          </select>

          <label for="series">Серия:</label>
          <input type="text" id="series" placeholder="Введите серию" />

          <label for="number_doc">Номер:</label>
          <input type="text" id="number_doc" placeholder="Введите номер" />

          <label for="issued">Кем выдан :</label>
          <input type="text" id="issued" placeholder="Укажите кем выдан " />

          <div class="validate" :class="{ invalidate: $v.passportDate.$error }">
            <label for="date_of_issued">Дата выдачи:</label>
            <input
              type="text"
              placeholder="ДД.ММ.ГГГГ"
              id="date_of_issued"
              required
              v-model="passportDate"
              @blur="$v.passportDate.$touch()"
            />
            <span v-if="$v.passportDate.$error">Формат даты: ДД.ММ.ГГГГ</span>
          </div>
        </fieldset>
      </fieldset>
      <input type="submit" />
    </form>
  </div>
</template>

<script>
import { required, maxLength, minLength } from "vuelidate/lib/validators";

export default {
  data() {
    return {
      groups: ["VIP", "Проблемные", "ОМС"],
      doctors: ["не выбран", "Иванов", "Захаров", "Чернышева"],
      types: ["Паспорт", "Свидетельство о рождении", "Вод. удостоверение"],
      lastnameData: null,
      firstnameData: null,
      birthdayDate: null,
      phoneData: null,
      cityData: null,
      passportDate: null
    };
  },

  validations: {
    lastnameData: {
      required,
      maxLength: maxLength(20),
      minLength: minLength(2),
      alpha: val => /^[а-яёА-Яa-zA-Z]*$/i.test(val)
    },
    firstnameData: {
      required,
      maxLength: maxLength(10),
      minLength: minLength(2),
      alpha: val => /^[а-яёА-Яa-zA-Z]*$/i.test(val)
    },
    birthdayDate: {
      required,
      validDate: val =>
        /^(0?[1-9]|[12][0-9]|3[01]).(0?[1-9]|1[012]).((19|20)\d\d)$/.test(val)
    },
    phoneData: {
      required,
      validFormat: val => /(^[7]{1}\d{10}$)/.test(val)
    },
    cityData: {
      required,
      alpha: val => /^[а-яёА-Яa-zA-Z]*$/i.test(val)
    },
    passportDate: {
      required,
      validDate: val =>
        /^(0?[1-9]|[12][0-9]|3[01]).(0?[1-9]|1[012]).((19|20)\d\d)$/.test(val)
    }
  },

  methods: {
    submitHandler() {
      alert("Новый клиент успешно создан");
      location.reload();
    }
  }
};
</script>

<style lang="scss">
.wrapper {
  width: calc(100vw - 100px);
  height: 100%;
  background-color: #ffffff;
  padding: 30px;
  margin: 0 auto;
  border-radius: 10px;
  max-width: 1300px;

  .form {
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    input[type="submit"] {
      display: inline-block;
      background-color: #fe5f1e;
      color: #232323;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 1px;
      border-radius: 30px;
      padding: 10px 20px;
      min-width: 100px;
      height: 50px;
      text-align: center;
      cursor: pointer;
      transition: background-color 0.15s ease-in-out,
        border-color 0.15s ease-in-out;
      border: 1px solid transparent;

      &:hover {
        background-color: darken(#fe5f1e, 8%);
      }

      &:active {
        background-color: darken(#fe5f1e, 12%);
        transform: translateY(1px);
      }
    }

    input,
    select {
      width: 100%;
      height: 30px;
      padding: 5px;
      margin: 10px 10px 40px 20px;
      max-width: 250px;
    }

    span {
      position: absolute;
      top: 67%;
      left: 10%;
      color: #ff0000;
      padding: 5px;
      font-size: 14px;
    }

    .invalidate {
      input,
      select {
        border: 2px solid rgba(255, 0, 0, 0.6);
      }
    }

    input {
      color: #7b7b7b;
    }

    .sms {
      max-width: 220px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      height: 20px;
    }

    #sms {
      width: 0;
      margin: 0 auto;
    }

    #group {
      height: 55px;
    }

    .validate {
      display: flex;
      flex-direction: column;
      position: relative;
    }

    .form__wrapp {
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      width: 100%;
      border: 0 none;
    }

    .form__field {
      display: flex;
      flex-direction: column;
      width: 30%;
      margin: 20px 5px;
      padding: 10px 0 5px 10px;
      border: 2px dashed #181818;
      border-radius: 20px;
    }

    .form__legend {
      color: #181818;
      letter-spacing: 1%;
      text-transform: uppercase;
      font-weight: 800;
      font-size: 16px;
      margin: 0 30px;
    }

    .form__legend-main {
      margin: 0 auto;
      font-size: 20px;
    }
  }
}

@media screen and (max-width: 1165px) {
  .wrapper {
    .form {
      .form__field {
        input,
        select {
          width: 80%;
        }
      }
    }
  }
}

@media screen and (max-width: 900px) {
  .wrapper {
    width: 90%;
    padding: 0;

    .form {
      .form__field {
        width: 40%;
      }
    }
  }
}

@media screen and (max-width: 600px) {
  .wrapper {
    .form {
      .form__field {
        width: 70%;
      }
    }
  }
}
</style>
