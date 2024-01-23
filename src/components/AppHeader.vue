<script>
import { store } from '../store'
export default {
    name: 'AppHeader',
    data() {
        return {
            store
        }
    },
}
</script>
<template lang="">
    <header>
        <div class="fixed-container">
            <div class="container">
                <div class="row">
                    <div class="col-12">
                        <div class="navbar-container">
                            <img src="../images/dark-logo.png" alt="logo">
                            <div class="dinamic-container">
                                <ul class="d-flex">
                                    <li>
                                        <button class="btn dropdown-toggle" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasTop" aria-controls="offcanvasTop">Home</button>

                                        <div class="offcanvas offcanvas-top m-header" tabindex="-1" id="offcanvasTop" aria-labelledby="offcanvasTopLabel">
                                            <div class="offcanvas-header">
                                                <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
                                            </div>
                                            <div class="offcanvas-body d-flex justify-content-between">
                                                <div class="ul-container">
                                                    <ul>
                                                        <li class="p-2 me-5" v-for="(submenu, index) in store.offcanvasMenu" :key="index">
                                                            {{submenu}}
                                                        </li>
                                                    </ul>
                                                </div>
                                                <div class="img-off-container">
                                                    <img class="off-img" src="../images/homepages-mega-menu-image-alt.jpg" alt="off-img"> 
                                                </div>
                                            </div>
                                        </div>
                                    </li>
                                    <li v-for="(item, index) in store.items" :key="index">
                                        <div class="dropdown">
                                            <button class="btn border border-0 dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
                                                {{item}}
                                            </button>
                                            <ul class="dropdown-menu w">
                                                <li class="p-4" v-for="(submenu, subIndex) in store.MenuList[index]" :key="subIndex">
                                                    {{submenu}}
                                                </li>
                                            </ul>
                                        </div>
                                    </li>
                                    <li class="mt-2"><i class="fa-regular fa-circle-user"></i></li>
                                </ul>
                                <div class="input-group ms-4">
                                    <input type="text" class="form-control border border-end-0 bg-l" placeholder="Search...">
                                    <button class="btn border border-start-0 bg-l" type="button" id="button-addon2"><i class="fa-solid fa-magnifying-glass green-glass"></i></button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>
<style lang="scss" scoped>
@use './styles/generals.scss';
@use './styles/partials/variables' as*;

.w {
    width: 250px;
    max-height: 500px;
    overflow: scroll;
}




.fixed-container{
    position: fixed;
    z-index: 999;
    width: 100%;
    background-color: white;
    box-shadow: 0 3px rgb(230, 229, 229);
}
   

.navbar-container {
    margin: 20px 0;
    display: flex;
    justify-content: space-between;
    align-items: center;

    img {
        width: 15%;
        cursor: pointer;
    }
    li:hover{
        color: $main_green
    }

    .dinamic-container {

        display: flex;
        justify-content: space-between;
        align-items: center;


        img{
            width: 15%;
            cursor: pointer;
        }
        li{

            &:hover{

                border-bottom: 1px solid $main_green;
    
                button:hover {
                    color: $main_green;
                }
    
                i:hover {
                    color: $main_green;
                }
            }

            .offcanvas.offcanvas-top.m-header{
            max-width: 1320px;
            margin: 80px auto;
            height: 500px;


                .offcanvas-body{
                    overflow-y: unset;
                    .ul-container{
                        height: 100%;

                        ul{
                            columns: 2 auto;
    
                            li:hover{
                                border: none;
                            }
                        }
                    }
    
                    .img-off-container{
    
                        .off-img{
                            width: 100%;
                        }
                    }
                }


            }

        }
        .bg-l {
            background-color: rgb(235, 234, 234);

            &::placeholder {
                color: rgb(185, 185, 185);
            }

            .green-glass {
                color: $main_green;


            }
        }

        button.bg-l:hover {
            background-color: $main_green;

            .green-glass {
                color: white;
            }
        }
        
    }
}
</style>