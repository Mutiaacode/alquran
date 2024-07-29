<template>
    <main class="container-fluid mt-custom">
        <div class="home bg-black text-light rounded-3 p-5 shadow-lg mb-4">
            <div class="text-center mb-4">
                <h1 class="display-4 text-warning animated-title">Al-Qur'an Online</h1>
                <p class="lead mb-4">
                    Baca Al-Qur'an secara Online dimana dan kapanpun saja dengan mudah.
                </p>
                <a href="https://quran.kemenag.go.id/" class="btn btn-outline-light text-warning" target="_blank">
                    Kementrian Agama Republik Indonesia
                </a>
            </div>
            <div class="text-center mt-4">
                <p>
                    Al-Qur'an ini yang bersumber dari
                    <strong>Misyari Rasyid Al-'Afasi</strong>.
                </p>
                <p id="clock" class="mt-4 clock"></p>
            </div>
        </div>
    </main>
</template>

<script>
export default {
    name: 'HomeVue',
    components: {},
    data() {
        return {
            time: new Date().toLocaleTimeString()
        };
    },
    mounted() {
        this.updateClock();
        setInterval(this.updateClock, 1000);
    },
    methods: {
        updateClock() {
            this.time = new Date().toLocaleTimeString();
            document.getElementById('clock').innerText = this.time;
        }
    }
}
</script>

<style scoped>
.mt-custom {
    margin-top: 95px;
}

.home {
    background-color: #000000; 
    transition: box-shadow 0.3s ease-in-out;
}

.home:hover {
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.5);
}

.animated-title {
    animation: fadeInDown 1s;
}

@keyframes fadeInDown {
    from {
        opacity: 0;
        transform: translateY(-20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.display-4 {
    font-weight: 700;
    font-size: 3.5rem; 
}


.btn-outline-light:hover {

    color: #000000; 
}

.text-center p {
    color: #e0e0e0;
}


.lead {
    font-size: 1.25rem; 
    color: #f8f9fa; 
}

.text-center strong {
    color: #ffc107;
}

.clock {
    font-size: 1.5rem; 
    color: #ffdf00; 
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
