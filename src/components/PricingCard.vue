<template>
    <article class="card">
        <h4>{{ subPlan }}</h4>
        <div class="price-container">
            <span class="currency">$</span>
            <p class="monthly-price" ref="mthPrice">{{ mthPrice }}</p>
            <p class="annually-price">{{ yearPrice }}</p>
        </div>
        <ul>
            <li>{{ storage }} Storage</li>
            <li>{{ nbUsers }} Users Allowed</li>
            <li>Send up to {{ sendable }} GB</li>
        </ul>
        <a href="#" class="btn">Learn More</a>
    </article>
</template>

<script>
export default {
    name: 'PricingCard',
    props: ["subPlan", "mthPrice", "yearPrice", "storage", "nbUsers", "sendable"]
}
</script>

<style lang="scss" scoped>
.card {
    background: $white;
    width: 100%;
    text-align: center;
    margin: 25px auto;
    padding: 20px 30px;
    border-radius: 8px;

    &:first-child, &:last-child {
        @include box-shadow (5px 5px 21px 10px rgba(0,0,0,0.09));
    }
    &.Professional {
        background: $purple-linear-gradient;
        color: $white;

        .price-container p, .price-container span {
            color: $white;
        }
        ul li, ul li:last-child {
            border-color: $white-alpha25;
        }
        a.btn {
            background: $white;
            color: $dark-pale-purple;

            &:hover {
                color: $white;
                @include box-shadow(0px 0px 0px 2px $white inset);
            }
        }

        @include respond(large) {
            padding: 45px 30px;
        }
    }
    > * {
        margin: 20px auto;
    }
    .price-container {
        display: flex;
        align-items: center;
        justify-content: center;

        .currency {
            font-size: 2.5em;
            font-weight: 700;
            color: $dark-grayish-blue;
            margin: 5px;
        }
        p {
            color: $dark-grayish-blue;
            font-size: 4.4em;
            font-weight: 700;

            &.monthly-price {
                display: none;
            }
            &.annually-price {
                display: inline-block;
            }
        }
    }
    ul li {
        list-style-type: none;
        border-top: 1px solid $light-grayish-blue-alpha25;
        padding: 15px;

        &:last-child {
            border-bottom: 1px solid $light-grayish-blue-alpha25;
        }
    }
    a.btn {
        display: block;
        text-decoration: none;
        text-transform: uppercase;
        letter-spacing: 0.1em;
        font-size: 0.85em;
        color: $white;
        margin-top: 40px;
        padding: 14px;
        background: $purple-linear-gradient;
        border-radius: 8px;
        transition: all .3s ease-in-out;

        &:hover {
            color: $dark-pale-purple;
            background: transparent;
            
            @include box-shadow(0px 0px 0px 2px $dark-pale-purple inset);
        }
    }

    @include respond(large) {
        max-width: 350px;
        margin: 25px 0;
    }
}
</style>