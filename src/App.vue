<script setup>
import { onMounted, reactive } from 'vue'
import StarTrails from './components/StarTrails.vue'
import { updateYear } from './JavaScript/updateYear.js'
import { smoothScroll } from './JavaScript/smoothScroll.js'

const data = reactive({
  titleList: [
    '你好，请多指教',
    '希望能成为有趣的人',
    'さあ、ゲームを始めよう',
    '相信美好的事情即将发生',
    '平凡的日常正奇迹的发生着',
    '你所热爱的<br/>就是你的生活',
    '给时光以生命<br/>给岁月以文明',
    '路虽远行则将至<br/>事虽难做则必成',
    '一望无际的迷雾中<br/>有人在寻找光明',
    '成长的路不需要惊天伟业,平凡踏实也同样精彩。'
    '当你在凝视着网页的时候<br/>网页也正在凝视着你',
  ],
  navLinks: [{
    name: 'Blog',
    link: 'https://blog.hanahime.online',
  }, {
    name: 'Index',
    link: 'https://HanaKDev.github.io',
  }],

  myProjects: [{
    name: 'Index',
    description: '个人简介、主页、引导页',
    link: 'https://github.com/HanaKDev/HanaKDev.github.io',
  }, {
    name: 'Blog',
    description: '个人博客，学习&随笔',
    link: 'https://blog.hanahime.online',
  }, {
    name: 'undefined',
    description: '喵喵喵~ 暂时没有别的东西 wv',
    link: './',
  }],

  socialLinks: [{
    icon: '<i i-ant-design-github-outlined />',
    link: 'https://github.com/HanaKDev',
    label: 'Github',
  }, {
    icon: '<i i-ant-design-x-outlined />',
    link: 'https://twitter.com/NobleLuluX',
    label: 'Twitter',
  }, /* {
    icon: '<i i-ant-design-youtube-outlined />',
    link: 'https://youtube.com/@sun0225SUN',
    label: 'YouTube',
  }, */ {
    icon: '<i i-ant-design-bilibili-outlined />',
    link: 'https://space.bilibili.com/511373704/',
    label: 'Bilibili',
  }],
})

onMounted(() => {
  // 背景固定
  window.addEventListener('scroll', () => {
    const bg = document.getElementById('background')
    const scrollTop = window.scrollY
    if (scrollTop > 0.7 * window.innerHeight)
      bg.classList.add('fixed')
    else
      bg.classList.remove('fixed')
  })
  // 页脚Copyright时间
  updateYear()
})
</script>

