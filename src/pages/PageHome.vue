<template>
    <div class="h-[calc(60svh)] relative">
        <img src="../assets/hero-image.webp" alt="Hero Image"
            class="absolute w-full h-full object-cover object-top z-[-1]" />
        <div class="absolute bottom-0 left-0 w-full flex flex-col items-center pb-24 px-4">
            <h1
                class="font-heading-font font-bold text-5xl sm:text-7xl lg:text-9xl text-[#e46235] drop-shadow-2xl drop-shadow-black text-shadow-lg text-shadow-black">
                OATHGUARD
            </h1>
            <p
                class="font-semibold uppercase  drop-shadow-2xl drop-shadow-black text-shadow-lg text-shadow-black pb-5 md:text-lg">
                Prepare to rise. Stand United. The Realm depends on your OATH.
            </p>
            <a href="https://discord.gg/g9kcDfHAkp" target="_blank" rel="noopener"
                class="font-heading-font  font-semibold uppercase bg-[#701305] sm:text-2xl px-[2em] py-[0.5em] hover:bg-orange-800 border-[#701305] hover:border-b-rose-950 border-2 cursor-pointer text-[#e7dcbf] w-full sm:w-auto text-center">join
                the discord</a>
        </div>
    </div>
    <div class="grid">
        <div class="bg-[#100909]">
            <div class="max-w-2xl mx-auto text-left sm:text-center py-32 px-4">
                <h2
                    class="font-heading-font text-shadow-lg text-shadow-black  font-semibold text-3xl md:text-6xl pb-4 text-[#e7dcbf]">
                    What is Oathguard?</h2>
                <p class="md:text-lg pb-6">Prepare to a dark-fantasy, action-rougelike game where your skill, timing and
                    strategy are key. Survive waves of corrupted foes defend sacred relics and forage alliances in a
                    shattered world.</p>
                <!--
                <button class="font-heading-font  font-semibold uppercase bg-[#701305] sm:text-2xl px-[2em] py-[0.5em] hover:bg-orange-800 border-[#701305] hover:border-b-rose-950 border-2 cursor-pointer text-[#e7dcbf] w-full sm:w-auto text-center">wishlist on steam</button>
                -->
            </div>
        </div>
        <div class="max-w-2xl mx-auto text-left sm:text-center py-32 px-4">
            <h2 class="font-heading-font text-shadow-lg text-shadow-black font-semibold text-3xl md:text-6xl pb-4 text-[#e7dcbf]">Stay Updated</h2>
            <p class="md:text-lg pb-6">Enter your email to get exclusive news, beta access and behind-the-scenes
                updates.</p>
            <div class="flex flex-col sm:flex-row gap-4">
                <input v-model="email" type="email" name="email" autocomplete="email" placeholder="Enter your email"
                    class="border-2 border-[#212322] p-2 px-4 w-full sm:max-w-md text-xl" />
                <button @click="onNewsletterSubmit"
                    class="font-heading-font  font-semibold uppercase bg-[#701305] sm:text-2xl px-[2em] py-[0.5em] hover:bg-orange-800 border-[#701305] hover:border-b-rose-950 border-2 cursor-pointer text-[#e7dcbf] w-full sm:w-auto text-center">Subscribe</button>
            </div>
        </div>
    </div>
    <footer>
        <div class="text-center py-8">
            <img src="../assets/404ForgeLogo_spaced.webp" alt="404 Forge Logo" class="mx-auto pb-8 w-32 h-auto">
            <p class="text-sm">Copyright © {{ new Date().getFullYear() }} - All right reserved by 404 Forge</p>
        </div>
    </footer>
    <dialog ref="dialogEl" class="p-6 bg-[#1b1b1b] text-[#e7dcbf] border border-[#701305] max-w-md w-full">
        <h3 class="font-heading-font  font-semibold text-2xl mb-4">Newsletter</h3>
        <p ref="dialogMessageEl" class="mb-6 text-lg"></p>
        <button @click="closeDialog"
            class="font-heading-font font-semibold uppercase bg-[#701305] hover:bg-orange-800 border-[#701305] hover:border-b-rose-950 border-2 px-6 py-2 text-[#e7dcbf] cursor-pointer">Close</button>
    </dialog>
</template>
<script setup lang="ts">
import { onMounted, ref } from 'vue';

const email = ref('');
const dialogEl = ref<HTMLDialogElement | null>(null);
const dialogMessageEl = ref<HTMLElement | null>(null);

onMounted(() => {
    if (dialogEl.value) {
        dialogEl.value.addEventListener('close', () => {
            document.body.style.overflow = ''; // ensure scroll is restored
        });
    }
});

const showDialog = (message: string) => {
    if (dialogMessageEl.value && dialogEl.value) {
        dialogMessageEl.value.textContent = message;
        if (!dialogEl.value.open) dialogEl.value.showModal();
        document.body.style.overflow = 'hidden'; // ⛔ prevent scrolling
    }
};

const closeDialog = () => {
    if (dialogEl.value && dialogEl.value.open) dialogEl.value.close();
    document.body.style.overflow = ''; // ✅ restore scroll
};

const onNewsletterSubmit = async () => {
    if (!email.value) {
        showDialog('Please enter a valid email address.');
        return;
    }
    try {
        await signUpForNewsletter(email.value);
        showDialog('Thank you for subscribing to our newsletter!');
        email.value = '';
    } catch (error) {
        console.error('Error subscribing to newsletter:', error);
        showDialog('There was an error subscribing to the newsletter. Please try again later.');
    }
};

const signUpForNewsletter = async (email: string) => {
    const LISTMONK_API = 'https://listmonk.pibern.ch/api/public/subscription';
    const LISTMONK_LIST_ID = '3e5aefc1-c25c-48b5-a4d5-6889a1689207';
    const payload = {
        email,
        name: '',
        list_uuids: [LISTMONK_LIST_ID],
    };

    const response = await fetch(LISTMONK_API, {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify(payload),
    });
    if (!response.ok) {
        throw new Error('Failed to subscribe to the newsletter');
    }
    return response.json();
};
</script>
<style scoped>
dialog::backdrop {
    background-color: rgba(0, 0, 0, 0.7);
    /* dark semi-transparent background */
    backdrop-filter: blur(3px);
    /* optional blur for a polished look */
}

dialog {

    /* Center fallback for browsers that don't do it natively */
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
</style>
