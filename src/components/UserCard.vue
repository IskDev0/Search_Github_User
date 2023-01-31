<template>
  <div class="bg-[#1F2A48] w-1/2 mx-auto p-12 mt-10 rounded-lg dark:bg-white">
    <div class="flex justify-between items-start">
      <img class="rounded-full w-24" :src="info.avatar_url" alt="">
      <div class="w-3/4">
        <div class="flex flex-col">
          <div class="flex flex-col">
            <div class="flex justify-between">
              <p class="text-xl font-bold">{{ info.name }}</p>
              <p class="font-thin">Joined {{ date.toDateString() }}</p>
            </div>
            <a class="text-blue-600" :href="`https://github.com/${info.login}`">@{{ info.login }}</a>
            <p class="text-gray-400 mt-4">{{ info.bio ? info.bio : "This profile has no bio" }}</p>
          </div>
          <div class="flex justify-between bg-[#141C2F] py-4 px-8 rounded-lg my-8 dark:bg-slate-100">
            <div class="flex flex-col">
              <span>Repos</span>
              <span class="text-2xl font-bold">{{ info.public_repos }}</span>
            </div>
            <div class="flex flex-col">
              <span>Followers</span>
              <span class="text-2xl font-bold">{{ info.followers }}</span>
            </div>
            <div class="flex flex-col">
              <span>Following</span>
              <span class="text-2xl font-bold">{{ info.following }}</span>
            </div>
          </div>
          <div class="grid grid-cols-2 gap-x-12 gap-y-6">
            <p class="flex gap-4">
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                    class="dark:fill-black"
                    d="M12 2C8.13 2 5 5.13 5 9C5 14.25 12 22 12 22C12 22 19 14.25 19 9C19 5.13 15.87 2 12 2ZM12 11.5C11.337 11.5 10.7011 11.2366 10.2322 10.7678C9.76339 10.2989 9.5 9.66304 9.5 9C9.5 8.33696 9.76339 7.70107 10.2322 7.23223C10.7011 6.76339 11.337 6.5 12 6.5C12.663 6.5 13.2989 6.76339 13.7678 7.23223C14.2366 7.70107 14.5 8.33696 14.5 9C14.5 9.66304 14.2366 10.2989 13.7678 10.7678C13.2989 11.2366 12.663 11.5 12 11.5Z"
                    :fill="info.location === null ? '#fff' : '#eee'"/>
              </svg>
              {{ info.location ? info.location : "Not available" }}
            </p>
            <a :href="`https://twitter.com/${info.twitter_username}`" class="flex gap-4">
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                    class="dark:fill-black"
                    d="M22.46 6C21.69 6.35 20.86 6.58 20 6.69C20.88 6.16 21.56 5.32 21.88 4.31C21.05 4.81 20.13 5.16 19.16 5.36C18.37 4.5 17.26 4 16 4C13.65 4 11.73 5.92 11.73 8.29C11.73 8.63 11.77 8.96 11.84 9.27C8.28004 9.09 5.11004 7.38 3.00004 4.79C2.63004 5.42 2.42004 6.16 2.42004 6.94C2.42004 8.43 3.17004 9.75 4.33004 10.5C3.62004 10.5 2.96004 10.3 2.38004 10V10.03C2.38004 12.11 3.86004 13.85 5.82004 14.24C5.19077 14.4122 4.53013 14.4362 3.89004 14.31C4.16165 15.1625 4.69358 15.9084 5.41106 16.4429C6.12854 16.9775 6.99549 17.2737 7.89004 17.29C6.37367 18.4904 4.49404 19.1393 2.56004 19.13C2.22004 19.13 1.88004 19.11 1.54004 19.07C3.44004 20.29 5.70004 21 8.12004 21C16 21 20.33 14.46 20.33 8.79C20.33 8.6 20.33 8.42 20.32 8.23C21.16 7.63 21.88 6.87 22.46 6Z"
                    fill="#fff"/>
              </svg>
              {{ info.twitter_username ? info.twitter_username : "Not available" }}</a>
            <a :href="info.blog" class="flex gap-4">
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                    class="dark:fill-black"
                    d="M10.59 13.41C11 13.8 11 14.44 10.59 14.83C10.2 15.22 9.56002 15.22 9.17002 14.83C8.23339 13.892 7.70732 12.6206 7.70732 11.295C7.70732 9.96942 8.23339 8.69803 9.17002 7.76L12.71 4.22C13.648 3.28338 14.9194 2.75731 16.245 2.75731C17.5706 2.75731 18.842 3.28338 19.78 4.22C20.7166 5.15803 21.2427 6.42942 21.2427 7.755C21.2427 9.08058 20.7166 10.352 19.78 11.29L18.29 12.78C18.3 11.96 18.17 11.14 17.89 10.36L18.36 9.88C18.6404 9.60269 18.8629 9.27253 19.0148 8.90863C19.1667 8.54473 19.2449 8.15432 19.2449 7.76C19.2449 7.36568 19.1667 6.97527 19.0148 6.61137C18.8629 6.24747 18.6404 5.91731 18.36 5.64C18.0827 5.35966 17.7525 5.13711 17.3886 4.98522C17.0247 4.83333 16.6343 4.75512 16.24 4.75512C15.8457 4.75512 15.4553 4.83333 15.0914 4.98522C14.7275 5.13711 14.3973 5.35966 14.12 5.64L10.59 9.17C10.3097 9.44731 10.0871 9.77747 9.93524 10.1414C9.78335 10.5053 9.70514 10.8957 9.70514 11.29C9.70514 11.6843 9.78335 12.0747 9.93524 12.4386C10.0871 12.8025 10.3097 13.1327 10.59 13.41ZM13.41 9.17C13.8 8.78 14.44 8.78 14.83 9.17C15.7666 10.108 16.2927 11.3794 16.2927 12.705C16.2927 14.0306 15.7666 15.302 14.83 16.24L11.29 19.78C10.352 20.7166 9.08059 21.2427 7.75502 21.2427C6.42944 21.2427 5.15804 20.7166 4.22002 19.78C3.28339 18.842 2.75732 17.5706 2.75732 16.245C2.75732 14.9194 3.28339 13.648 4.22002 12.71L5.71002 11.22C5.70002 12.04 5.83002 12.86 6.11002 13.65L5.64002 14.12C5.35968 14.3973 5.13712 14.7275 4.98524 15.0914C4.83335 15.4553 4.75514 15.8457 4.75514 16.24C4.75514 16.6343 4.83335 17.0247 4.98524 17.3886C5.13712 17.7525 5.35968 18.0827 5.64002 18.36C5.91733 18.6403 6.24749 18.8629 6.61139 19.0148C6.97528 19.1667 7.36569 19.2449 7.76002 19.2449C8.15434 19.2449 8.54475 19.1667 8.90865 19.0148C9.27254 18.8629 9.6027 18.6403 9.88002 18.36L13.41 14.83C13.6904 14.5527 13.9129 14.2225 14.0648 13.8586C14.2167 13.4947 14.2949 13.1043 14.2949 12.71C14.2949 12.3157 14.2167 11.9253 14.0648 11.5614C13.9129 11.1975 13.6904 10.8673 13.41 10.59C13.3129 10.499 13.2355 10.389 13.1826 10.2669C13.1296 10.1448 13.1023 10.0131 13.1023 9.88C13.1023 9.7469 13.1296 9.61522 13.1826 9.4931C13.2355 9.37097 13.3129 9.26101 13.41 9.17Z"
                    fill="#fff"/>
              </svg>
              {{ info.blog ? info.blog : "Not available" }}</a>
            <p class="flex gap-4">
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path
                    class="dark:stroke-1 dark:stroke-black"
                    d="M2.25 21H21.75M3.75 3V21M14.25 3V21M20.25 7.5V21M6.75 6.75H7.5M6.75 9.75H7.5M6.75 12.75H7.5M10.5 6.75H11.25M10.5 9.75H11.25M10.5 12.75H11.25M6.75 21V17.625C6.75 17.004 7.254 16.5 7.875 16.5H10.125C10.746 16.5 11.25 17.004 11.25 17.625V21M3 3H15M14.25 7.5H21M17.25 11.25H17.258V11.258H17.25V11.25ZM17.25 14.25H17.258V14.258H17.25V14.25ZM17.25 17.25H17.258V17.258H17.25V17.25Z"
                    stroke="#fff" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              {{ info.company ? info.company : "Not available" }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import {computed} from "vue";

let props = defineProps({
  info: {
    type: Object,
    required: true
  }
})

let date = computed(() => {
  return new Date(props.info.created_at)
})

</script>