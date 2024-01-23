<script>
export default {
    name: 'AppFooter',
    data() {
        return {
            showBtn: false,
            addresses: [
                {
                    label: "382 NE 191st St # 87394 Miami, FL 33179-3899",
                    url: "#"
                },
                {
                    label: "+1 (305) 547-9909 (9am - 5pm EST, Monday - Friday)",
                    url: "#"
                },
                {
                    label: "support@maxcoach.com",
                    url: "#"
                }
            ],
            explore: [
                {
                    label: "Start here",
                    url: "#"
                },
                {
                    label: "Blog",
                    url: "#"
                },
                {
                    label: "About us",
                    url: "#"
                },

            ],
            explore2: [
                {
                    label: "Success story",
                    url: "#"
                },
                {
                    label: "Courses",
                    url: "#"
                },
                {
                    label: "Contact us",
                    url: "#"
                },
            ],
            information: [
                {
                    label: "Membership",
                    url: "#"
                },
                {
                    label: "Purchase guide",
                    url: "#"
                },
                {
                    label: "Privacy policy",
                    url: "#"
                },
                {
                    label: "Terms of services",
                    url: "#"
                },
            ]

        }
    },
    methods: {
        // funzione richiamata sul button, per tornare all'inizio della pagina
        scrollStart() {
            window.scrollTo(0, 0);
        }
    },
    created(){
        var scrollBefore = 0;
        window.onscroll = ()=>{
            const scrolled = window.scrollY;

            if(scrollBefore > scrolled){
                this.showBtn = true;
                scrollBefore = scrolled;
            }else{
                scrollBefore = scrolled;
                this.showBtn = false;
            }
        }
    }
}
</script>
<template lang="">
    <footer>
        <div class="container">
            <div class="row">
                <div class="col-6">
                    <h6 class="mb-3">Address</h6>

                    <ul>
                        <li v-for="address, index in addresses" :key="index">
                            {{address.label}}
                        </li>
                        <li class="mt-3 ">
                            <span class="me-4"><i class="fa-brands fa-square-facebook"></i></span>
                            <span class="me-4"><i class="fa-brands fa-twitter"></i></span>
                            <span class="me-4"><i class="fa-brands fa-instagram"></i></span>
                            <span class=""><i class="fa-brands fa-linkedin"></i></span>
                        </li>
                    </ul>
                </div>
                <div class="col-3">
                    <div class="row">
                        <h6 class="mb-3">Explore</h6>
                        <div class="col-6">
                            <ul class="color-hover">
                                <li v-for="ex, index in explore" :key="index">
                                    {{ex.label}}
                                </li>
                            </ul>
                        </div>
                      <div class="col-6">
                            <ul class="color-hover">
                                <li v-for="ex2, index in explore2" :key="index">
                                    {{ex2.label}}
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
                <div class="col-3">
                    <h6 class="mb-3">Information</h6>
                    <ul class="color-hover">
                        <li v-for="info, index in information" :key="index">
                            {{info.label}}
                        </li>
                    </ul>
                </div>
            </div>
        </div>
        <div class="text-center mt-4">
            <span class="scritta-piccola">&copy;2020 Maxcoach. All Rights Reserved</span>
        </div>
        <button type="button" class="btn" @click="scrollStart" v-show="showBtn">&uarr;</button>
    </footer>
</template>
<style lang="scss" scoped>
@use "./styles/generals.scss" as *;
@use "./styles/partials/variables" as *;

footer {
    background-color: $bg_carou-footer;
    padding: 40px 0px;
    position: relative;
}

li {
    color: rgba(177, 177, 177, 255);
    list-style: none;
    font-size: 12px;
    padding-bottom: 10px;
    cursor: pointer;
}

span {
    font-size: 24px;
    color: rgba(177, 177, 177, 255);
}

.scritta-piccola {
    font-size: 10px;
}

button {
    background-color: $main_green;
    color: white;
    border-radius: 50px;
    position: fixed;
    bottom: 40px;
    right: 40px;
    box-shadow: 2px 2px 2px #dedede;
    z-index: 1;

    &:hover {
        color: $main_green;
        background-color: white;
    }
}

.color-hover {
    li:hover {
        color: $main_green;
    }
}
</style>