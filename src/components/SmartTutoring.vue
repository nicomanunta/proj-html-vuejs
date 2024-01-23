<script>
    import { store } from '../store';

    export default {
        name: 'SmartTutoring',
        data() {
            return {
                store
            }
        },
    }
</script>

<template>
    <div class="container py-4">

        <h6 class="my-2">
            Maxcoach Available Courses
        </h6>
        <h2 class="my-2">
            Access <span>Smart Tutoring</span> Program for Benefits.
        </h2>

        <div class="row">
            <div v-for="option, index in store.smartTutoring" :key="index" class="position-relative custom-column">
                <img :src="`${option.img}`" class="py-3">
                <h4>{{ option.title }}</h4>
                <div class="option-description pb-4">{{ option.description }}</div>
                <span class="option-button">
                    <div class="menu-text">
                        {{ option.button }} &#10140;
                    </div>
                </span>
            </div>
        </div>
    </div>

</template>

<style lang="scss" scoped>
@use './styles/partials/variables' as *;
@use './styles/partials/mixin' as *;

.custom-column{
    width: calc(100% / 3 - 3rem);
    margin: 1rem;

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

h6{
    @include teaser-title;
}

h2{
    @include important-title;

    span{
        color: $main_green;
    }
}

h4{
    color: $main_violet;
    font-weight: bolder;
}

.option-description{
    color: $dark_text;
}

.option-button{
    color: $dark_text;
    font-weight: bolder;
    position: absolute;
    bottom: 0;
}
</style>