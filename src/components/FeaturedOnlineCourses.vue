<script>
    import { store } from '../store';
    import CourseCard from './CourseCard.vue';

    export default {
        name: 'FeaturedOnlineCourses',
        components:{
            CourseCard,
        },
        data() {
            return {
                store
            }
        },
    }
</script>

<template>
<div class="background">
    <div class="container py-4">
        <h6 class="my-2">
            Stimulated to learn?
        </h6>
        <h2 class="my-2">
            Featured Online Courses
        </h2>

        <div class="row">
            <CourseCard v-for="course, index in store.featuredCourses" :key="index" :course="course"/>
        </div>

        <div class="d-flex justify-content-center">
            <div class="btn view-button">View all courses &#10140;</div>
        </div>
    </div>
</div>
</template>

<style lang="scss" scoped>
@use './styles/partials/variables' as *;
@use './styles/partials/mixin' as *;

.background{
    background-color: #F5F7FA;
    .container{
        h6{
            @include teaser-title;
        }

        h2{
            @include important-title;
        }

        .view-button{
            background-color: $main_green;
            color: white;
            padding: 1rem 3rem;

            &:hover{
                background-color: $main_violet;
                transition: 0.25s;
            }
        }
    }
}
</style>