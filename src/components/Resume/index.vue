<script>
const currencyFormater = new Intl.NumberFormat(("es-CO"), {
  style: "currency", currency: "COP"
})
export default {
    props: {
        totalLabel: {
            type: String,
        },
        label: {
            type: String,
            default: null,
        },
        totalAmount: {
            type: Number,
        },
        amount: {
            type: Number,
            default: null
        },
    },
    computed: {
        labelVisual() {
            return this.label !== null ? this.label : this.totalLabel; 
        },
        amountVisual() {
            return this.amount !== null ? this.amount : this.totalAmount;
        },
        amountCurrency() {
            return currencyFormater.format(this.amountVisual)
        }
    },
};
</script>

<template>
    <main>
        <p>{{ labelVisual }}</p>
        <h1>{{ amountCurrency }}</h1>
        <div class="graphic">
            <slot name="graphic"></slot>
        </div>
        <div class="action">
            <slot name="action"></slot>
        </div>
    </main>
</template>

<style scoped>
    main {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        width: 100%;
    }

    h1,
    p {
        margin: 0;
        text-align: center;
    }

    p {
        color: #529fdf;
        font-size: 16px;
        font-weight: 300;
    }

    h1 {
        margin-top: 14px;
        color: #76e7b8;
    }

    .graphic {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        padding: 48px 24px;
        box-sizing: border-box;
    }
</style>