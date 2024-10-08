<script>
    export let product;
    export let addToCart;

    function handleAdd() {
        addToCart(product);
    }
</script>

<div class="product">
    <h2>{product.name}</h2>
    <p>${product.price}</p>
    <button on:click={handleAdd}>Add to Cart</button>
</div>

<style>
    .product {
        border: 1px solid #ccc;
        padding: 20px;
        width: 200px;
        text-align: center;
    }
    button {
        margin-top: 10px;
        background-color: #28a745;
        color: white;
        border: none;
        padding: 10px;
        cursor: pointer;
    }
    button:hover {
        background-color: #218838;
    }
</style>
