<template>
    <form @submit.prevent="onSubmit" class="form">
        <div class="inputs">
            <input class="input-title" type="text" placeholder="Название товара" v-model='title'>
            <input class="input-date" type="date" placeholder="Дата приема" v-model='date'>
            <input class="input-count" type="number" placeholder="Количество" v-model='count'>
            <input class="input-price" type="number" placeholder="Цена" v-model='price'>
        </div>
        <button type="submit">Добавить товар</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            title: '',
            date: '',
            count: '',
            price: ''
        }
    },
    methods: {
        onSubmit() {

            let form = document.querySelector('.form')
            let isValid = true;

			for (let i = 0; i < form.length; i++) {
                if (form.elements[i].type != 'submit') {
                    if (form.elements[i].value == '') {
					    form.elements[i].style.borderColor = 'rgb(255, 94, 94)';
					    isValid = false;
			    	}
				    else {
					    form.elements[i].style.borderColor = 'black';
				    }
                }
			}

            if (isValid) {
                const newProduct = {
                    id: Date.now(),
                    title: this.title,
                    date: this.date,
                    count: this.count,
                    price: this.price,
                    summ: this.price * this.count
                }

                this.$emit('add-product', newProduct)
                this.title = ''
                this.date = ''
                this.count = ''
                this.price = ''
            }
            else {
                alert('Форма заполнена не полностью!')
            }
        }
    }
}
</script>

<style scoped>
    
    .form {
        width: 60%;
        margin: 0 auto 30px;
        padding: 30px 20px;
        border: 2px solid #ddd;
        border-radius: 15px;
    }

    input, button {
        outline: none;
        font-family: inherit;
        font-size: inherit;
        border-radius: 5px;
        border: 1px solid #ccc;
    }

    .inputs {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
    }

    input {
        padding: 10px;
    }

    .input-title {
        width: 100%;
        margin-bottom: 15px;
    }

    .input-date, .input-count, .input-price {
        width: 25%;
    }

    button {
        margin-top: 20px;
        padding: 10px 20px;
        cursor: pointer;
        background: rgb(3, 74, 141);
        color: #fff;
        transition: background .1s linear;
    }

    button:hover {
        background: rgb(33, 129, 219);
    }

</style>