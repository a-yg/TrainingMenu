<script>
export default{
    data() {
        return {
            active: false,
            messsage: 'マウスhover',
            hoverFlag: false,
            isOpen: false,
            items: [
              {
                url: "#",
                name: "Home"
              },
              {
                url: "#",
                name: "About"
              },
              {
                url: "#",
                name: "Service",
                children: [
                  {
                    url: "#",
                    name: "Service1"
                  },
                  {
                    url: "#",
                    name: "Service2"
                  },
                  {
                    url: "#",
                    name: "Service3"
                  }
                ]
              },
              {
                url: "#",
                name: "Url"
              },
            ]
        }
    },
    // クリックしたらデータactiveの真偽値を変更
    methods: {
        click: function () {
            this.active = !this.active
        },
        mouseOverAction(){
          this.hoverFlag = true
        },
        mouseLeaveAction() {
          this.hoverFlag = false
        },
        mouseover() {
          this.isOpen = true
        },
        mouseleave() {
          this.isOpen = false
        },
        // 「behavior」はアニメーションの速度
        // smooth・instant・auto
        scrollTop() {
          window.scrollTo({
            top: 0,
            behavior: "smooth"
          })
        }
    },
}

</script>

<template>
<div>
  <div id="app">
    <button :class="{active}" v-on:click="click" class="menu-trigger">
      <span></span>
      <span></span>
      <span></span>
    </button>
  </div>

  <header>
    <nav id="nav">
      <h1>Site Title</h1>
      <ul>
        <li v-for="item in items" :key="item">
          <a :href="item.url" v-if="!item.children">
            {{ item.name }}
          </a>
          <span
            v-else
            @mouseover="mouseover"
            @mouseleave="mouseleave">
            {{ item.name }}
            
            <ul class="dropdown" :class="{isOpen}">
              <li v-for="child in item.children" :key="child">
                <a :href="child.url">{{ child.name }}</a>
              </li>
            </ul>
          </span>
        </li>
      </ul>
    </nav>
  </header>

  <div v-show="active" class="list">
    <ul>
      <li><a href="#home">HOME</a></li>
      <li><a href="#menu">MENU</a></li>
      <li><a href="#information">INFORMATION</a></li>
    </ul>
  </div>

  <div>
    <h2 class="sticky">Sticky sample</h2>
    <p>bbbb</p>
    <p>bbbb</p>
    <p>bbbb</p>
    <p>bbbb</p>
    <p>bbbb</p>

    <div class="page-btn">
      <button @click="scrollTop" class="btn">TOP</button>
    </div>

    <div class="menu">
      <div class="hover">
        <div @mouseover="mouseOverAction"  >
          <h1 
          data-target="#content-menu" class="hover-text">{{messsage}}</h1>
          <!-- <p v-if="hoverFlag">hoverされました</p> -->
          <ul id="content-menu" v-if="hoverFlag" @mouseleave="mouseLeaveAction">
            <li><a href="#aaa">aaa</a></li>
            <li><a href="#bbb">bbb</a></li>
            <li><a href="#ccc">ccc</a></li>
          </ul>
        </div>
      </div>
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
</div>

</template>

<style scoped>
/* Site Title */
header {
    width: 100%;
    background-color: rgb(173, 170, 170);
    margin-top: 50px;
}
#nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    max-width: 1280px;
    margin: 0 auto;
}
#nav h1 {
    margin: 0 0 0 20px;
}
#nav > ul {
    display: flex;
    margin: 0;
    padding: 0;
    list-style-type: none;
}
#nav > ul > li {
    margin: 0 20px 0 0;
}
#nav > ul > li > a {
    display: block;
    height: auto;
    padding: 20px;
    text-decoration: none;
}
#nav > ul > li > span {
    position: relative;
    display: block;
    height: auto;
    padding: 20px;
    text-decoration: none;
}
#nav > ul > li > span:after {
    content: '▼';
    display: inline-block;
    transform: rotate(90deg);
}
.dropdown {
    position: absolute;
    top: 100%;
    left: 0;
    display: none;
    padding: 0;
    list-style-type: none;
    background-color: rgb(173, 170, 170);
    z-index: 5;
}
.dropdown li {
    width: 250px;
    border-bottom: 1px solid;
}
.dropdown li a {
    display: block;
    padding: 10px;
    text-decoration: none;
}
.isOpen {
    display: block;
}

/* sticky */
.sticky {
  position: sticky;
  top: 0;
  background-color: rgb(65, 64, 64);
  color: #fff;
}

/* ページトップへボタン */
.page-btn {
  position: fixed;
  right: 14px;
  bottom: 14px;
}
.btn {
  width: 100px;
  height: 40px;
}

/* マウスhover */
.hover {
  padding: 0;
  margin: 0;
}
.hover-text {
  background-color: gray;
}
#content-menu {
  background-color: gray;
  width: 30%;
  position: fixed;
  margin: 0;
}
#content-menu li {
  text-align: center;
  padding-right: 35%;
}
a {
  color: black;
}
li {
  list-style: none;
  text-align: center;
  margin-bottom: 15px;
  text-decoration: underline;
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