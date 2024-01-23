<script>
import { store } from '../store'
export default {
    name: 'CardMostViewed',
    props: {
        date: Object
    },
    data() {
        return {
            store
        }
    },    
}
</script>
<template lang="">
    <div class="card">
        <div class="image">
            <img :src="date.img" alt="">
        </div>
        <div class="info">
            <h5>{{ date.work }}</h5>
            <h3>{{ date.articol }}</h3>
            <div class="date-end d-flex justify-content-between mt-4">
                <span><i class="fa-regular fa-calendar fa-2xs" style="color: #707070;"></i> {{ date.data }}</span>
                <span><i class="fa-solid fa-eye fa-2xs" style="color: #737373;"></i> {{ date.views }}</span>
            </div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
@use '../components/styles/partials/variables' as *;
.card{
    width: calc(100% / 2 - 10px);
    border: none;
    border-radius: 10px;
    margin: 20px;
    .image{
        max-width: 100%;
        overflow: hidden;

        img{
            width: 100%;
            transition: transform 1.5s ease;
            
        }
        &:hover img{
            transform: scale(1.1);
        }
    }
    .info{
        padding: 30px;
        h5{
            color: $violet_text;
            font-weight: 600;
        }
        h3{
            font-weight: 600;
        }
        span{
            font-size: 18px;
            color: $violet_text;
        }
    }
}
</style>