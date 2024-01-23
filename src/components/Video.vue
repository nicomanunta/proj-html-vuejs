<script>
export default {
    data() {
        return {
            mouseX: 0,
            mouseY: 0,
        };
    },
    computed: {
        movingFirstStyle() {
            let translateX = (this.mouseX / 10);
            let translateY = (this.mouseY / 10);

            return {
                transform: `translate(${translateX}px, ${translateY}px)`,
                transition: 'transform 0.3s ease-out',
            };
        },
        movingSecondStyle() {
            let translateX = (this.mouseX / 30);
            let translateY = (this.mouseY / 30);

            return {
                transform: `translate(${translateX}px, ${translateY}px)`,
                transition: 'transform 0.3s ease-out',
            };
        },
    },
    methods: {
        mousePosition(event) {
            this.mouseX = event.clientX;
            this.mouseY = event.clientY;
        },
    },
}
</script>
<template lang="">
    <div class="bg-radial " @mousemove="mousePosition">
        <div class="container py-5 container-img">
            <div class="row ">
                <div class="col-7 d-flex justify-content-end">
                    <div class="col-img">
                        <img class="video" src="../images/home-2-popup-video-poster.jpg" alt="">
                    </div>
                        <img class="youtube"  src="../images/icon-youtube-play.png" alt="">
                    <div>
                        <img class="moving-img-square" :style="movingSecondStyle" src="../images/maxcoach-shape-07-100x100.png" alt="">
                        <svg class="moving-img-cloud" :style="movingFirstStyle" xmlns="http://www.w3.org/2000/svg" version="1.1" width="200px" height="202px" viewBox="0 0 200 202">
                            <path class="elementor-shape-fill color-cloud" d="M139.374493,198.087515 C155.702187,206.99353 190.724846,197.001323 197.677982,159.049528 C204.827153,120.027728 184.496324,118.997566 188.045232,104.801934 C202.287755,83.6528313 204.827153,56.662651 190.073179,40.4146034 C153.570125,2.39058926 144.444362,48.0194062 114.025151,20.1351292 C101.727304,7.83728238 83.0989526,-6.73517414 56.2286492,3.40456297 C18.2385839,17.7404371 27.3303985,47.659333 27.3303985,69.3128542 C27.3303985,76.9370868 3.11408002,91.2696589 0.460095291,110.885776 C-2.88628833,135.619549 12.6277797,168.175291 27.3303985,179.329002 C50.6517938,205.692318 86.6478605,199.608476 102.87144,190.482713 C116.802125,182.646702 128.220783,192.003673 139.374493,198.087515 Z"></path>
                        </svg>
                        <img class="moving-img-rombo" :style="movingSecondStyle" src="../images/maxcoach-shape-05.png" alt="">
                        <div class="circle" :style="movingFirstStyle"></div>
                        
                    </div>
                </div>
                <div class="col-4 z-2 ">   
                    <h6 class="my-3">get started <b>effortlessly</b></h6>
                    <h1 class="mb-3"><span class="enjoy"><b>Enjoy Our</b></span> <span class="companionship">Companionship</span></h1>
                    <span class="sneek">Sneek peek into what has in store fot you on our online teaching and mentoring portal. Seek for some hidden hints of early-bird rewards as well.</span>
                    <div class="mt-4">
                        <a href="#">Download free guidebook &rarr;</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
</template>
<style lang="scss" scoped>
@use "./styles/generals.scss";
@use "./styles/partials/variables" as *;




.bg-radial {
    background-image: radial-gradient(ellipse farthest-corner at -7% -16%, white 82%, #F5F7FA 44%);
}

.col-img {
    z-index: 2;
    max-width: 100%;
    overflow: hidden;
    position: relative;

    .video {
        width: 500px;
        transition: transform 1.5s ease;


        &:hover {
            transform: scale(1.1);
        }
    }

}

.container-img {
    position: relative;
}


.moving-img-square {
    width: 100px;
    height: 100px;
    position: absolute;
    bottom: 20px;
    left: 610px;

}

.moving-img-cloud {
    position: absolute;
    top: -20px;
    left: 80px;

}

.moving-img-rombo {
    position: absolute;
    bottom: 100px;
    left: 100px;

}

.circle {
    height: 82px;
    width: 82px;
    color: #ECC5AB;
    border-radius: 50%;
    border: 10px solid currentColor;
    position: absolute;
    right: 600px;
    top: 10px;

}


.youtube {
    width: 80px;
    height: 60px;
    position: relative;
    top: 38%;
    right: 38%;
    z-index: 3;

    &:hover {
        cursor: pointer;
    }
}

.color-cloud {
    fill: rgba(229, 199, 145, 255);
}

h6 {
    color: $main_violet;
    text-transform: uppercase;
}

.enjoy {
    color: $main_violet;
}

.companionship {
    color: $main_green;
}

.sneek {
    color: $dark_text;
}

a {
    color: $main_green;
}
</style>

