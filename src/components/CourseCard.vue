<script>
    export default {
        props:{
            course: Object,
        }
    }
</script>

<template>
<div class="col-6 d-flex my-4 p-4">
    <div class="image-container">
        <img :src="`${course.img}`" class="round-image">
    </div>
    <div class="data-container">
        <div class="price">
            {{ course.price }}<span v-if="course.priceCents != ''" class="price-cents">{{ course.priceCents }}</span>
        </div>
        <div class="title">
            {{ course.title }} 
        </div>
        <span class="sub-data">
            <i class="far fa-file-alt" /> {{ course.lessons }} Lessons 
        </span>
        <span class="sub-data">
            <i class="far fa-user" /> {{ course.students }} Students 
        </span>
    </div>
</div>
</template>

<style lang="scss" scoped>
@use './styles/partials/variables' as *;
div{
    .image-container{
        height: 175px;
        width: 175px;
        aspect-ratio: 1 / 1;
        .round-image{
            height: 100%;
            width: 100%;
            object-fit: cover;
            border-radius: 50%;
        }
    }
    .data-container{
        padding: 2rem;
        .price{
            font-size: 20px;
            font-weight: bold;
            color: $main_green;
            
            .price-cents{
                font-size: 15px;
            }
        }
    
        .title{
            font-size: 20px;
            font-weight: bold;
            color: $main_violet;
        }
    
        .sub-data{
            font-size: 15px;
            color: $dark_text;
        }
    }

    &:hover{
        cursor: pointer;
        background-color: white;
        transition: 0.25s;
    }
}

</style>