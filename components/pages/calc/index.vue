<template>
  <div class="calc">
    <div class="calc__inner">
      <div class="calc__header calc-header">
        <h3 class="calc-header__name">Калькулятор</h3>
      </div>

      <div class="calc__result">
        <span> {{ getFixedLeftOperand }}</span>
        <span>{{ mathOperation }}</span>
        <span v-show="rightOperand">{{ getFixedRightOperand }}</span>
      </div>
      <div class="calc__action calc-action">
        <TableBox
          class="calc-action__item"
          :boxList="boxList"
          :resultData="getOperand"
          @onChangeResult="onChangeResult"
          @onClear="onClear()"
          @onDelete="onDelete()"
        />
        <TableBoxAside
          class="calc-action__aside"
          :boxListAsideData="boxListAside"
          @onSetMathOperation="onSetMathOperation"
        />
      </div>
    </div>
  </div>
</template>
<script>
import TableBox from "@/components/pages/calc/TableBox.vue";
import TableBoxAside from "@/components/pages/calc/TableBoxAside.vue";

export default {
  components: {
    TableBox,
    TableBoxAside,
  },
  data() {
    return {
      result: 0,
      leftOperand: 0,
      rightOperand: 0,
      mathOperation: "",

      boxList: [
        { id: 321, name: 1 },
        { id: 24242, name: 2 },
        { id: 4213, name: 3 },
        { id: 4675, name: 4 },
        { id: 8345, name: 5 },
        { id: 56236, name: 6 },
        { id: 642137, name: 7 },
        { id: 786238, name: 8 },
        { id: 4242459, name: 9 },
        { id: 6464210, name: 0 },
      ],

      boxListAside: [
        { id: 321, name: "/" },
        { id: 24242, name: "*" },
        { id: 4213, name: "+" },
        { id: 4675, name: "-" },
        { id: 8345, name: "=" },
      ],
    };
  },
  methods: {
    onClear() {
      this.leftOperand = 0;
      this.rightOperand = 0;
      this.mathOperation = "";
    },

    onDelete() {
      const delLeft = Number(String(this.leftOperand).slice(0, -1));
      const delRight = Number(String(this.rightOperand).slice(0, -1));
      if (this.mathOperation) {
        this.rightOperand = delRight;
      }
      if (!this.mathOperation) {
        this.leftOperand = delLeft;
      }
      if (!this.rightOperand) {
        this.mathOperation = "";
      }
    },

    onChangeResult(number) {
      this.mathOperation
        ? (this.rightOperand = number)
        : (this.leftOperand = number);
      this.result = number;
    },

    onSetMathOperation(operation) {
      if (this.rightOperand) {
        switch (this.mathOperation) {
          case "+":
            this.leftOperand += this.rightOperand;
            this.rightOperand = 0;
            this.mathOperation = "";
            break;

          case "-":
            this.leftOperand -= this.rightOperand;
            this.rightOperand = 0;
            this.mathOperation = "";
            break;

          case "*":
            this.leftOperand *= this.rightOperand;
            this.rightOperand = 0;
            this.mathOperation = "";
            break;

          case "/":
            this.leftOperand /= this.rightOperand;
            this.rightOperand = 0;
            this.mathOperation = "";
            break;
        }
      }
      if (operation === "=" && !this.rightOperand) return;
      this.mathOperation = operation;
    },
  },

  computed: {
    getOperand() {
      return this.mathOperation ? this.rightOperand : this.leftOperand;
    },

    getFixedLeftOperand() {
      return Math.floor(this.leftOperand * 100) / 100;
    },

    getFixedRightOperand() {
      return Math.floor(this.rightOperand * 100) / 100;
    },
  },
};
</script>
<style lang="scss">
.calc {
  // .calc__inner
  &__inner {
    padding: 10px;

    background-color: rgb(239, 237, 237);
    width: 350px;
    height: auto;
  }
  //   .calc__header
  &__header {
    justify-items: center;
  }
  //   .calc__result
  &__result {
    height: 60px;
    display: flex;
    justify-items: center;
    justify-content: flex-end;
    font-size: 34px;
  }
}
.calc-header {
  display: flex;
  justify-content: space-between;
  width: 100%;
  height: 35px;

  // .calc-header__name
  &__name {
    font-weight: 400;
  }
  // .calc-header__close-btn
  &__close-btn {
    cursor: pointer;
    transition: $transition-mod;
    font-weight: 700;

    // .calc-header__close-btn:hover
    &:hover {
      color: red;
    }
  }
}
.calc-action {
  display: grid;
  grid-template-columns: 4fr 1fr;
  gap: 4px;
}
</style>
