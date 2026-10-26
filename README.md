<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>QuickWear | Fashion Delivered</title>

    <style>
        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: #f8f8f8;
            color: #222;
        }

        header {
            background: #111;
            color: white;
            padding: 20px 7%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
        }

        header h1 {
            color: #ff416c;
            margin: 0;
        }

        nav a {
            color: white;
            text-decoration: none;
            margin: 8px;
        }

        .hero {
            background: #ffe4eb;
            padding: 65px 20px;
            text-align: center;
        }

        .hero h2 {
            font-size: 38px;
        }

        button {
            background: #ff416c;
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 6px;
            cursor: pointer;
        }

        .section {
            padding: 30px 7%;
        }

        .products {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(190px, 1fr));
            gap: 20px;
        }

        .product {
            background: white;
            padding: 20px;
            text-align: center;
            border-radius: 12px;
        }

        .product-image {
            font-size: 75px;
            background: #f0f0f0;
            padding: 20px;
            border-radius: 8px;
        }

        .price {
            font-size: 20px;
            font-weight: bold;
        }

        footer {
            background: #111;
            color: white;
            padding: 20px;
            text-align: center;
        }
    </style>
</head>

<body>

<header>
    <h1>QuickWear</h1>
    <nav>
        <a href="#home">Home</a>
        <a href="#products">Shop</a>
        <a href="#cart">Cart (<span id="count">0</span>)</a>
    </nav>
</header>

<section class="hero" id="home">
    <h2>Fashion at Your Doorstep</h2>
    <p>Your favourite styles, delivered to you.</p>
    <button onclick="document.getElementById('products').scrollIntoView({behavior:'smooth'})">
        Shop Now
    </button>
</section>

<section class="section" id="products">
    <h2>Trending Fashion</h2>

    <div class="products">

        <div class="product">
            <div class="product-image">👕</div>
            <h3>Classic T-Shirt</h3>
            <p>Everyday collection</p>
            <p class="price">₹499</p>
            <button onclick="addToCart('Classic T-Shirt',499)">Add to Cart</button>
        </div>

        <div class="product">
            <div class="product-image">👖</div>
            <h3>Denim Jeans</h3>
            <p>Casual collection</p>
            <p class="price">₹999</p>
            <button onclick="addToCart('Denim Jeans',999)">Add to Cart</button>
        </div>

        <div class="product">
            <div class="product-image">👗</div>
            <h3>Stylish Dress</h3>
            <p>Party collection</p>
            <p class="price">₹799</p>
            <button onclick="addToCart('Stylish Dress',799)">Add to Cart</button>
        </div>

        <div class="product">
            <div class="product-image">🧥</div>
            <h3>Casual Jacket</h3>
            <p>Streetwear collection</p>
            <p class="price">₹1499</p>
            <button onclick="addToCart('Casual Jacket',1499)">Add to Cart</button>
        </div>

    </div>
</section>

<section class="section" id="cart">
    <h2>Your Shopping Cart</h2>
    <div id="cart-items">Your cart is empty.</div>
    <h3>Total: ₹<span id="total">0</span></h3>
    <button onclick="clearCart()">Clear Cart</button>
</section>

<footer>
    <p>QuickWear — Fashion delivered faster.</p>
    <p>Student project prototype</p>
</footer>

<script>
    let cart = [];
    let total = 0;

    function addToCart(name, price) {
        cart.push({name, price});
        total += price;
        updateCart();
    }

    function updateCart() {
        document.getElementById('count').textContent = cart.length;
        document.getElementById('total').textContent = total;

        const items = document.getElementById('cart-items');

        if (cart.length === 0) {
            items.textContent = 'Your cart is empty.';
            return;
        }

        items.innerHTML = '';

        cart.forEach((item, index) => {
            const row = document.createElement('p');
            row.textContent = `${index + 1}. ${item.name} - ₹${item.price}`;
            items.appendChild(row);
        });
    }

    function clearCart() {
        cart = [];
        total = 0;
        updateCart();
    }
</script>

</body>
</html>
