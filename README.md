# E-commerece
Fix Navbar Background Issue

The color was set incorrectly (b is invalid).
 Fixed by setting background-color: #333; (dark color).

Make Banner Image Responsive

It wasn’t centered or adjusting to screen sizes.
 Fixed by adding:

css
Copy
Edit
.banner { text-align: center; }
.banner img { max-width: 100%; height: auto; }
Improve Product Grid Layout

Products may not align well on small screens.
 Fixed by using:

css
Copy
Edit
.product-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
}
Fix Cart Logic (Track Quantity)

Clicking "Add to Cart" created duplicate products instead of increasing quantity.
Fixed by updating JavaScript:

javascript
Copy
Edit
let cart = [];

document.querySelectorAll('.add-to-cart').forEach(button => {
    button.addEventListener('click', function() {
        const name = this.dataset.name;
        const price = parseFloat(this.dataset.price);

        let existingProduct = cart.find(item => item.name === name);
        if (existingProduct) {
            existingProduct.quantity++;
        } else {
            cart.push({ name, price, quantity: 1 });
        }
        updateCartCount();
    });
});

function updateCartCount() {
    let totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
    document.getElementById('cart-count').textContent = totalItems;
}
Improve Footer Layout (Social Icons)

Icons were not evenly spaced.
 Fixed by using:

css
Copy
Edit
.social-links {
    display: flex;
    justify-content: center;
    gap: 15px;
    padding: 10px 0;
}
