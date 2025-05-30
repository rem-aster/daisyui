<script>
  import { browser } from "$app/environment"
  import { PUBLIC_DAISYUI_API_PATH } from "$env/static/public"
  import { page } from "$app/stores"
  import LogoHorizontal from "$components/LogoHorizontal.svelte"
  import CompanyLogos from "$components/CompanyLogos.svelte"
  import Footer from "$components/Footer.svelte"
  import SEO from "$components/SEO.svelte"
  import { t } from "$lib/i18n.svelte.js"
  let { title, desc, children } = $props()
  async function fetchStats() {
    if (!browser) return
    const response = await fetch(`${PUBLIC_DAISYUI_API_PATH}/stats.json`)
    return await response.json()
  }
</script>

<SEO
  {title}
  {desc}
  img={`https://img.daisyui.com/images${$page.url.pathname.replace(/\/$/, "")}.webp`}
/>
<div class="mx-auto max-w-4xl px-4 py-20">
  <div
    class="prose prose-sm lg:prose-h1:text-5xl lg:prose-h2:text-4xl lg:prose-h3:text-3xl md:prose-base w-full max-w-4xl grow pt-10 md:text-sm"
  >
    <a class="btn btn-xs not-prose btn-soft group mb-2" href="/components/">
      See all daisyUI components
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="hidden size-5 transition-transform duration-300 group-hover:translate-x-1 md:inline-block rtl:rotate-180 group-hover:rtl:-translate-x-1"
        ><path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M17.25 8.25L21 12m0 0l-3.75 3.75M21 12H3"
        ></path></svg
      >
    </a>

    {#if title}
      <h1>{@html $t(title)}</h1>
    {/if}
    {#if desc}
      <p>{@html $t(desc)}</p>
    {/if}

    {@render children?.()}

    <div class="not-prose pt-12">
      <div
        class="border-base-300 rounded-box mt-6 mb-12 flex flex-col justify-between gap-2 border-2 p-4 sm:gap-12 lg:p-6"
      >
        <div class="flex items-center justify-between gap-2 p-4 max-md:flex-col lg:gap-12">
          <div class="flex flex-col gap-2 max-lg:items-center max-lg:text-center">
            <div class="max-w-46"><LogoHorizontal /></div>
            <h2 class="mx-2">
              {@html $t("daisyUI is the most popular<br />component library for Tailwind&nbsp;CSS")}
            </h2>
          </div>
          <div class="flex flex-col items-center gap-2">
            <a href="/docs/install/" class="btn-primary btn group rounded-full">
              How to install daisyUI?
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="hidden size-5 transition-transform duration-300 group-hover:translate-x-1 md:inline-block rtl:rotate-180 group-hover:rtl:-translate-x-1"
                ><path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M17.25 8.25L21 12m0 0l-3.75 3.75M21 12H3"
                ></path></svg
              >
            </a>
            <a href="/components/" class="link link-hover text-xs"> See components </a>
          </div>
        </div>
        <ul class="my-2 flex gap-4 max-sm:flex-col max-sm:items-center sm:justify-around" dir="ltr">
          {#await fetchStats() then stats}
            <li class="flex gap-2">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-12 w-auto fill-current"
                viewBox="0 0 329 628"
                ><path
                  d="M87.471 224.674s24.709-31.848 8.729-76.079c-16.036-44.202-53.378-60.991-53.378-60.991s-27.944 37.956-12.327 81.043c15.59 43.115 56.976 56.027 56.976 56.027zm68.577 22.618s43.199-3.459 67.936-42.084c24.737-38.597 5.828-81.768 5.828-81.768s-40.103 8.143-65.509 47.773c-25.378 39.601-8.255 76.079-8.255 76.079zm4.379 51.035c-19.996 42.585 1.729 76.553 1.729 76.553s42.418-9.092 61.884-50.561c19.438-41.526-4.937-81.852-4.937-81.852s-38.68 13.275-58.676 55.86zm97.636 34.302s-37.286 16.9-53.183 61.131c-15.896 44.314 8.897 76.051 8.897 76.051s41.33-13.024 56.836-56.167c15.478-43.143-12.55-81.015-12.55-81.015zm31.068 232.922s35.864-24.402 38.29-70.166c2.398-45.793-35.39-73.96-35.39-73.96s-30.844 26.912-33.326 73.876c-2.455 46.936 30.426 70.25 30.426 70.25zm-146.58-426.103s38.234-12.773 49.445-58.426C203.235 35.369 181.51.676 181.51.676s-44.286 16.064-55.246 60.601c-10.932 44.51 16.287 78.171 16.287 78.171zM87.443 321.753s14.195-37.733-14.111-75.242C44.97 208.973 4.364 203.925 4.364 203.925s-15.506 44.51 12.104 81.099c27.609 36.617 70.975 36.729 70.975 36.729zm31.681 99.561s5.439-39.936-30.481-70.223c-35.976-30.314-76.692-26.187-76.692-26.187s-5.243 46.852 29.784 76.386c35.083 29.506 77.389 20.024 77.389 20.024zm48.247 82.326s-6.833-39.713-50.283-57.673c-43.477-18.016-81.015-1.757-81.015-1.757s9.203 46.238 51.537 63.808c42.334 17.486 79.76-4.378 79.76-4.378zm21.083 34.19c-45.29-12.661-80.652 7.949-80.652 7.949s14.641 44.788 58.76 57.142c44.175 12.355 78.701-13.832 78.701-13.832s-11.518-38.625-56.809-51.259zm-41.19-371.163l-20.136-9.9c-1.059 2.203-104.636 222.212 186.405 471.003l14.557-17.04C50.994 373.82 143.192 175.005 147.264 166.667z"
                /></svg
              >
              <div class="text-center">
                <div class="font-title text-2xl tabular-nums">{stats.stargazers_count}</div>
                <div class="text-base-content/60 text-[0.625rem] whitespace-nowrap">
                  Stars on GitHub
                </div>
              </div>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-12 w-auto rotate-y-180 fill-current"
                viewBox="0 0 329 628"
                ><path
                  d="M87.471 224.674s24.709-31.848 8.729-76.079c-16.036-44.202-53.378-60.991-53.378-60.991s-27.944 37.956-12.327 81.043c15.59 43.115 56.976 56.027 56.976 56.027zm68.577 22.618s43.199-3.459 67.936-42.084c24.737-38.597 5.828-81.768 5.828-81.768s-40.103 8.143-65.509 47.773c-25.378 39.601-8.255 76.079-8.255 76.079zm4.379 51.035c-19.996 42.585 1.729 76.553 1.729 76.553s42.418-9.092 61.884-50.561c19.438-41.526-4.937-81.852-4.937-81.852s-38.68 13.275-58.676 55.86zm97.636 34.302s-37.286 16.9-53.183 61.131c-15.896 44.314 8.897 76.051 8.897 76.051s41.33-13.024 56.836-56.167c15.478-43.143-12.55-81.015-12.55-81.015zm31.068 232.922s35.864-24.402 38.29-70.166c2.398-45.793-35.39-73.96-35.39-73.96s-30.844 26.912-33.326 73.876c-2.455 46.936 30.426 70.25 30.426 70.25zm-146.58-426.103s38.234-12.773 49.445-58.426C203.235 35.369 181.51.676 181.51.676s-44.286 16.064-55.246 60.601c-10.932 44.51 16.287 78.171 16.287 78.171zM87.443 321.753s14.195-37.733-14.111-75.242C44.97 208.973 4.364 203.925 4.364 203.925s-15.506 44.51 12.104 81.099c27.609 36.617 70.975 36.729 70.975 36.729zm31.681 99.561s5.439-39.936-30.481-70.223c-35.976-30.314-76.692-26.187-76.692-26.187s-5.243 46.852 29.784 76.386c35.083 29.506 77.389 20.024 77.389 20.024zm48.247 82.326s-6.833-39.713-50.283-57.673c-43.477-18.016-81.015-1.757-81.015-1.757s9.203 46.238 51.537 63.808c42.334 17.486 79.76-4.378 79.76-4.378zm21.083 34.19c-45.29-12.661-80.652 7.949-80.652 7.949s14.641 44.788 58.76 57.142c44.175 12.355 78.701-13.832 78.701-13.832s-11.518-38.625-56.809-51.259zm-41.19-371.163l-20.136-9.9c-1.059 2.203-104.636 222.212 186.405 471.003l14.557-17.04C50.994 373.82 143.192 175.005 147.264 166.667z"
                /></svg
              >
            </li>
            <li class="flex gap-2">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-12 w-auto fill-current"
                viewBox="0 0 329 628"
                ><path
                  d="M87.471 224.674s24.709-31.848 8.729-76.079c-16.036-44.202-53.378-60.991-53.378-60.991s-27.944 37.956-12.327 81.043c15.59 43.115 56.976 56.027 56.976 56.027zm68.577 22.618s43.199-3.459 67.936-42.084c24.737-38.597 5.828-81.768 5.828-81.768s-40.103 8.143-65.509 47.773c-25.378 39.601-8.255 76.079-8.255 76.079zm4.379 51.035c-19.996 42.585 1.729 76.553 1.729 76.553s42.418-9.092 61.884-50.561c19.438-41.526-4.937-81.852-4.937-81.852s-38.68 13.275-58.676 55.86zm97.636 34.302s-37.286 16.9-53.183 61.131c-15.896 44.314 8.897 76.051 8.897 76.051s41.33-13.024 56.836-56.167c15.478-43.143-12.55-81.015-12.55-81.015zm31.068 232.922s35.864-24.402 38.29-70.166c2.398-45.793-35.39-73.96-35.39-73.96s-30.844 26.912-33.326 73.876c-2.455 46.936 30.426 70.25 30.426 70.25zm-146.58-426.103s38.234-12.773 49.445-58.426C203.235 35.369 181.51.676 181.51.676s-44.286 16.064-55.246 60.601c-10.932 44.51 16.287 78.171 16.287 78.171zM87.443 321.753s14.195-37.733-14.111-75.242C44.97 208.973 4.364 203.925 4.364 203.925s-15.506 44.51 12.104 81.099c27.609 36.617 70.975 36.729 70.975 36.729zm31.681 99.561s5.439-39.936-30.481-70.223c-35.976-30.314-76.692-26.187-76.692-26.187s-5.243 46.852 29.784 76.386c35.083 29.506 77.389 20.024 77.389 20.024zm48.247 82.326s-6.833-39.713-50.283-57.673c-43.477-18.016-81.015-1.757-81.015-1.757s9.203 46.238 51.537 63.808c42.334 17.486 79.76-4.378 79.76-4.378zm21.083 34.19c-45.29-12.661-80.652 7.949-80.652 7.949s14.641 44.788 58.76 57.142c44.175 12.355 78.701-13.832 78.701-13.832s-11.518-38.625-56.809-51.259zm-41.19-371.163l-20.136-9.9c-1.059 2.203-104.636 222.212 186.405 471.003l14.557-17.04C50.994 373.82 143.192 175.005 147.264 166.667z"
                /></svg
              >
              <div class="text-center">
                <div class="font-title text-2xl tabular-nums">{stats.dependents_count}</div>
                <div class="text-base-content/60 text-[0.625rem] whitespace-nowrap">
                  Open-source projects
                </div>
              </div>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-12 w-auto rotate-y-180 fill-current"
                viewBox="0 0 329 628"
                ><path
                  d="M87.471 224.674s24.709-31.848 8.729-76.079c-16.036-44.202-53.378-60.991-53.378-60.991s-27.944 37.956-12.327 81.043c15.59 43.115 56.976 56.027 56.976 56.027zm68.577 22.618s43.199-3.459 67.936-42.084c24.737-38.597 5.828-81.768 5.828-81.768s-40.103 8.143-65.509 47.773c-25.378 39.601-8.255 76.079-8.255 76.079zm4.379 51.035c-19.996 42.585 1.729 76.553 1.729 76.553s42.418-9.092 61.884-50.561c19.438-41.526-4.937-81.852-4.937-81.852s-38.68 13.275-58.676 55.86zm97.636 34.302s-37.286 16.9-53.183 61.131c-15.896 44.314 8.897 76.051 8.897 76.051s41.33-13.024 56.836-56.167c15.478-43.143-12.55-81.015-12.55-81.015zm31.068 232.922s35.864-24.402 38.29-70.166c2.398-45.793-35.39-73.96-35.39-73.96s-30.844 26.912-33.326 73.876c-2.455 46.936 30.426 70.25 30.426 70.25zm-146.58-426.103s38.234-12.773 49.445-58.426C203.235 35.369 181.51.676 181.51.676s-44.286 16.064-55.246 60.601c-10.932 44.51 16.287 78.171 16.287 78.171zM87.443 321.753s14.195-37.733-14.111-75.242C44.97 208.973 4.364 203.925 4.364 203.925s-15.506 44.51 12.104 81.099c27.609 36.617 70.975 36.729 70.975 36.729zm31.681 99.561s5.439-39.936-30.481-70.223c-35.976-30.314-76.692-26.187-76.692-26.187s-5.243 46.852 29.784 76.386c35.083 29.506 77.389 20.024 77.389 20.024zm48.247 82.326s-6.833-39.713-50.283-57.673c-43.477-18.016-81.015-1.757-81.015-1.757s9.203 46.238 51.537 63.808c42.334 17.486 79.76-4.378 79.76-4.378zm21.083 34.19c-45.29-12.661-80.652 7.949-80.652 7.949s14.641 44.788 58.76 57.142c44.175 12.355 78.701-13.832 78.701-13.832s-11.518-38.625-56.809-51.259zm-41.19-371.163l-20.136-9.9c-1.059 2.203-104.636 222.212 186.405 471.003l14.557-17.04C50.994 373.82 143.192 175.005 147.264 166.667z"
                /></svg
              >
            </li>
            <li class="flex gap-2">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-12 w-auto fill-current"
                viewBox="0 0 329 628"
                ><path
                  d="M87.471 224.674s24.709-31.848 8.729-76.079c-16.036-44.202-53.378-60.991-53.378-60.991s-27.944 37.956-12.327 81.043c15.59 43.115 56.976 56.027 56.976 56.027zm68.577 22.618s43.199-3.459 67.936-42.084c24.737-38.597 5.828-81.768 5.828-81.768s-40.103 8.143-65.509 47.773c-25.378 39.601-8.255 76.079-8.255 76.079zm4.379 51.035c-19.996 42.585 1.729 76.553 1.729 76.553s42.418-9.092 61.884-50.561c19.438-41.526-4.937-81.852-4.937-81.852s-38.68 13.275-58.676 55.86zm97.636 34.302s-37.286 16.9-53.183 61.131c-15.896 44.314 8.897 76.051 8.897 76.051s41.33-13.024 56.836-56.167c15.478-43.143-12.55-81.015-12.55-81.015zm31.068 232.922s35.864-24.402 38.29-70.166c2.398-45.793-35.39-73.96-35.39-73.96s-30.844 26.912-33.326 73.876c-2.455 46.936 30.426 70.25 30.426 70.25zm-146.58-426.103s38.234-12.773 49.445-58.426C203.235 35.369 181.51.676 181.51.676s-44.286 16.064-55.246 60.601c-10.932 44.51 16.287 78.171 16.287 78.171zM87.443 321.753s14.195-37.733-14.111-75.242C44.97 208.973 4.364 203.925 4.364 203.925s-15.506 44.51 12.104 81.099c27.609 36.617 70.975 36.729 70.975 36.729zm31.681 99.561s5.439-39.936-30.481-70.223c-35.976-30.314-76.692-26.187-76.692-26.187s-5.243 46.852 29.784 76.386c35.083 29.506 77.389 20.024 77.389 20.024zm48.247 82.326s-6.833-39.713-50.283-57.673c-43.477-18.016-81.015-1.757-81.015-1.757s9.203 46.238 51.537 63.808c42.334 17.486 79.76-4.378 79.76-4.378zm21.083 34.19c-45.29-12.661-80.652 7.949-80.652 7.949s14.641 44.788 58.76 57.142c44.175 12.355 78.701-13.832 78.701-13.832s-11.518-38.625-56.809-51.259zm-41.19-371.163l-20.136-9.9c-1.059 2.203-104.636 222.212 186.405 471.003l14.557-17.04C50.994 373.82 143.192 175.005 147.264 166.667z"
                /></svg
              >
              <div class="text-center">
                <div class="font-title text-2xl tabular-nums">
                  {stats.npm_downloads_count_total}
                </div>
                <div class="text-base-content/60 text-[0.625rem] whitespace-nowrap">
                  NPM downloads
                </div>
              </div>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-12 w-auto rotate-y-180 fill-current"
                viewBox="0 0 329 628"
                ><path
                  d="M87.471 224.674s24.709-31.848 8.729-76.079c-16.036-44.202-53.378-60.991-53.378-60.991s-27.944 37.956-12.327 81.043c15.59 43.115 56.976 56.027 56.976 56.027zm68.577 22.618s43.199-3.459 67.936-42.084c24.737-38.597 5.828-81.768 5.828-81.768s-40.103 8.143-65.509 47.773c-25.378 39.601-8.255 76.079-8.255 76.079zm4.379 51.035c-19.996 42.585 1.729 76.553 1.729 76.553s42.418-9.092 61.884-50.561c19.438-41.526-4.937-81.852-4.937-81.852s-38.68 13.275-58.676 55.86zm97.636 34.302s-37.286 16.9-53.183 61.131c-15.896 44.314 8.897 76.051 8.897 76.051s41.33-13.024 56.836-56.167c15.478-43.143-12.55-81.015-12.55-81.015zm31.068 232.922s35.864-24.402 38.29-70.166c2.398-45.793-35.39-73.96-35.39-73.96s-30.844 26.912-33.326 73.876c-2.455 46.936 30.426 70.25 30.426 70.25zm-146.58-426.103s38.234-12.773 49.445-58.426C203.235 35.369 181.51.676 181.51.676s-44.286 16.064-55.246 60.601c-10.932 44.51 16.287 78.171 16.287 78.171zM87.443 321.753s14.195-37.733-14.111-75.242C44.97 208.973 4.364 203.925 4.364 203.925s-15.506 44.51 12.104 81.099c27.609 36.617 70.975 36.729 70.975 36.729zm31.681 99.561s5.439-39.936-30.481-70.223c-35.976-30.314-76.692-26.187-76.692-26.187s-5.243 46.852 29.784 76.386c35.083 29.506 77.389 20.024 77.389 20.024zm48.247 82.326s-6.833-39.713-50.283-57.673c-43.477-18.016-81.015-1.757-81.015-1.757s9.203 46.238 51.537 63.808c42.334 17.486 79.76-4.378 79.76-4.378zm21.083 34.19c-45.29-12.661-80.652 7.949-80.652 7.949s14.641 44.788 58.76 57.142c44.175 12.355 78.701-13.832 78.701-13.832s-11.518-38.625-56.809-51.259zm-41.19-371.163l-20.136-9.9c-1.059 2.203-104.636 222.212 186.405 471.003l14.557-17.04C50.994 373.82 143.192 175.005 147.264 166.667z"
                /></svg
              >
            </li>
          {/await}
        </ul>
      </div>
      <div class="text-base-content">
        <CompanyLogos />
      </div>
    </div>
  </div>
</div>
<Footer />
