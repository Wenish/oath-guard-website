<template>
    <div class="h-[calc(60svh)] relative">
        <img src="../assets/hero-image.webp" alt="Hero Image"
            class="absolute w-full h-full object-cover object-top z-[-1]" />
        <div class="absolute bottom-0 left-0 w-full flex flex-col items-center pb-24 px-4">
            <h1
                class="font-cizel font-bold text-5xl sm:text-7xl lg:text-9xl text-[#e46235] [text-shadow:_2px_2px_0_#000,2px_-2px_0_#000,-2px_2px_0_#000,-2px_-2px_0_#000]">
                OATHGUARD
            </h1>
            <p
                class="font-lora font-semibold uppercase [text-shadow:_1px_1px_0_#000,1px_-1px_0_#000,-1px_1px_0_#000,-1px_-1px_0_#000] pb-5 md:text-lg">
                Prepare to rise. Stand United. The Realm depends on your OATH.
            </p>
            <a href="https://discord.gg/g9kcDfHAkp" target="_blank" rel="noopener"
                class="font-cizel font-semibold uppercase bg-[#701305] sm:text-2xl px-[2em] py-[0.5em] hover:bg-orange-800 border-[#701305] hover:border-b-rose-950 border-2 cursor-pointer text-[#e7dcbf] w-full sm:w-auto text-center">join
                the discord</a>
        </div>
    </div>
    <div class="grid">
        <div class="bg-[#090505]">
            <div class="max-w-2xl mx-auto text-left sm:text-center py-32 px-4">
                <h2 class="font-cizel font-semibold text-3xl md:text-6xl pb-4 text-[#e7dcbf]">What is Oathguard?</h2>
                <p class="md:text-lg pb-6">Prepare to a dark-fantasy, action-rougelike game where your skill, timing and
                    strategy are key. Survive waves of corrupted foes defend sacred relics and forage alliances in a
                    shattered world.</p>
                <!--
                <button class="font-cizel font-semibold uppercase bg-[#701305] sm:text-2xl px-[2em] py-[0.5em] hover:bg-orange-800 border-[#701305] hover:border-b-rose-950 border-2 cursor-pointer text-[#e7dcbf] w-full sm:w-auto text-center">wishlist on steam</button>
                -->
            </div>
        </div>
        <div class="max-w-2xl mx-auto text-left sm:text-center py-32 px-4">
            <h2 class="font-cizel font-semibold text-3xl md:text-6xl pb-4 text-[#e7dcbf]">Stay Updated</h2>
            <p class="md:text-lg pb-6">Enter your email to get exclusive news, beta access and behind-the-scenes
                updates.</p>
            <div class="flex flex-col sm:flex-row gap-4">
                <input type="email" name="email" autocomplete="email" placeholder="Enter your email"
                    class="border-2 border-[#212322] p-2 px-4 w-full sm:max-w-md text-xl" />
                <button
                    class="font-cizel font-semibold uppercase bg-[#701305] sm:text-2xl px-[2em] py-[0.5em] hover:bg-orange-800 border-[#701305] hover:border-b-rose-950 border-2 cursor-pointer text-[#e7dcbf] w-full sm:w-auto text-center">Subscribe</button>
            </div>
        </div>
    </div>
    <footer>
        <div class="text-center py-8">
            <img src="../assets/404ForgeLogo_spaced.webp" alt="404 Forge Logo" class="mx-auto pb-8 w-32 h-auto">
            <p class="text-sm">Copyright © {{ new Date().getFullYear() }} - All right reserved by 404 Forge</p>
        </div>
    </footer>
</template>
<script setup lang="ts">
</script>