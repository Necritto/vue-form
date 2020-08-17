<template>
  <div class="wrapper">
    <form class="form">
      <fieldset class="form__wrapp">
        <legend class="form__legend form__legend-main">Создание клиента</legend>
        <fieldset class="form__field">
          <legend class="form__legend">Основное</legend>
          <div class="req lastname">
            <label for="lastname">Фамилия:</label>
            <input
              type="text"
              id="lastname"
              placeholder="Введите фамилию"
              required
            />
            <span></span>
          </div>
          <div class="req firstname">
            <label for="firstname">Имя:</label>
            <input
              type="text"
              id="firstname"
              placeholder="Введите имя"
              required
            />
            <span></span>
          </div>
          <label for="middlename">Отчество:</label>
          <input type="text" id="middlename" placeholder="Введите отчество" />
          <div class="req birthday">
            <label for="birthday">Дата рождения:</label>
            <input
              type="date"
              id="birthday"
              placeholder="Введите дату рождения"
              required
            />
            <span></span>
          </div>
          <div class="req phone_num">
            <label for="phone_num">Номер телефона:</label>
            <input
              type="tel"
              id="phone_num"
              placeholder="7 *** ** ** ***"
              required
            />
            <span></span>
          </div>
          <label for="gender">Пол:</label>
          <select id="gender">
            <option value>не выбрано</option>
            <option value="2">Мужской</option>
            <option value="1">Женский</option>
          </select>
          <div class="req req-m group">
            <label for="group">Группа клиентов:</label>
            <select id="group" multiple required>
              <option value="1">VIP</option>
              <option value="2">Проблемные</option>
              <option value="3">ОМС</option>
            </select>
            <span></span>
          </div>
          <label for="doctor">Лечащий врач:</label>
          <select id="doctor">
            <option value>не выбрано</option>
            <option value="1">Иванов</option>
            <option value="2">Захаров</option>
            <option value="3">Чернышева</option>
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
          <div class="req city">
            <label for="city">Город:</label>
            <input type="text" id="city" placeholder="Укажите город" required />
            <span></span>
          </div>
          <label for="street">Улица:</label>
          <input type="text" id="street" placeholder="Укажите улицу" />
          <label for="house">Дом:</label>
          <input type="text" id="house" placeholder="Укажите номер дома" />
        </fieldset>
        <fieldset class="form__field">
          <legend class="form__legend">Паспорт</legend>
          <div class="req type_doc">
            <label for="type_doc">Тип документа:</label>
            <select id="type_doc" required>
              <option value>не выбрано</option>
              <option value="1">Паспорт</option>
              <option value="2">Свидетельство о рождении</option>
              <option value="3">Вод. удостоверение</option>
            </select>
            <span></span>
          </div>
          <label for="series">Серия:</label>
          <input type="text" id="series" placeholder="Введите серию" />
          <label for="number_doc">Номер:</label>
          <input type="text" id="number_doc" placeholder="Введите номер" />
          <label for="issued">Кем выдан :</label>
          <input type="text" id="issued" placeholder="Укажите кем выдан " />
          <div class="req date_of_issued">
            <label for="date_of_issued">Дата выдачи:</label>
            <input type="date" id="date_of_issued" required />
            <span></span>
          </div>
        </fieldset>
      </fieldset>
      <input type="submit" />
    </form>
  </div>
</template>

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
      display: none;
      position: absolute;
      top: 67%;
      left: 10%;
      color: red;
      border: 1px dotted red;
      padding: 5px;
    }

    .req-m {
      span {
        top: 73%;
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

    .req {
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

@media screen and (max-width: 900px) {
  .wrapper {
    width: 90%;
    padding: 0;

    .form {
      .form__field {
        width: 40%;

        input,
        select {
          width: 80%;
        }
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
