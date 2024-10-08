<script>
    import { onMount } from "svelte";
    import Product from "./Product.svelte";
    import Cart from "./Cart.svelte";

    let products = [];
    let cart = [];

    // Mock API data (you can later replace this with a real API call)
    onMount(() => {
        products = [
            { id: 1, name: "Laptop", price: 999.99 },
            { id: 2, name: "Phone", price: 499.99 },
            { id: 3, name: "Headphones", price: 199.99 },
        ];
    });

    function addToCart(product) {
        cart = [...cart, product];
    }

    function removeFromCart(index) {
        cart = cart.filter((_, i) => i !== index);
    }
</script>

<main>
    <h1>Simple E-Commerce Platform</h1>
    
    <div class="products">
        {#each products as product}
            <Product {product} on:addToCart={addToCart} />
        {/each}
    </div>
    
    <Cart {cart} on:removeFromCart={removeFromCart} />
</main>

<style>
    .products {
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
    }
</style>
