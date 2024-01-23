<script>
import { store } from '../store'
export default {
    name: 'Jumbotron',
    data() {
        return {
            store,
            mouseX: 0,
            mouseY: 0,
        }
    },
    computed: {
        movingStyle() {
            let translateX = (this.mouseX / 10);
            let translateY = (this.mouseY / 10);

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
    <div class="container" @mousemove="mousePosition">
        <div class="row">
            <div class="col-6">
                <div class="content p-5">
                    <h1>Distant learning for further expansion</h1>
                    <p>Learning is a life-long journey that in fact we never find the terminate stop. Stop searching, enjoy the process.</p>
                    <button class="btn my-3 py-3 px-5"><i class="fa-solid fa-download" style="color: #ffffff;"></i> Download free guide</button>
                    <div class="menu-text">
                        <span class="py-2 text"><a class="link" href="#">Have questions?</a>    <a href="#">Get Free Sample <i class="fa-solid fa-arrow-right" style="color: #20ad96;"></i></a></span>
                    </div>
                </div>
            </div>
            <div class="col-6">
                <div class="image">
                    <img class="profile" src="../images/about-me-profile-ohm4dxoearqbxny7q3bq1pzbdgofdx0tobbeqcvzd0.jpg" alt="">
                </div>
                <div>
                    <img class="moving-img-square" :style="movingStyle" src="../images/maxcoach-shape-07-100x100.png" alt="">
                    <img class="moving-img-circle" :style="movingStyle" src="../images/maxcoach-shape-02.png" alt="">
                    <div class="circle" :style="movingStyle"></div>
                </div>
            </div>
            <div class="col-12">
                <div class="content-logo d-flex justify-content-around ; mt-5">
                    <img class="logo" src="../images/client-logo-01.png" alt="">
                    <img class="logo" src="../images/client-logo-02.png" alt="">
                    <img class="logo" src="../images/client-logo-03.png" alt="">
                    <img class="logo" src="../images/client-logo-04.png" alt="">
                    <img class="logo" src="../images/client-logo-05.png" alt="">
                    <img class="logo" src="../images/client-logo-06.png" alt="">
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
@use './styles/partials/variables' as *;

.content {
    margin-top: 150px;

    h1 {
        font-weight: bold;
        font-size: 50px;
    }

    p {
        font-size: 22px;
        color: $violet_text;
        padding-top: 10px;
    }

    button {
        font-weight: bold;
        background-color: $main_green;
        color: white;
    }

    button:hover {
        background-color: #3F3A64;
    }

    span {
        display: block;
        font-size: 17px;
        color: $violet_text;

        .link {
            color: $violet_text;
        }

        a {
            color: $main_green;
            text-decoration: none;
            font-weight: bold;
        }
    }
    .menu-text{
        width: 300px;
    }
    .menu-text:after {
        transition: all ease-in-out .2s;
        background: none repeat scroll 0 0 rgb(193, 202, 206);
        display: block;
        height: 1px;
        width: 0;
        content: "";
    }


    &:hover{
        cursor: pointer;

        .menu-text:after{
            width: 100%;
        }
        
        .option-button{
            color: $main_green;
        }
    }
}

.profile {
    border-radius: 50%;
    margin-top: 50px;
    margin-left: 50px;
}

.logo {
    margin-top: 50px;
    opacity: 0.5;
    height: 100%;
}

.logo:hover {
    opacity: 1;
}

.content-logo {
    margin-bottom: 50px;
}
.moving-img-square {
    width: 300px;
    height: 300px;
    position: absolute;
    bottom: 300px;
    right: 600px;
    z-index: -1;
}

.moving-img-circle {
    position: absolute;
    top: 250px;
    left: 1250px;
    z-index: 1;
}
.circle{
    position: absolute;
    top: 600px;
    left: 700px;
    height: 75px;
    width: 75px;
    border-radius: 50%;
    border: 10px solid rgb(240, 175, 56);
    opacity: 0.5;
    z-index: 1;
}

</style>