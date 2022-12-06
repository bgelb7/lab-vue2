<script>
import ITEMS from "../assets/items.json";
export default {
    data() {
        return {
            items: ITEMS,

        };
    },
    computed: {
        TotalPrice() {
            let TotalPrice = this.items.reduce(function (accumulator, item) {
                let TotalPrice = accumulator + item.price * item.quantity;
                return TotalPrice;

            }, 0);

            return TotalPrice;

        },
        numberOfItems() {
            let TotalQuantity = this.items.reduce(function (accumulator, item) {
                let TotalQuantity = accumulator + item.quantity;
                return TotalQuantity;
            }, 0);
            return TotalQuantity;
        },
        limitReached() {
            return this.items.length < 3;
        },


    },

    methods: {

        increment(index) {

            this.items[index].quantity++
        },

        decrement(index) {

            this.items[index].quantity--
        }
    },



}





</script>
<template>


    <div class="font-semibold text-gray-500 text-lg">

        <div class="container mx-auto mt-10">
            <div class="flex shadow-md my-10">
                <div class="w-3/4 bg-white px-10 py-10">
                    <div class="flex justify-between border-b pb-8">
                        <h1 class="font-semibold text-2xl">Shopping Cart</h1>
                        <h2 class="font-semibold text-2xl"> {{ numberOfItems }} items</h2>
                    </div>
                    <div class="flex mt-10 mb-5">
                        <h3 class="font-semibold text-gray-600 text-xs uppercase w-2/5">Product Details</h3>
                        <h3 class="font-semibold text-center text-gray-600 text-xs uppercase w-1/5 text-center">Quantity
                        </h3>
                        <h3 class="font-semibold text-center text-gray-600 text-xs uppercase w-1/5 text-center">Price
                        </h3>
                        <h3 class="font-semibold text-center text-gray-600 text-xs uppercase w-1/5 text-center">Total
                        </h3>
                    </div>
                    <div v-for="item, index of items" :key="items.uuid"
                        class="flex items-center hover:bg-gray-100 -mx-8 px-6 py-5">
                        <div class="flex w-2/5"> <!-- product -->
                            <div class="w-20">
                                <img class="h-24" :src="item.image" alt="">
                            </div>
                            <div class="flex flex-col justify-between ml-4 flex-grow">
                                <span class="font-bold text-sm">{{ item.name }}</span>
                                <span class="text-red-500 text-xs">{{ index }}</span>
                                <a href="#" class="font-semibold hover:text-red-500 text-gray-500 text-xs">Remove</a>
                            </div>
                        </div>
                        <div class="flex justify-center w-1/5">
                            <button class="fill-current text-gray-600 w-3" viewBox="0 0 448 512"
                                @click="decrement(index)">-</button>

                            <input class="mx-2 border text-center w-8" type="text" v-model="item.quantity">

                            <button class="fill-current text-gray-600 w-3" viewBox="0 0 448 512"
                                @click="increment(index)">
                                +</button>
                        </div>
                        <span class="text-center w-1/5 font-semibold text-sm">${{ item.price }}</span>
                        <span class="text-center w-1/5 font-semibold text-sm"> ${{ item.quantity * item.price }}
                        </span>
                    </div>




                    <a href="#" class="flex font-semibold text-indigo-600 text-sm mt-10">

                        <button class="fill-current mr-2 text-indigo-600 w-4" viewBox="0 0 448 512" @click="decrement">
                            <path
                                d="M134.059 296H436c6.627 0 12-5.373 12-12v-56c0-6.627-5.373-12-12-12H134.059v-46.059c0-21.382-25.851-32.09-40.971-16.971L7.029 239.029c-9.373 9.373-9.373 24.569 0 33.941l86.059 86.059c15.119 15.119 40.971 4.411 40.971-16.971V296z" />
                            -
                        </button>
                        Continue Shopping
                    </a>
                </div>

                <div id="summary" class="w-1/4 px-8 py-10">
                    <h1 class="font-semibold text-2xl border-b pb-8">Order Summary</h1>
                    <div class="flex justify-between mt-10 mb-5">
                        <span class="font-semibold text-sm uppercase">{{ numberOfItems }} items</span>
                        <span class="font-semibold text-sm">${{ TotalPrice }}</span>
                    </div>


                    <div class="border-t mt-8">
                        <div class="flex font-semibold justify-between py-6 text-sm uppercase">
                            <span>Total cost <br>(plus shipping)</span>
                            <span>Total $ {{ TotalPrice + 10 }}</span>
                        </div>

                        <button class="flex font-semibold justify-between py-6 text-sm uppercase"
                            v-if="limitReached">Añade
                            mínimo 3 artículos</button>

                        <button v-else
                            class="bg-indigo-500 font-semibold hover:bg-indigo-600 py-3 text-sm text-white uppercase w-full">{{
                                    numberOfItems
                            }}
                            items</button>
                        <p v-if="(numberOfItems >= 3)">Ahora tienes shipping gratis! </p>
                        <p v-else-if="(numberOfItems >= 2)"> Solo uno mas para obtener shipping gratis!</p>
                        <p v-else-if="(numberOfItems >= 1)"> Dos mas para obtener shipping gratis!</p>

                    </div>
                </div>

            </div>
        </div>

    </div>

</template>




