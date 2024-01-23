<script>
import { store } from '../store.js'

export default {
    data() {
        return {

            active: 0,
            store,
            ouseX: 0,
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
        activeCount(n){
            let array = [n, n+1, n+2];

            for(let i = 0; i<array.length; i++){
                if(array[i]>3){
                    array[i] = array[i]-4;
                }
            }

            return array;
        },
        anotherCount(n){
            if(n == 4){
                return 0;
            }
            else{
                return n;
            }
        },
        mousePosition(event) {
            this.mouseX = event.clientX;
            this.mouseY = event.clientY;
        },
    }

}
</script>
<template lang="">
    <div class="bg py-5">
        <div class="container-fluid" @mousemove="mousePosition">
            <div class="row">
                <div class="col-12">
                    <div class="text-container">
                        <p>great words about maxcoach</p>
                        <strong>Our <span>top learnes'</span> verbatim</strong>
                    </div>
                </div>
                <div class="col-12">
                    <div class="swiper-container">
                        <div class="swiper-card" v-for="(slide, index) in activeCount(active)" :class="slide == anotherCount(active+1) ? 'active' : ''">
                            <p class="mb-3">{{store.carousell[slide].title}}</p>
                            <span>{{store.carousell[slide].paragraph}}</span>
                            <div class="profile">
                                <img :src="store.carousell[slide].img" :alt="store.carousell[slide].name">
                                <div class="profile-text">
                                    <p>{{store.carousell[slide].name}}</p>
                                    <span>{{store.carousell[slide].role}}</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="btn-container">
                        <div v-for="index in 4" :key="index" class="rounded-btn" :class="index-1 == active ? 'active' : ''" @click="active = index-1"></div>
                    </div>
                </div>
                <div class="col-12">
                    <div class="text-center mt-5">
                        <span class="violet-text">Start today for getting </span>
                        <span class="green-text">Online certification</span>
                        <h2>You can be own guiding star with our help!</h2>
                        <button class="btn my-btn my-4">Get stared now</button>
                    </div>
                </div>
            </div>
        </div>
        <img class="pattern-1" src="../images/maxcoach-shape-01.png" alt="pattern" :style="movingStyle">
        <img class="pattern-2" src="../images/maxcoach-shape-02.png" alt="pattern" :style="movingStyle">
    </div>
</template>
<style lang="scss" scoped>
@use './styles/generals.scss';
@use './styles/partials/variables' as*;

    .bg{
        background-color: $bg_carou-footer;
        position: relative;

        .pattern-1{
            position: absolute;
            bottom: 25%;
            left: 10%;
        }

        .pattern-2{
            position: absolute;
            bottom: 15%;
            right: 20%;
        }

        .text-container{
            text-align: center;
            margin: 50px 0;
            p{
                color: $dark_text;
                text-transform: uppercase;
                
            }
    
            strong{
                color: $main_violet;
                font-size: 35px;
                
    
                span{
                    color: $main_green;
                    font-weight: lighter;
                }
            }
        }

        .swiper-container{
            
            display: flex;
            

            .swiper-card{
                background-color: white;
                width: calc(100% / 3 - 80px);
                margin: 0 40px;
                padding: 30px;
                opacity: 0.5;

                &.active{
                    opacity: 1;
                }

                p{
                    color: $main_violet;
                    font-weight: bolder;
                }

                span{
                    color: $dark_text;
                    font-size: 12px;
                }

                .profile{
                    margin: 20px 0;
                    display: flex;
                    align-items: center;

                    img{
                        width: 20%;
                        border-radius: 50%;
                    }

                    .profile-text{
                        display: flex;
                        flex-direction: column;
                        margin-left: 20px;
                        justify-content: space-between;

                        p{
                            font-size: 12px;
                        }

                        span{
                            font-size: 10px;
                            color: grey;
                        }
                    }
                }
            }

            
        }

        .btn-container{
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 30px 0;

            .rounded-btn{
                width: 6px;
                height: 6px;
                border-radius: 50%;
                background-color: $violet_text;
                margin: 0 10px;

                &.active{
                    width: 10px;
                    height: 10px;
                    background-color: $main_violet;
                }
            }
        }

        .violet-text,
        h2{
            color: $main_violet;
        }

        .green-text{
            color: $main_green;
        }

        .my-btn{
            background-color: $main_green;
            color: white;
            font-weight: 600;
            padding: 10px 70px;

            &:hover{
                background-color: $main_violet;
            }
        }
    }
    
</style>