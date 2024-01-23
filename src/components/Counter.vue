<script>
export default {
    data() {
        return {
            counter: [
                {
                    string: "Successfully trained",
                    number: "1790",
                    area: "enrolled learners"
                },
                {
                    string: "Proudly Received",
                    number: "19",
                    area: "contrywide awards"
                },
                {
                    string: "Firmly Established",
                    number: "24",
                    area: "local branches"
                },
                {
                    string: "Getting Feutured on",
                    number: "1090",
                    area: "blog posts"
                }
            ],

        }
    },
    created() {
        //chiamo la funzione handlescroll quando scrollo 
        window.addEventListener('scroll', this.handleScroll);
    },
    //utilizzo unmounted che viene chiamato quando la componente viene rimossa dal DOM
    unmounted() {
        //rimuovo l'eventlistener che viene chiamato in created 
        window.removeEventListener('scroll', this.handleScroll);
    },

    methods: {
        handleScroll() {
            // verifica quando il componente è visibile nella finestra di visualizzazione utilizzando $el (proprietà di Vue.js che rappresenta l'elemento DOM associato al componente Vue)
            let element = this.$el;
            let windowHeight = window.innerHeight; //altezza della finestra
            //element.getBoundingClientRect() restituisce la dimensione di un elemento e la sua posizione rispetto al viewport. Aggiungendo ".top" si avrà la distanza tra il bordo superiore dell'elemento e il bordo superiore della finestra di visualizzazione
            let top = element.getBoundingClientRect().top;

            // faccio un if, per verificare se la parte superiore del componente è visibile nella finestra di visualizzazione
            if (top < windowHeight) {
                // il componente è visibile, si avvia l'animazione del contatore
                this.startCounterAnimation();
                // rimuove l'event listener una volta che l'animazione è stata avviata
                window.removeEventListener('scroll', this.handleScroll);
            }
        },
        // animazione del contatore 
        startCounterAnimation() {
            this.counter.forEach((count, index) => {
                this.animateCounter(parseInt(count.number), index);
            });
        },

        animateCounter(targetNumber, index) {
            let duration = 2000; // Durata dell'animazione in millisecondi

            // determino la quantità di incremento del contatore in ogni intervallo di tempo, calcolandolo in base al numero finale desiderato (targetNumber) e alla durata totale dell'animazione (duration)
            let step = Math.ceil(targetNumber / (duration / 16));

            let currentNumber = 0;

            let interval = setInterval(() => {
                currentNumber += step; //incremento il valore di currentNumber 

                if (currentNumber >= targetNumber) {
                    currentNumber = targetNumber;
                    clearInterval(interval);
                }

                this.counter[index].number = currentNumber.toString();

            }, 16);
        },
    },

}
</script>
<template lang="">
    
    <div class="container moving-background" >
        <div class="row">
            <div class="bordi col-3 d-flex flex-column align-items-center " v-for="count, index in counter">
                <h4 class="my-3 text-center " >{{count.string}}</h4>
                <h5 class="mt-3">{{count.number}}</h5>
                <h6 class="my-3">{{count.area.toUpperCase()}}</h6>
            </div>       
        </div>
    </div>
    
</template>
<style lang="scss" scoped>
@use "./styles/generals.scss" as *;
@use "./styles/partials/variables" as *;

.container {
    font-family: 'Gilroy-bold', sans-serif
}

.bordi {
    border-left: 1px solid $bg_cardSection;
    border-right: 1px solid $bg_cardSection;
    padding: 80px 0px;
}

h4 {
    width: 50%;
    color: $main_violet;

}

h5 {
    color: $main_green;
    font-size: 45px;
    font-weight: 900;
    font-family: 'Gilroy-bold', sans-serif;
}

h6 {
    color: rgba(177, 177, 177, 255);
    font-size: 12px;
    font-weight: 600;
    letter-spacing: 2px;
}
</style>
