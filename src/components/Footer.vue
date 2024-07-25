<template>
    <footer class="footer">
      <div class="container">
        <div class="row py-5">
          <div class="col-md-2 text-center">
            <img src="../../public/img/icons/masjid.png" class="logo" alt="Logo">
          </div>
          <div class="col-md-6">
            <h5>Al-Qur'an Online</h5>
            <p>
              Baca Al-Qur'an secara Online dimana dan kapanpun saja dengan mudah. Al-Qur'an ini bersumber dari
              <a href="#" class="link">Kementrian Agama Republik Indonesia</a> dengan murottal
              <strong>Misyari Rasyid Al-'Afasi</strong>.
            </p>
          </div>
          <div class="col-md-2">
            <h5>Social Media</h5>
            <ul class="list-unstyled">
              <li><a href="https://www.instagram.com/mtiaavv_/?hl=id" class="link" target="_blank">Instagram</a></li>
            </ul>
          </div>
          <div class="col-md-2">
            <h5>Related</h5>
            <ul class="list-unstyled">
              <li><a href="" class="link" target="_blank">krisdewa</a></li>
            </ul>
          </div>
        </div>
        <hr class="separator">
        <div class="row text-center">
          <div class="col-md-12">
            <span>
              ® <a href="https://mutiaa.vercel.app" target="_blank" class="text-decoration-none text-light">Mutia Pegi Intanswari</a>
            </span>
          </div>
        </div>
      </div>
    </footer>
  </template>
  
  <script>
  export default {
    name: 'FooterVue',
  };
  </script>
  
  <style scoped>
  .footer {
    background-color: #000; /* Hitam */
    color: #fff; /* Putih */
    padding: 1.5rem 0;
  }
  
  .logo {
    width: 80%;
    max-width: 100px;
  }
  
  h5 {
    font-weight: 600;
    margin-bottom: 1rem;
  }
  
  p {
    color: #d3d3d3; /* Abu-abu terang untuk teks */
  }
  
  .link {
    color: #ffb600; /* Kuning */
    text-decoration: none;
  }
  
  .link:hover {
    text-decoration: underline;
  }
  
  .separator {
    border-color: #444; /* Warna garis pemisah */
  }
  
  @media (max-width: 768px) {
    .logo {
      width: 60%;
    }
  
    .footer {
      text-align: center;
    }
  }
  </style>
  