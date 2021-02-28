BigCommerce Store URL: https://jmac.mybigcommerce.com/
Preview Code: silyn736w6

1) Create a feature that will show the product's second image when it is hovered on.
    - In 'cornerstone\templates\components\products\card.html', I added an onmouseenter function that replaces the card image's src with the product's second image, if it exists.  I also added an onmouseleave function that sets the card image's src back to the initial image.

2) Add a button at the top of the category page labeled Add All To Cart. When clicked, the product will be added to the cart. Notify the user that the product has been added.
    - In 'cornerstone\templates\components\category\product-listing.html', I added a button that says Add All To Cart.  I used the existing "button button--primary" class for styling.
    - Also in 'cornerstone\templates\components\category\product-listing.html', I added an onclick function that loops through each product in the handlebars products variable and, if a particular product does not have multiple options, it pushes one of that product to an array.  It then uses the storefront API to create a cart with that array of products or, if a cart exists, it adds those items to the existing cart.  It then updates the cart quantity and cart id in local storage and, if necessary, adds the 'countPill--positive' class to the cart badge and makes the Remove All items button visible.
    - In 'cornerstone\assets\js\theme\category.js', this triggers a sweet-alert pop-up to let the user know the items were added to the cart.

3) If the cart has an item in it - show a button next to the Add All To Cart button which says Remove All Items. When clicked it should clear the cart and notify the user.
    - In 'cornerstone\templates\components\category\product-listing.html', I added a button that says Remove All Items.  I used the existing "button button--secondary" class for styling.
    - Also in 'cornerstone\templates\components\category\product-listing.html', I added an onclick function that uses the storefront API to delete the cart based on cartId.  It then updates the cart quantity and cart id in local storage, removes the 'countPill--positive' class from the cart badge, and removes visibility from the Remove All items button.
    - In 'cornerstone\assets\js\theme\category.js', this triggers a sweet-alert pop-up to let the user know the items were removed from the cart.

4) If a customer is logged in - at the top of the category page show a banner that shows some customer details (i.e. name, email, phone, etc). This should utilize the data that is rendered via Handlebars on the Customer Object.
    - In 'cornerstone\templates\components\common\navigation.html', I created a div that only shows up if the customer data is available in Handlebars and if the page template is 'pages/category'.  It will not show otherwise.  I copied the styling from the adminAlert bar and made a few tweaks to account for both bars being open at the same time.  If both the adminBar and the customer banner are showing, the navigation area gets additional padding-top to account for the extra item.