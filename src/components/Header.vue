<template>
    <header :class="isScroll?'header active' : 'header'">
        <q-scroll-observer @scroll="handleScroll" />
        <div id="menu-btn" :class="menuToggle ? 'fas fa-times':'fas fa-bars'" @click="toggleMenu"></div>
        <router-link to="/" class="logo"><i class="fas fa-hospital">프라임<span>병원</span></i></router-link>
        <nav :class="menuToggle ? 'navbar active':'navbar'">
            <router-link to="/">이용안내</router-link>
            <router-link to="/">척추센터</router-link>
            <router-link to="/">관절센터</router-link>
            <router-link to="/">내과검진센터</router-link>
            <router-link to="/">건강정보</router-link>
        </nav>

        <div id="login-btn">
            <q-btn flat  class="btn gt-sm">Login</q-btn>
            <q-btn round size="sm" flat icon="far fa-user" class="lt-md"></q-btn>
        </div>
    </header>
</template>

<script setup>
import { ref } from 'vue'

const menuToggle = ref(false)
const isScroll = ref(false)

function toggleMenu () {
  menuToggle.value = !menuToggle.value
}

function handleScroll () {
  if (window.scrollY > 0) {
    isScroll.value = true
  } else {
    isScroll.value = false
  }
}
</script>

<style>
body{
    height: 300rem;
}
.header{
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 999;
    background: #fff;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 3rem 9%;
}

.header.active{
    box-shadow: var(--box-shadow);
    padding: 2rem 9%;
}

.header .logo{
    font-size: 2.5rem;
    color: var(--green);
}

.header .logo span{
    font-size: 2rem;
    color: var(--black);
}

.header .navbar a{
    font-size: 1.7rem;
    margin: 0 1rem;
    color: var(--black);
}

.header .navbar a:hover{
    color: var(--green);
    font-size: 2rem;
}
.btn{
    font-size: 1.7rem;
    background: var(--green);
    color: #fff;
}

.btn:hover{
    background: var(--light-green);
}

.header .btn{
    margin-top: 0;
}

#menu-btn{
    display: none;
}

@media(max-width: 1023px)
{
    .header{
        padding: 2rem;
    }

    #menu-btn{
        display: block;
    }

    #menu-btn.fa-times{
        transform: rotate(180deg);
    }
}

@media(max-width: 599px)
{
    .header .navbar{
        position: absolute;
        top: 99%; left:0; right: 0;
        background: #fff;
        border-top: var(--border);
        clip-path: polygon(0 0,100% 0, 100% 0,0 0);
    }
    .header .navbar a{
        display: block;
        margin: 2rem;
        font-size: 2rem;
    }
    .header .navbar.active{
        clip-path: polygon(0 0,100% 0, 100% 100%,0 100%);
    }
    #menu-btn.fa-times{
        transform: rotate(360deg);
    }
}
</style>
