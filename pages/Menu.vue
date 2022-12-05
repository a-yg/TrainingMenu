<script>
export default{
    data() {
        return {
            active: false
        }
    },
    // クリックしたらデータactiveの真偽値を変更
    methods: {
        click: function () {
            this.active = !this.active
        }
    },
}

</script>

<template>
<div>
  <div id="app">
    <button v-bind:class="{active}" v-on:click="click" class="menu-trigger">
      <span></span>
      <span></span>
      <span></span>
    </button>
  </div>
  <div v-show="active" class="list">
    <ul>
      <li>HOME</li>
      <li>MENU</li>
      <li>INFORMATION</li>
    </ul>
  </div>
  <div class="menu">
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  <h2>aaa</h2>
  </div>
</div>

</template>

<style scoped>
li {
  list-style: none;
  text-align: center;
  margin-bottom: 15px;
  text-decoration: underline;
}
ul {
  z-index: 9;
}
#app {
  position: fixed;
  top: 10px;
  left: 10px;
}
  .menu-trigger,
  .menu-trigger span {
    display: inline-block;
    transition: all 0.4s;
    box-sizing: border-box;
    position: relative;
    z-index: 100;
  }
  .menu-trigger {
    position: relative;
    width: 32px;
    height: 26px;
    background: none;
    border: none;
    appearance: none;
    cursor: pointer;
  }
  .menu-trigger span {
    position: absolute;
    left: 0;
    width: 100%;
    height: 4px;
    background-color: #172a22;
    border-radius: 4px;
  }
  .menu-trigger span:nth-of-type(1) {
    top: 0;
  }
  .menu-trigger span:nth-of-type(2) {
    top: 11px;
  }
  .menu-trigger span:nth-of-type(3) {
    bottom: 0;
  }
  .menu-trigger.active span:nth-of-type(1) {
    transform: translateY(11px) rotate(-45deg);
  }
  .menu-trigger.active span:nth-of-type(2) {
    opacity: 0;
  }
  .menu-trigger.active span:nth-of-type(3) {
    transform: translateY(-11px) rotate(45deg);
  }
</style>