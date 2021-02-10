<template>
  <div class="container">
    <div class="card">
      <h1>План cтановления Frontend-разработчика</h1>
      <div class="steps">
        <div class="steps-content">
          {{ activeStep.text }}
        </div>

        <ul class="steps-list">
          <li
            class="steps-item"
            v-for="(step, idx) in steps"
            :key="idx"
            :class="{
              active: idx === activeIndex,
              done: idx < activeIndex,
            }"
          >
            <span>{{ idx + 1 }}</span>
            {{ step.title }}
          </li>
        </ul>
      </div>
      <div v-if="activeFinish">
        <button class="btn" :disabled="prevDisabled" @click="prev">Назад</button>
        <button class="btn primary" @click="next">
          {{ lastStep ? "Закончить" : "Вперед" }}
        </button>
      </div>
      <div v-else>
        <button class="btn" @click="reset">Начать заного</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    activeIndex: 0,
    activeFinish: true,
    steps: [
      {
        title: "Основы HTML",
        text:
          "Изучите структуру HTML-документа, что такое теги и какие они есть, мета-теги, атрибуты, как добавлять изображения, создавать формы. Важными моментами в верстке является семантика и доступность.",
      },
      {
        title: "CSS",
        text:
          "Добавление стилей для элементов страницы. Изучаем блочную модель, позиционирование, каскадирование стилей, специфичность селекторов, псевдоэлементы, адаптивную верстку (для компьютеров, планшетов и телефонов). Учимся верстать современные макеты с помощью Flexbox и Grid.",
      },
      {
        title: "ЯП JavaScript",
        text:
          "Не путайте JavaScript с Java. Изучите основы языка: переменные, объекты, типы данных, функции, контекст и замыкания, классы. Сравните отличия спецификаций EcmaScript старых и новых версий. После понимания основ переходите к более сложным вещам: тонкостям асинхронного программирования (коллбеки, промисы, async-await) и выполнению запросов на сервер (XmlHttpRequest, Ajax, Fetch, Cookie).",
      },
      {
        title: "Изучение фреймворка",
        text:
          "React, Angular или Vue? На 2021 год основная борьба идет между этими библиотеками. Вы можете выбрать любую из них. Если вам симпатизирует какая-то конкретная компания, в которой вы хотели бы работать, можете выбрать используемый ими фреймворк.",
      },
    ],
  }),
  methods: {
    prev() {
      if (this.activeIndex !== 0) {
        this.activeIndex--;
      }
    },
    next() {
      if (this.activeIndex !== this.steps.length - 1) {
        this.activeIndex++;
      } else {
        this.activeFinish = false;
      }
    },
    reset() {
      this.activeIndex = 0;
      this.activeFinish = true;
    },
  },
  computed: {
    activeStep() {
      return this.steps[this.activeIndex];
    },
    lastStep() {
      return this.activeIndex === this.steps.length - 1;
    },
    prevDisabled() {
      return this.activeIndex === 0;
    },
  },
};
</script>

<style lang="scss">
.container {
  margin: 300px auto 0 auto;
  max-width: 1000px;
}

.card {
  padding: 1rem;
  border-radius: 10px;
  box-shadow: 2px 3px 10px rgba(0, 0, 0, 0.2);
  background: #fff;
}

.steps {
  &-content {
    margin-bottom: 1rem;
  }
  &-list {
    list-style: none;
    margin: 0;
    margin-bottom: 2rem;
    padding: 0;
    display: flex;
    justify-content: space-between;
  }
  &-item span {
    cursor: pointer;
    border-radius: 50%;
    padding: 0.75rem 1rem;
    font-size: 0.75rem;
    background: #cccccc;
  }
}

.btn {
  color: #42b983;
  position: relative;
  place-content: center;
  place-items: center;
  width: fit-content;
  border-radius: 99px;
  letter-spacing: 0.05em;
  border: 1px solid #42b983;
  text-decoration: none;
  text-transform: uppercase;
  margin-right: 10px;
  padding: 0.5rem 1.5rem;
  white-space: nowrap;
  font-weight: 700;
  outline: none;
  background: #fff;
  transition: all 0.22s;
}

.btn.primary {
  background: #42b983;
  color: #fff;
}

.steps-item.active span,
.steps-item.done span {
  background: #42b983;
}

.steps-item.active span {
  font-weight: bold;
  color: #ffffff;
}

.btn:hover {
  cursor: pointer;
  opacity: 0.8;
}

.btn:disabled {
  background: #eee!important;
  border: #ddd!important;
  color: #aaa!important;
  cursor: not-allowed;
}

</style>