<template>
        <article class="product-small">
            <figure class="product-small__image img-wrap">
                <a :href="'https://www.coburns.com/store/productdetails.aspx?itemId=' + item.itemId"><img width="50" :src="getPhoto(item)" ></a>
            </figure>
            <div class="product-small__text">
                <h4 class="product-small__title">
                    <a :href="'https://www.coburns.com/store/productdetails.aspx?itemId=' + item.itemId">{{item.itemName}}</a>
                </h4>
                <div class="row">
                    <div class="col">
                        <div class="product-small__price">${{item.price}}</div>
                    </div>
                    <div class="col-auto">
                        <div class="product-small__quantity form-group">
                            <label class="sr-only" for="inputQuantity">Quantity</label>
                            <div class="input-group input-group-sm input-group--minimal">
                                <div class="input-group-prepend">
                                    <button class="btn btn-outline-gray-light" type="button" v-on:click.prevent="decrement">
                                        <span aria-hidden="true">-</span>
                                        <span class="sr-only">Decrease Quantity</span>
                                    </button>
                                </div>
                                <input type="text" class="form-control text-center" v-on:change.enter="change" v-model="item.quantity">
                                <div class="input-group-append">
                                    <button class="btn btn-outline-gray-light" type="button" v-on:click.prevent="increment">
                                        <span aria-hidden="true">+</span>
                                        <span class="sr-only">Increase Quantity</span>
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </article>
</template>
<script>
export default {
    name : "CartItem",
    props: ["item"],
    methods: {
        decrement(){
            this.$emit("decItem", this.item);
        },
        increment(){
            this.$emit("incItem", this.item);
        },
        change(){
            this.$emit("change", this.item);
        },
        getPhoto(item){
            var image = item.imageUrl ? item.imageUrl : "https://www.coburns.com/images/no-image.png";

            return image + '?w=50'
        }
    }
}
</script>
