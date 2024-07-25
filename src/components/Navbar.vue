<template>
    <nav class="navbar navbar-expand-md navbar-custom fixed-top py-3">
        <div class="container">
            <router-link :to="{ name: 'home' }" class="navbar-brand text-light" aria-current="page">
                <img src="../../public/img/icons/masjid.png" class="img text-dark" alt="Logo" />
                AL-QUR'AN ONLINE 
            </router-link>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarCollapse"
                aria-controls="navbarCollapse" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarCollapse">
                <ul class="navbar-nav me-auto mb-2 mb-md-0">
                   
                </ul>
              
            </div>
        </div>
    </nav>
</template>

<style scoped>
.navbar-custom {
    background-color: rgb(0, 0, 0); /* Black background for navbar */
}

.navbar-brand {
    font-weight: bold;
    color: #fff; /* White text for brand */
}

.navbar-brand img {
    width: 35px;
    height: 35px;
}

.nav-link {
    color: #fff; /* White text for nav links */
}

.nav-link:hover {
    color: #00f; /* Blue color on hover */
}

.btn-custom {
    background-color: #00f; /* Blue background for button */
    color: #fff; /* White text for button */
    border: none;
}

.btn-custom:hover {
    background-color: #0056b3; /* Darker blue on hover */
}

@media only screen and (max-width: 768px) {
    .navbar {
        text-align: center;
    }

    .btn-custom {
        width: 100%;
    }
}
</style>

<script>
export default {
    name: 'NavbarVue',
}
</script>
