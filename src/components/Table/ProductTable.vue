<template>
    <div>
        <table>
            <tr class="table-header">
                <th>№</th>
                <th>Название товара</th>
                <th>Дата приема товара</th>
                <th>Количество</th>
                <th>Цена</th>
                <th>Сумма</th>
                <th>Удалить товар</th>
            </tr>
            <ProductRow
                v-for="(product, i) of products"  
                v-bind:index='i'  
                v-bind:product="product"
                v-on:remove-product='removeProduct'
            />
        </table>
    </div>
</template>

<script>
import ProductRow from '@/components/Table/ProductRow'
export default {
    props: ['products'],
    components: {
        ProductRow
    },
    methods: {
        removeProduct(id) {
            this.$emit('remove-product', id)
        }
    }
}
</script>

<style scoped>

table {
    width: 100%;
    padding: 0 20px;
    margin: 0 auto;
}

.table-header {
    display: flex;
    justify-content: space-between;
    border-bottom: 3px solid rgb(44, 62, 80);
    margin-bottom: 10px;
}

.table-header th {
    flex-basis: calc(100% / 7);
    text-align: left;
    margin-left: 10px;
}

.table-header th:first-child {
    margin-left: 0;
}
</style>