<script>
    export let cart = [];
    export let removeFromCart;

    let total = 0;

    $: total = cart.reduce((sum, item) => sum + item.price, 0);

    function handleRemove(index) {
        removeFromCart(index);
    }
</script>

<div class="cart">
    <h2>Your Cart</h2>
    {#if cart.length === 0}
        <p>No items in cart</p>
    {:else}
        <ul>
            {#each cart as item, index}
                <li>
                    {item.name} - ${item.price}
                    <button on:click={() => handleRemove(index)}>Remove</button>
                </li>
            {/each}
        </ul>
        <p>Total: ${total.toFixed(2)}</p>
    {/if}
</div>

<style>
    .cart {
        margin-top: 40px;
        padding: 20px;
        border: 1px solid #ccc;
    }
    ul {
        list-style: none;
        padding: 0;
    }
    li {
        display: flex;
        justify-content: space-between;
        padding: 5px 0;
    }
    button {
        background-color: #dc3545;
        color: white;
        border: none;
        padding: 5px;
        cursor: pointer;
    }
    button:hover {
        background-color: #c82333;
    }
</style>
