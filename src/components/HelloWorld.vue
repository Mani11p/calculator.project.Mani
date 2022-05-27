<template>
  <div>
    <table id="calculator" dir="ltr" style="text-align: center; margin: auto">
      <tr>
        <!-- table row -->
        <td colspan="5">
          <!-- span = امتداد داشتن -->
          <input
            v-model="screen"
            dir="ltr"
            id="result"
            type="number"
            style="padding: 5px; font-weight: bold; text-align: right"
          />
        </td>
        <td>
          <!-- table data -->
        </td>
      </tr>
      <tr>
        <td><button @click="digit(7)" class="digit">7</button></td>
        <td><button @click="digit(8)" class="digit">8</button></td>
        <td><button @click="digit(9)" class="digit">9</button></td>
        <td><button @click="div" id="div">/</button></td>
        <td><button @click="clear" id="clear">C</button></td>
      </tr>
      <tr>
        <td><button @click="digit(4)" class="digit">4</button></td>
        <td><button @click="digit(5)" class="digit">5</button></td>
        <td><button @click="digit(6)" class="digit">6</button></td>
        <td><button @click="mul" id="mul">*</button></td>
        <td><button @click="remove" id="remove">del</button></td>
      </tr>
      <tr>
        <td><button @click="digit(1)" class="digit">1</button></td>
        <td><button @click="digit(2)" class="digit">2</button></td>
        <td><button @click="digit(3)" class="digit">3</button></td>
        <td><button @click="minus" id="minus">-</button></td>
        <td><button @click="mod" id="mod">%</button></td>
      </tr>
      <tr>
        <td colspan="2"><button @click="digit(0)" class="digit">0</button></td>
        <td><button @click="decimal" id="decimal">.</button></td>
        <td><button @click="sum" id="sum">+</button></td>
        <td><button @click="equal" id="equal">=</button></td>
      </tr>
    </table>
  </div>
</template>
<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      screen: "",
      Screen2: "",
      value1: Number,
      value2: Number,
      op: "",
    };
  },
  methods: {
    digit(n) {
      this.screen += n;
    },
    sum() {
      this.value1 = parseFloat(this.screen, 10);
      this.op = "+";
      this.screen = "";
    },
    mul() {
      this.value1 = parseFloat(this.screen, 10);
      this.op = "*";
      this.screen = "";
    },
    decimal() {
      this.screen = this.screen + "." + this.scr2;
    },
    minus() {
      this.value1 = parseFloat(this.screen, 10);
      this.op = "-";
      this.screen = "";
    },
    div() {
      this.value1 = parseFloat(this.screen, 10);
      this.op = "/";
      this.screen = "";
    },

    mod() {
      this.value1 = parseFloat(this.screen, 10);
      this.op = "%";
      this.screen = "";
    },
    remove() {
      this.screen = this.screen.slice(1);
    },
    clear() {
      this.screen = "";
    },

    equal() {
      switch (this.op) {
        case "+":
          this.value2 = parseFloat(this.screen, 10);
          this.screen = this.value2 + this.value1;
          break;
        case "-":
          this.value2 = parseFloat(this.screen, 10);
          this.screen = this.value1 - this.value2;
          break;
        case "/":
          this.value2 = parseFloat(this.screen, 10);
          this.screen = this.value1 / this.value2;
          break;
        case "%":
          this.value2 = parseFloat(this.screen, 10);
          this.screen = this.value1 % this.value2;
          break;
        case "*":
          this.value2 = parseFloat(this.screen, 10);
          this.screen = this.value1 * this.value2;
          break;
        case ".":
          this.screen = this.screen + "." + this.Screen2;
          break;
        case "del":
          this.screen = this.screen.slice(1);
          break;
        default:
          break;
      }
    },
  },
};
</script>
<style scoped>
button {
  border: 1.8px solid rgb(88, 88, 88);
  background-color: rgb(112, 0, 146);
  width: 100%;
  height: 50px;
  color: white;
  border-radius: 5px;
}
table {
  border: 1px solid rgb(243, 237, 237);
  background-color: rgb(14, 28, 75);
  width: 80%;
  padding: 4px;
  border-radius: 8px;
}
input {
  background-color: rgb(255, 255, 255);
  width: 95%;
  height: 46px;
}
</style>