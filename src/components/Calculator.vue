<script>
import { ref } from "vue";
export default {
  data() {
    return {
      current: "",
      previous: null,
      result: null,
      operatorClicked: false,
      operation: "",
    };
  },
  methods: {
    clearOperation() {
      this.current = "";
    },
    singOperation() {
      if (this.current.charAt(0) !== "-") {
        this.current = `-${this.current}`;
      } else {
        this.current = this.current.slice(1);
      }
    },
    percentOperation() {
      this.current = `${parseFloat(this.current) / 100}`;
    },
    writeNumber(number) {
      if (this.operatorClicked) {
        this.operatorClicked = false;
        // this.current = `${this.current}${this.previous}`;
        console.log(`${this.current}:CURRENT`);
      }
      this.current = `${this.current}${number}`;
      console.log(`${this.current}:CURRENT`);
      console.log(`${this.previous} :PREVIOUS`);
      console.log(
        `${this.current.charAt(
          this.current.length - 1
        )}: LAST NUMBER FROM CURRENT`
      );
    },
    //indexOf returns the position of the first occurence of a value in a string
    //when dot doesn't exist
    //probleme mit double operation
    doubleOperation() {
      if (this.current.indexOf(".") !== -1) {
        this.writeNumber(".");
      } else {
        this.current = '0';
        this.writeNumber(".");
      }
    },

    setPrevious() {
      this.previous = this.current.slice(0, -1);
      this.operatorClicked = true;
    },
    appendOperation() {
      this.current = `${this.current}${this.operation}`;
    },
    divideOperation() {
      this.operation = "/";
      this.appendOperation();
      this.setPrevious();
      this.result = (a, b) => b / a;
    },
    multiplyOperation() {
      this.operation = "*";
      this.appendOperation();
      this.setPrevious();
      this.result = (a, b) => b * a;
    },
    addOperation() {
      this.operation = "+";
      this.appendOperation();
      this.setPrevious();
      this.result = (a, b) => b + a;
    },
    subOperation() {
      this.operation = "-";
      this.appendOperation();
      this.setPrevious();
      this.result = (a, b) => b - a;
    },
    equalOperation() {
      this.current = `${this.result(
        parseFloat(this.current.charAt(this.current.length - 1)),
        parseFloat(this.previous)
      )}`;
      this.previous = null;
    },
  },
};
</script>

<template>
  <div class="calculator">
    <button class="display">{{ current || "0" }}</button>
    <button @click="clearOperation" class="item">AC</button>
    <button @click="singOperation" class="item">+/-</button>
    <button @click="percentOperation" class="item">%</button>
    <button @click="divideOperation" class="item operations">/</button>
    <button @click="writeNumber('7')" class="item">7</button>
    <button @click="writeNumber('8')" class="item">8</button>
    <button @click="writeNumber('9')" class="item">9</button>
    <button @click="multiplyOperation" class="item operations">x</button>
    <button @click="writeNumber('4')" class="item">4</button>
    <button @click="writeNumber('5')" class="item">5</button>
    <button @click="writeNumber('6')" class="item">6</button>
    <button @click="subOperation" class="item operations">-</button>
    <button @click="writeNumber('1')" class="item">1</button>
    <button @click="writeNumber('2')" class="item">2</button>
    <button @click="writeNumber('3')" class="item">3</button>
    <button @click="addOperation" class="item operations">+</button>
    <button @click="writeNumber('0')" class="item longer">0</button>
    <button @click="doubleOperation" class="item">.</button>
    <button @click="equalOperation" class="item operations">=</button>
  </div>
</template>

<style scoped>
.calculator {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(5rem, auto);
  font-size: 3rem;
  width: 40rem;
  margin: 0 auto;
  height: 50rem;
  /* shadow  */
}
.display {
  grid-column: 1/5;
  background-color: #333;
  color: white;
  font-style: normal;
  font-weight: 200;
}
.item {
  position: relative;
  background-color: #f2f2f2;
  color: black;
  text-align: center;
  border: solid 1px #999;
}
/* .item::after {
  content: "";
  position: absolute;
  width: 1px;
  height: 100%;
  right: 0;
  top: 0;
  background-color: blue;
  z-index: 1;
}
.item::before {
  content: "";
  position: absolute;
  width: 100%;
  height: 1px;
  left: 0;
  bottom: 0;
  background-color: blue;
  z-index: 1;
} */

.longer {
  grid-column: 1 / 3;
}

.operations {
  background-color: orange;
  color: white;
}
</style>