<script>
export default {
    name: 'ImgCarousel',
    data() {
        return {
            slogans: [
                { 'title': 'Hai fame?', 'subtitle': 'ci pensiamo noi!' },
                { 'title': 'Scegli', 'subtitle': 'fra i ristoranti della tua città' },
                { 'title': 'Con un click', 'subtitle': 'potrai soddisfare il tuo palato' },
                { 'title': 'Facile', 'subtitle': 'come un download!' }
            ]
        }
    }
}
</script>

<template>
    <!-- carousel -->
    <div id="carousel" class="carousel slide" data-bs-touch="false" data-bs-ride="carousel" data-bs-interval="2200">
        <!-- slides -->
        <div id="jumbotron" class="carousel-inner">
            <div v-for="(slogan, index) in slogans " class="carousel-item active">
                <div id="positioner" class="container">
                    <h1>{{ slogan.title }} <br>
                        <span>{{ slogan.subtitle }}</span>
                    </h1>
                </div>
                <img :src="`img/slider/cs-banner-${index}.png`" class="d-block w-100" alt="immagine copertina">
            </div>

        </div>

        <!-- slider buttons -->
        <button class="carousel-control-prev" type="button" data-bs-target="#carousel" data-bs-slide="prev">
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Previous</span>
        </button>
        <button class="carousel-control-next" type="button" data-bs-target="#carousel" data-bs-slide="next">
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Next</span>
        </button>
    </div>

    <!-- orange border -->
    <div class="brd-decoration"></div>
</template>

<style lang="scss" scoped>
img {
    height: 580px;
    object-fit: cover;
}

h1 {
    color: white;
    text-shadow: 0 5px 10px rgba(0, 0, 0, 0.4);
    font-size: 6rem;

    position: absolute;
    top: 120px;
}

span {
    font-size: 3rem;

    position: relative;
    bottom: 35px;
}

#jumbotron {
    position: relative;
}

#positioner {
    margin: 0 auto;
    position: relative;
}

.brd-decoration {
    height: 12px;
    background-color: var(--d-orange);
}

//media query
@media screen and (max-width: 600px) {
    #jumbotron {
        height: 330px;
    }

    img {
        height: 330px;
        object-fit: cover;
    }

    h1 {
        top: 60px;
        left: 20px;
        font-size: 3rem;
    }

    span {
        font-size: 1.5rem;

        position: relative;
        bottom: 20px;
    }
}
</style>