<template>
  <!-- 导航 -->
  <nav absolute fixed bottom-4 left-4 z-20>
    <div v-for="(item, index) in data.navLinks" :key="index" my-6 text-3 text-white wv>
      <a :href="item.link" opacity-75 text-white tracking-widest hover:opacity-100>
        {{ item.name }}
      </a>
    </div>
  </nav>

  <!-- 主体 -->
  <main bg-transparent absolute w-full top-75vh z-10>
    <!-- 大标题 -->
    <section ml-15vw absolute>
      <div text-10 text-white font-bold tracking-widest v-html="data.titleList[Math.floor(Math.random() * data.titleList.length)]" />
      <div flex items-center>
        <div mr-4 flex gap-2>
          <div bg-red rounded-full h-3 w-3 />
          <div bg-yellow rounded-full h-3 w-3 />
          <div bg-green rounded-full h-3 w-3 />
        </div>
        <div text-4 text-white tracking-widest>
          笨蛋依凌 / Hanahime
        </div>
      </div>
    </section>
    <!-- 个人简介 -->
    <section mx-9vw mt-90>
      <!-- 关于我 -->
      <div text-bold mb-4 ml-10 text-8 text-white>
        About Me
      </div>
      <div mx-10 mb-10 flex justify-between>
        <div class="text-white/80">
          <p leading-10>
            喵喵喵~ 你好，这里是是鸾依凌~
          </p>
          <p leading-10>
            热爱编程、读书、白天睡觉。
          </p>
          <p leading-10>
            喜欢计算机科学和 IT 互联网事业，希望能成为一名优秀的开发者。
          </p>
          <p leading-10>
            正在用代码小魔法，让这个世界变得更加可爱和美好。通过巧妙地重用和扩展代码，构建出更美好的的数字世界。喵~
          </p>
          <p leading-10>
            Using a bit of code magic to make the world more adorable and wonderful. By cleverly reusing and extending code to create a more beautiful digital world. Meow~
          </p>
        </div>
        <div>
          <button class="transparent-button" @click.prevent="smoothScroll('AboutMe')">
          <img hidden rounded-full h-25 w-25 transition md:block hover:-translate-y-1 src="./assets/images/avatar.webp" alt="avatar">
          </button>
        </div>
      </div>

      <!-- 我的技能 -->
      <!-- <div text-bold mb-2 ml-10 text-8 text-white>
          My Skills
        </div> -->

      <!-- 我的项目 -->
      <div text-bold mb-2 ml-10 text-8 text-white>
        Projects
      </div>
      <div mb-10 flex flex-wrap justify-between>
        <div v-for="(item, index) in data.myProjects" :key="index" mx-10 my-4 class="basis-3/4 md:basis-1/6">
          <a :href="item.link">
            <div class="bg-white/5 hover:bg-white/10" p-2 rounded-lg shadow-md flex-col transition backdrop-blur-3xl backdrop-opacity-60 hover:backdrop-opacity-100 hover:-translate-y-2>
              <div text-bold opacity-75 text-white>
                {{ item.name }}
              </div>
              <div mt-1 opacity-50 text-3 text-white>
                {{ item.description }}
              </div>
            </div>
          </a>
        </div>
      </div>

      <!-- 社交链接 -->
      <div text-bold mb-2 ml-10 text-8 text-white id="AboutMe">
        Find Me
      </div>
      <div flex flex-wrap justify-between>
        <div v-for="(item, index) in data.socialLinks" :key="index" mx-10 my-4 class="basis-1/6">
          <a class="bg-white/5 hover:bg-white/10" p-2 rounded-lg shadow-md flex-col justify-between items-center transition backdrop-blur-3xl backdrop-opacity-60 hover:backdrop-opacity-100 hover:-translate-y-2 :href="item.link">
            <div mb-1 text-white f-c-c v-html="item.icon" />
            <div text-bold opacity-75 text-white>{{ item.label }}</div>
          </a>
        </div>
      </div>
    </section>

    <!-- 底部 -->
    <footer mb-5>
      <div class="text-white/60" mt-50 f-c-c>
        <i i-ant-design-environment-outlined mr-1 />
        <p>路虽远行则将至，事虽难做则必成</p>
        <!--  <i i-ant-design-environment-outlined ml-1 /> -->
      </div>
      <div class="text-white/60" mt-2 f-c-c gap-4>
        <div>
          © 2019
          <span id="yearSpan" />
          鸾依凌
        </div>
        <div text-pink-800>
          <a href="https://beian.miit.gov.cn">ICP: 粤ICP备2024275888号-1</a>
        </div>
      </div>
    </footer>
  </main>

  <!-- 背景 -->
  <div id="background" absolute wh-full left-0 top-0 z-0>
    <!-- 渐变阴影 -->
    <div to-black-500 absolute h-80vh w-full bottom--30vh left-0 from-black bg-gradient-to-t />
    <!-- 星轨背景 -->
    <StarTrails pb-45vh bg-black />
  </div>
</template>

<style lang="scss" scoped>
#background.fixed {
  position: fixed;
  top: -70%;
}

.transparent-button {
  background: transparent;
  border: none;
  color: inherit;
  text-decoration: none;
  cursor: pointer;
}
</style>
