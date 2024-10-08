<template>
    <main class="container mt-custom">
        <div class="bg-dark p-4 rounded shadow text-white">
            <div class="row">
                <div class="col-md-6">
                    <h2 class="fw-bold">
                        <span v-text="quran.nama_latin" /> - <span v-text="quran.nama" />
                    </h2>
                    <p class="text-capitalize"
                        v-text="quran.tempat_turun + ' • ' + quran.jumlah_ayat + ' ayat' + ' • ' + quran.arti"></p>
                </div>
                <div class="col-md-6 text-end justify-content-end">
                    <div class="">
                        <div class="mt-1">
                            <router-link :to="{ name: 'tafsir', params: { id: quran.nomor } }"
                                class="btn btn-warning fw-bold"> Lihat Tafsir </router-link>
                        </div>
                    </div>
                </div>
                <div class="col-md-12 text-center justify-content-center">
                    <div class="">
                        <audio controls v-if="quran.audio">
                            <source v-bind:src="quran.audio" type="audio/mpeg" />
                            Your browser does not support the audio element.
                        </audio>
                    </div>
                </div>
            </div>
        </div>

        <div class="row mt-2">
            <div class="col-md-6 mt-1" v-if="quran.prev != false">
                <div class="d-grid gap-2">
                    <router-link :to="{ name: 'surah', params: { id: quran.prev_id } }" class="btn btn-dark">
                        <i class="bi bi-arrow-left"></i> Surah Sebelumnya ({{ quran.prevsurah }})
                    </router-link>
                </div>
            </div>
            <div class="col-md-6" v-if="quran.prev == false"></div>
            <div class="col-md-6 mt-1" v-if="quran.next != false">
                <div class="d-grid gap-2">
                    <router-link :to="{ name: 'surah', params: { id: quran.next_id } }"
                        class="btn btn-dark float-end">
                        ({{ quran.nextsurah }}) Surah Selanjutnya <i class="bi bi-arrow-right"></i>
                    </router-link>
                </div>
            </div>
        </div>

    </main>

    <div class="container mb-5" v-if="!isLoading">
        <div class="row">
            <div class="col-md-12" v-for="(ayat, index) in ayat" :key="index">
                <div class="card mt-3 shadow-sm">
                    <div class="card-body">
                        <div class="row">
                            <div class="col-md-6 col-12">
                                <h5 class="card-title nama-latin mb-2"> {{ ayat.surah }} : {{ ayat.nomor }} </h5>
                            </div>
                            <div class="col-md-6 col-12">
                                <h1 class="text-end"> {{ ayat.ar }} </h1>
                                <p class="text-end"><span v-html="ayat.tr"> </span></p>
                            </div>
                            <div class="col-md-6 col-12">
                                <p class="card-text fst-italic text-muted"> {{ ayat.idn }}</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <footer-vue />
</template>

<script>
import { reactive, ref, onMounted } from 'vue'
import { useRouter, useRoute } from 'vue-router'
import axios from 'axios'
import FooterVue from '@/components/Footer.vue'

export default {
    name: 'DetailSurahVue',
    components: {
        FooterVue,
    },
    setup() {
        const quran = reactive({
            nomor: '',
            nama: '',
            nama_latin: '',
            arti: '',
            ayat: [],
            jumlah_ayat: '',
            tempat_turun: '',
            audio: '',
            surat_selanjutnya: {
                id: '',
                nama: '',
                nama_latin: '',
                arti: '',
                jumlah_ayat: '',
                tempat_turun: '',
            },
            surat_sebelumnya: {
                id: '',
                nama: '',
                nama_latin: '',
                arti: '',
                jumlah_ayat: '',
                tempat_turun: '',
            },
        });

        const ayat = ref([]);
        const isLoading = ref(true);

        const router = useRouter();
        const route = useRoute();

        onMounted(async () => {
            try {
                const response = await axios.get(`https://equran.id/api/surat/${route.params.id}`);
                quran.nomor = response.data.nomor;
                quran.nama_latin = response.data.nama_latin;
                quran.nama = response.data.nama;
                quran.arti = response.data.arti;
                quran.ayat = response.data.ayat;
                quran.jumlah_ayat = response.data.jumlah_ayat;
                quran.tempat_turun = response.data.tempat_turun;
                quran.audio = response.data.audio;
                quran.next = response.data.surat_selanjutnya;
                quran.prev = response.data.surat_sebelumnya;
                quran.next_id = response.data.surat_selanjutnya.id;
                quran.prev_id = response.data.surat_sebelumnya.id;
                quran.nextsurah = response.data.surat_selanjutnya.nama_latin;
                quran.prevsurah = response.data.surat_sebelumnya.nama_latin;
                ayat.value = response.data.ayat;
            } catch (error) {
                console.error('Error fetching surah details:', error);
            } finally {
                isLoading.value = false;
            }
        });

        return {
            quran,
            ayat,
            isLoading,
        };
    },
}
</script>

<style scoped>
.mt-custom {
    margin-top: 95px;
}

.card {
    border-top-left-radius: 3px;
    border-top-right-radius: 20px;
    border-bottom-left-radius: 20px;
    border-bottom-right-radius: 3px;
}

.card-body:hover {
    box-shadow: 0 0px 10px 0 rgb(181, 181, 181);
    border-top-left-radius: 3px;
    border-top-right-radius: 20px;
    border-bottom-left-radius: 20px;
    border-bottom-right-radius: 3px;
}

.card-text {
    margin-top: -10px;
}

/* Specifies the size of the audio container */
audio {
    margin-top: 5px;
    background-color: #ffc107;
    border-radius: 5px;
    width: 100%;
}

audio::-webkit-media-controls-panel {
    background-color: #ffc107;
    justify-content: center;
}
</style>
