<template>
  <main
    class="min-h-screen p-4 sm:p-10"
    :style="{ background: 'var(--canvas)', color: 'var(--text)' }"
  >
    <div class="mx-auto max-w-xl">
      <RouterLink
        to="/"
        class="focusable eyebrow"
      >
        ← Portfolio
      </RouterLink>
      <section
        class="relative mt-5 overflow-hidden rounded-lg p-8 sm:p-10"
        :style="{ background: 'var(--primary)', color: 'var(--primary-foreground)' }"
      >
        <div class="absolute -right-10 -top-10 h-36 w-36 rotate-45 bg-white/30"></div>
        <img
          src="../assets/rjw.svg"
          alt="Ryan Wong"
          class="relative h-20 w-20 rounded-lg bg-white p-2"
        />
        <h1 class="relative mt-7 text-5xl font-extrabold tracking-[-.05em]">Ryan Wong</h1>
        <p class="relative mt-2 text-lg">Developer, creator, and occasional camera holder.</p>
      </section>
      <section class="mt-10">
        <p class="eyebrow">Fresh from the desk</p>
        <h2 class="section-heading mt-2">Recent releases</h2>
        <div class="mt-5 grid gap-3">
          <a
            href="https://www.youtube.com/watch?v=euQlo9ny4Ec"
            target="_blank"
            class="focusable flat-card flat-card-interactive flex items-center justify-between"
            :style="{ background: 'var(--amber)', color: '#4A2A05' }"
          >
            <span>
              <b class="block">Japan Part 2</b>
              <small>Video · March 28, 2025</small>
            </span>
            <i class="pi pi-youtube text-2xl"></i>
          </a>
          <a
            href="https://www.blog.ryanwong.ca/blog/diy-nas"
            target="_blank"
            class="focusable flat-card flat-card-interactive flex items-center justify-between"
          >
            <span>
              <b class="block">DIY NAS</b>
              <small>Blog post · March 17, 2025</small>
            </span>
            <i class="pi pi-file-edit text-2xl"></i>
          </a>
        </div>
      </section>
      <section class="mt-10">
        <p class="eyebrow">Find me elsewhere</p>
        <h2 class="section-heading mt-2">Links</h2>
        <div class="mt-5 grid gap-3 sm:grid-cols-2">
          <a
            v-for="item in [
              { text: 'Portfolio website', url: '/', icon: 'pi-home' },
              { text: 'Blog', url: 'https://blog.ryanwong.ca', icon: 'pi-file' },
              { text: 'YouTube', url: 'https://www.youtube.com/@ryanwoong', icon: 'pi-youtube' },
              { text: 'Instagram · @ryxn.wxng', url: 'https://www.instagram.com/ryxn.wxng/', icon: 'pi-instagram' },
              { text: 'LinkedIn', url: 'https://www.linkedin.com/in/ryanwongyyc/', icon: 'pi-linkedin' },
              { text: 'GitHub', url: 'https://github.com/ryanwoong', icon: 'pi-github' },
            ]"
            :key="item.text"
            :href="item.url"
            :target="item.url.startsWith('http') ? '_blank' : undefined"
            class="focusable flat-card flat-card-interactive flex items-center gap-3 font-bold"
          >
            <i
              :class="['pi', item.icon]"
              :style="{ color: 'var(--primary-strong)' }"
            ></i>
            {{ item.text }}
            <i
              class="pi pi-arrow-up-right ml-auto text-xs"
              :style="{ color: 'var(--muted-text)' }"
            ></i>
          </a>
        </div>
      </section>
    </div>
  </main>
</template>
