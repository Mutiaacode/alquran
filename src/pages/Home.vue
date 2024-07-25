<template>
    <main class="container mt-custom">
        <div class="home bg-black text-light rounded-3 p-5 shadow-lg mb-4">
            <div class="text-center mb-4">
                <h1 class="display-4 text-warning">Al-Qur'an Online</h1>
                <p class="lead mb-4">
                    Baca Al-Qur'an secara Online dimana dan kapanpun saja dengan mudah.
                </p>
                <a href="https://quran.kemenag.go.id/" class="btn btn-outline-light text-warning btn-lg" target="_blank">
                    Kementrian Agama Republik Indonesia
                </a>
            </div>
            <div class="text-center mt-4">
                <p>
                    Al-Qur'an ini yang bersumber dari
                    <strong>Misyari Rasyid Al-'Afasi</strong>.
                </p>
            </div>
        </div>
    </main>
</template>

<script>
export default {
    name: 'HomeVue',
    components: {},
}
</script>

<style scoped>
.mt-custom {
    margin-top: 95px;
}

.home {
    background-color: #000000; /* Hitam untuk tampilan elegan */
}

.display-4 {
    font-weight: 700;
}

.btn-outline-light {
    border-color: #ffffff; /* Outline putih */
    color: #ffffff; /* Teks putih */
}

.btn-outline-light:hover {
    background-color: #ffffff; /* Background putih saat hover */
    color: #000000; /* Teks hitam saat hover */
}

.text-center p {
    color: #e0e0e0; /* Teks light untuk kontras dengan background hitam */
}

@media screen and (max-width: 768px) {
    .home {
        padding: 20px;
    }

    .display-4 {
        font-size: 2.5rem;
    }
}
</style>
