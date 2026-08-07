<template>
  <section
    class="flex min-h-screen items-center justify-center p-6 text-center"
    :style="{ background: 'var(--canvas)', color: 'var(--text)' }"
  >
    <div
      class="rounded-lg p-10 sm:p-16"
      :style="{ background: 'var(--primary)', color: 'var(--primary-foreground)' }"
    >
      <p class="text-8xl font-extrabold tracking-[-.08em]">404</p>
      <h1 class="mt-4 text-3xl font-extrabold tracking-[-.04em]">Wrong turn.</h1>
      <p class="mt-3">This page doesn’t exist, but the rest of the site does.</p>
      <RouterLink
        to="/"
        class="focusable mt-7 inline-block rounded-md bg-[#172033] px-5 py-3 text-sm font-bold uppercase tracking-wider text-white transition-transform duration-200 hover:scale-105"
      >
        Back home
      </RouterLink>
    </div>
  </section>
</template>
