<template>
    <tr>
        <td class="row">{{index + 1}}</td>
        <td class="row">{{product.title}}</td>
        <td class="row">{{product.date}}</td>
        <td class="row">{{product.count}}</td>
        <td class="row">{{product.price}}</td>
        <td class="row">{{product.summ}}</td>
        <td class="row row--btn">
            <button class="remove" v-on:click="$emit('remove-product', product.id)">
                &times;
            </button>
        </td>
    </tr>
</template>

<script>
export default {
    props: {
        product: {
            type: Object,
            required: true
        },
        index: Number
    }
}
</script>

<style scoped>

tr {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.row {
    flex-basis: calc(100% / 7);
    text-align: left;
    margin-left: 10px;
}

.row:first-child {
    margin-left: 0;
}

.remove {
    display: block;
    width: 35px;
    height: 35px;
    border: none;
    border-radius: 50%;
    background: rgb(255, 94, 94);
    color: #fff;
    font-size: 1.1rem;
    cursor: pointer;
    outline: none;
    transition: background .1s linear;
}

.remove:hover {
    background: rgb(255, 139, 139);
}

</style>