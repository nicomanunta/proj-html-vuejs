<script>
import { store } from '../store'
import CardMostViewed from './CardMostViewed.vue';
export default {
    name: 'SectionMostViewed',
    components:{
        CardMostViewed
    },
    data() {
        return {
            store
        }
    },    
}
</script>
<template lang="">
    <div class="bg py-5">
        <div class="container">
            <div class="row">
                <div class="col-4">
                    <div class="list">
                        <p>ENJOYABLE INSIGHTS</p>
                        <span class="text">Most Viewed <span class="text-end">Best Blogs </span></span>
                        <ul>
                            <li><i class="fa-solid fa-arrow-right fa-2xs mt-5"></i>Become a Better Blogger: Content Planning</li>
                            <li><i class="fa-solid fa-arrow-right fa-2xs"></i>Promoting Your Online Business on Pinterest</li>
                            <li><i class="fa-solid fa-arrow-right fa-2xs"></i>Gamification and Game-Based Learning</li>
                            <li><i class="fa-solid fa-arrow-right fa-2xs"></i>Designing an Online Course from Expert's Perspective</li>
                            <li><i class="fa-solid fa-arrow-right fa-2xs"></i>Why Online Courses Are the Future of Education</li>
                        </ul>
                    </div>
                </div>
                <div class="col-8">
                    <div class="my-card d-flex justify-content-around my-5" >
                        <CardMostViewed  v-for="date, index in store.MostViewed" :key="index" :date="date"/>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
@use '../components/styles/partials/variables' as *;
.bg{
    background-color: $bg_mostviewed;
    .list{
       margin-top: 120px; 
    }
    p{
        color: $violet_text;
    }
    .text{
        font-size: 35px;
        font-weight: bold;
    }
    .text-end{
        font-weight: 400;
        color: $main_green;
    }
    ul{
        list-style: none;
        padding-left: 0px;

        li{
            font-weight: bold;
            margin-bottom: 20px;
            .fa-solid{
                margin-right: 20px;
            }
        }
        li:hover{
            color: $main_green;
        }
    }
    .my-card{
        width: 100%;
        flex-wrap: nowrap;
        margin-left: 50px;
        
    }
}
    
</style>