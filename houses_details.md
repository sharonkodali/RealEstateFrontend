---
permalink: /houses/house_details
title: House Details
---

<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>House Info</title>
    <style>
        /* Your existing styles */
        body {
            font-family: Arial, sans-serif;
            background-color: #f8f8f8;
            margin: 0;
            padding: 0;
        }
        .house-info {
            background-color: #fff;
            margin: 20px auto; /* Center aligning the container */
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            text-align: center; /* Center-aligning text content */
        }
        h1 {
            color: #333;
            font-size: 24px;
            margin-bottom: 10px;
        }
        p {
            color: #666;
            margin-bottom: 5px;
        }
        img {
            width: 60%; /* Decreased image width to 60% of its parent container */
            height: auto;
            margin-bottom: 15px;
            border-radius: 8px;
        }
        a {
            color: #3498db;
            text-decoration: none;
        }
        a:hover {
            text-decoration: underline;
        }
        /* Additional Styles */
        .house-details {
            margin-top: 20px;
        }
        .house-details p {
            font-size: 16px;
            margin-bottom: 8px;
        }
        .house-details strong {
            color: #333;
        }
    </style>
</head>

<body>
    <div class="house-info" id="house-info">
        <!-- House information will be inserted here dynamically using JavaScript -->
    </div>
    <script>
        // Function to get the JWT token from cookies
        function getJwtToken() {
            return document.cookie.split(';').find(cookie => cookie.trim().startsWith('jwt='));
        }
        // Function to redirect to the login page if the JWT token does not exist
        function redirectToLogin() {
            window.location.href = "{{site.baseurl}}/login"; // Adjust the login page URL as needed
        }
        // Check for the existence of the JWT token when the page loads
        window.addEventListener('load', function() {
            const jwtToken = getJwtToken();
            // If the JWT token does not exist, redirect to the login page
            if (!jwtToken) {
                redirectToLogin();
            }
        });
    // Your existing JavaScript code for fetching and displaying house details
    document.addEventListener('DOMContentLoaded', () => {
        // Your existing JavaScript code for fetching and displaying house details
    });
        document.addEventListener('DOMContentLoaded', () => {
            const urlParams = new URLSearchParams(window.location.search);
            const houseId = urlParams.get('id');
            const houseInfoContainer = document.getElementById('house-info');
            async function fetchHouseInfo() {
                try {
                    const response = await fetch(`http://127.0.0.1:8181/api/house/housedetails?id=${houseId}`);
                    const house = await response.json();
                    houseInfoContainer.innerHTML = `
                        <img src="${house.imgSRC || 'https://www.avantistones.com/images/noImage.png'}" alt="${house.address}" />
                        <h1>${house.address}</h1>
                        <div class="house-details">
                            ${house.city ? `<p><strong>City:</strong> ${house.city}</p>` : ''}
                            ${house.state ? `<p><strong>State:</strong> ${house.state}</p>` : ''}
                            ${house.zip ? `<p><strong>Zip Code:</strong> ${house.zip}</p>` : ''}
                        </div>
                        <div class="house-details">
                            ${house.price ? `<p><strong>Price:</strong> $${house.price}</p>` : ''}
                            ${house.bedrooms ? `<p><strong>Bedrooms:</strong> ${house.bedrooms}</p>` : ''}
                            ${house.bathrooms ? `<p><strong>Bathrooms:</strong> ${house.bathrooms}</p>` : ''}
                            ${house.livingarea ? `<p><strong>Living Area:</strong> ${house.livingarea} sqft</p>` : ''}
                            ${house.homeType ? `<p><strong>Home Type:</strong> ${house.homeType}</p>` : ''}
                            ${house.priceEstimate ? `<p><strong>Price Estimate:</strong> $${house.priceEstimate}</p>` : ''}
                            ${house.rentEstimate ? `<p><strong>Rent Estimate:</strong> $${house.rentEstimate}</p>` : ''}
                            <button class="btn btn-primary btn-lg font-weight-bold" id="addToFavorites">Add to Favorites</button>
                        </div>
                    `;
                } catch (error) {
                    console.error('Error fetching data:', error);
                    houseInfoContainer.innerHTML = '<p>Error loading house information.</p>';
                }
            }
            fetchHouseInfo();
        });
    </script>
</body>

</html>
