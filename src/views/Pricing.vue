<template>
    <section>
        <h2>Our Pricing</h2>
        <div id="toggle-container">
            <input @click="changeDisplay" type="checkbox" name="" id="" ref="input">
            <div id="toggle">
                <div id="toggle-btn" ref="toggleBtn"></div>
            </div>
            <span>Annually</span>
            <span>Monthly</span>
        </div>
        <div class="cards-container">
            <PricingCard v-for = "card in cards" :key="card.subPlan" :ref="card.reference"
                :class = "card.subPlan"
                :subPlan="card.subPlan" 
                :mthPrice="card.mthPrice" 
                :yearPrice="card.yearPrice"
                :storage="card.storage" 
                :nbUsers="card.nbUsers" 
                :sendable="card.sendable" 
            />
        </div>
        <div class="attribution">
            <p>
                Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>.
                <br/>
                Coded by <a href="https://github.com/MehdiT-dev">Mehdi Tadjer</a>.
            </p>
        </div>
    </section>
</template>

<script>
import PricingCard from '@/components/PricingCard.vue'
export default {
    name: 'Pricing',
    components: {
        PricingCard
    },
    data() {
        return {
            cards: [
                {
                    subPlan: 'Basic',
                    mthPrice: '19.99',
                    yearPrice: '199.99',
                    storage: '500 GB',
                    nbUsers: '2',
                    sendable: '3',
                    reference: 'card',
                },
                {
                    subPlan: 'Professional',
                    mthPrice: '24.99',
                    yearPrice: '249.99',
                    storage: '1 TB',
                    nbUsers: '5',
                    sendable: '10',
                    reference: 'card',
                },
                {
                    subPlan: 'Master',
                    mthPrice: '39.99',
                    yearPrice: '399.99',
                    storage: '2 TB',
                    nbUsers: '10',
                    sendable: '20',
                    reference: 'card',
                }
            ]
        };
    },
    methods: {        
        changeDisplay: function() {
            if (this.$refs.input.checked) {
                this.$refs.toggleBtn.style.float = 'right';
                for (let i=0; i<this.$refs.card.length; i++) {
                    this.$refs.card[i].$el.children[1].children[1].style.display = 'inline-block';
                    this.$refs.card[i].$el.children[1].children[2].style.display = 'none';
                }
            } else {
                this.$refs.toggleBtn.style.float = 'left';
                for (let i=0; i<this.$refs.card.length; i++) {
                    this.$refs.card[i].$el.children[1].children[1].style.display = 'none';
                    this.$refs.card[i].$el.children[1].children[2].style.display = 'inline-block';
                }
            }
        }
    }
}
</script>

<style lang="scss" scoped>
section {
    background-image: url(@/assets/bg-top.svg), url(@/assets/bg-bottom.svg);
    background-repeat: no-repeat, no-repeat;
    background-position: right -200px top -40px, bottom -1000px left;
    padding: 0 20px;

    @include respond(large) {
        background-position: top right, bottom left;
    }
}
h2 {
    text-align: center;
    font-size: 1.8em;
    padding-top: 80px;
}
#toggle-container {
    position: relative;
    display: flex;
    justify-content: space-around;
    align-items: center;
    max-width: 300px;
    margin: 50px auto 30px;

    input {
        position: relative;
        cursor: pointer;
        order: 1;
        width: 50px;
        height: 30px;
        opacity: 0;

        &:hover + #toggle {
            opacity: 0.5;
        }
    }
    #toggle {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        height: 30px;
        width: 50px;
        border-radius: 50px;
        background: $purple-linear-gradient;
        transition: all .5s ease;

        #toggle-btn {
            background: $white;
            height: 23px;
            width: 23px;
            border-radius: 50px;
            margin: 4px 4px;
            float: left;
            transition: all .5s ease;
        }
    }
    span {
        color: $light-grayish-blue;

        &:last-child {
            order: 2;
        }
    }
}
.cards-container {
    margin-top: 50px;

    @include respond(large) {
        display: flex;
        align-items: center;
        justify-content: center;
    }
}
.attribution {
    text-align: center;
    padding: 10px 10px 30px;
    font-size: 0.75em;
    color: $dark-grayish-blue;
    
    a {
        color: $dark-pale-purple;
        text-decoration: none;

        &:hover {
            color: $light-pale-purple;
        }
    }
}
</style>