<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Product Sale Page</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f7f7f7;
      padding: 40px;
    }
    .container {
      max-width: 400px;
      margin: auto;
      background: #fff;
      padding: 30px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
      border-radius: 10px;
    }
    .product-img {
      width: 100%;
      max-height: 250px;
      object-fit: contain;
      margin-bottom: 20px;
      border: 1px solid #eee;
      border-radius: 8px;
    }
    .product-details {
      margin-bottom: 20px;
    }
    select, button {
      width: 100%;
      padding: 10px;
      margin-top: 12px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    button {
      background: #007bff;
      color: #fff;
      font-weight: bold;
      cursor: pointer;
      border: none;
      transition: background 0.2s;
    }
    button:hover {
      background: #0056b3;
    }
    .success-message {
      color: green;
      margin-top: 15px;
      text-align: center;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Buy a Product</h2>
    <div class="product-details">
      <img id="productImage" class="product-img" src="" alt="Product Image">
      <div>
        <label for="productDropdown"><b>Select Product:</b></label>
        <select id="productDropdown"></select>
      </div>
      <p id="productDescription"></p>
      <p><b>Price: $<span id="productPrice"></span></b></p>
    </div>
    <button onclick="buyProduct()">Buy Now</button>
    <div id="message" class="success-message"></div>
  </div>
  <script>
    const products = [
      {
        name: "Red Sneakers",
        price: 49.99,
        image: "https://images.unsplash.com/photo-1517260911205-8fc6e4e7e3f9?auto=format&fit=crop&w=400&q=80",
        description: "Comfortable and stylish red sneakers for everyday use."
      },
      {
        name: "Blue Hoodie",
        price: 29.99,
        image: "https://images.unsplash.com/photo-1512436991641-6745cdb1723f?auto=format&fit=crop&w=400&q=80",
        description: "Warm blue hoodie made from organic cotton."
      },
      {
        name: "Black Backpack",
        price: 39.99,
        image: "https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=400&q=80",
        description: "Spacious black backpack for work or travel."
      }
    ];

    const dropdown = document.getElementById('productDropdown');
    const productImage = document.getElementById('productImage');
    const productDescription = document.getElementById('productDescription');
    const productPrice = document.getElementById('productPrice');
    const message = document.getElementById('message');

    // Populate dropdown
    products.forEach((product, idx) => {
      const option = document.createElement('option');
      option.value = idx;
      option.textContent = product.name;
      dropdown.appendChild(option);
    });

    function updateProductDetails(idx) {
      const product = products[idx];
      productImage.src = product.image;
      productDescription.textContent = product.description;
      productPrice.textContent = product.price.toFixed(2);
      message.textContent = '';
    }

    dropdown.addEventListener('change', (e) => {
      updateProductDetails(e.target.value);
    });

    function buyProduct() {
      const idx = dropdown.value;
      const product = products[idx];
      message.textContent = `Thank you for purchasing ${product.name}!`;
    }

    // Initialize with first product
    updateProductDetails(0);
  </script>
</body>
</html>
