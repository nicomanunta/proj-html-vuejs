<script>
import { store } from '../store'
export default {
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
    <div class="container my-pos" @mousemove="mousePosition">
        <div class="row">
            <div class="col-4 offset-4">
                <div class="text-container">
                    <strong>Subscribe <span>Newsletters</span></strong>
                    <p>Enter your email address to register to our newsletter subscription delivered on a regular basis!</p>
                    <div class="input-group mt-4">
                        <input type="email" class="form-control border border-0 bg-light" placeholder="Enter your email">
                        <button class="btn border border-start-0 my-bg" type="button" id="button-addon2">Subscribe</button>
                    </div>
                    <img class="moving-img-square" :style="movingStyle" src="../images/maxcoach-shape-07-100x100.png" alt="">
                    <img class="moving-img-circle" :style="movingStyle" src="../images/maxcoach-shape-02.png" alt="pattern">
                    <div class="circle" :style="movingStyle"></div>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
@use './styles/generals.scss';
@use './styles/partials/variables' as*;


    .my-pos{
        position: relative;
    }
    .text-container{
        text-align: center;
        margin: 50px 0;
        

        strong{
            font-size: 25px;
            color: $main_violet;
            span{
                color: $main_green;
                font-weight: lighter;
            }
        }
        
        p{
            color: $violet_text;
            font-size: 12px;
            margin: 10px 0;
        }
        
        input::placeholder{
            color: rgb(162, 162, 162);
            font-size: 12px;
        }
        .my-bg{
            background-color: $main_green;
            color: white;
            font-size: 8px;
            font-weight: 600;

            &:hover{
                background-color: $main_violet;
            }
        }
        .moving-img-square{
            width: 7%;
            position: absolute;
            bottom: 50%;
            right: 22% ;
            opacity: 0.5;
        }
        .moving-img-circle{
            width: 7%;
            position: absolute;
            bottom: 50%;
            right: 20%;
            z-index: 1;
        }
        .circle{
            position: absolute;
            bottom: 50%;
            left: 15%;
            height: 25%;
            width: 5%;
            color: $main_green;
            border-radius: 50%;
            border: 10px solid currentColor;
            opacity: 0.5;
        }
    }
    
</style>