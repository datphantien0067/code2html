<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Photo Gallery</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: Arial, sans-serif;
            background-color: #f0f4f8;
            padding: 20px;
        }

        h1 {
            color: #2c3e50;
            text-align: center;
            margin-bottom: 10px;
        }

        h2 {
            color: #34495e;
            text-align: center;
            font-weight: normal;
            font-size: 1.2em;
            margin-bottom: 30px;
        }

        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .gallery-item {
            background: white;
            border-radius: 12px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            text-align: center;
            padding: 15px;
        }

        .gallery-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
        }

        .gallery-item:focus {
            outline: 3px solid #3498db;
            outline-offset: 3px;
        }

        .gallery-item img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 8px;
            display: block;
        }

        .gallery-item p {
            margin-top: 12px;
            color: #2c3e50;
            font-weight: bold;
            font-size: 0.95em;
        }

        .status-box {
            max-width: 600px;
            margin: 20px auto;
            padding: 15px;
            background: white;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            text-align: center;
            color: #2c3e50;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h1>Interactive Photo Gallery</h1>
    <h2>Hover or focus on images to see information</h2>

    <div class="gallery" id="galleryContainer">
        <!-- Gallery items will be inserted here by JavaScript -->
    </div>

    <div class="status-box" id="statusDisplay">
        Hover or focus on an image
    </div>

    <script>
        // Image data with six images
        const images = [
            {
                src: 'https://images.unsplash.com/photo-1506744038136-46273834b3fb?w=500&h=300&fit=crop',
                alt: 'Beautiful mountain landscape with snow-capped peaks and a clear blue lake',
                caption: 'Mountain Lake - A serene alpine scene'
            },
            {
                src: 'https://images.unsplash.com/photo-1470071459604-7b5ec3c74fe9?w=500&h=300&fit=crop',
                alt: 'Lush green forest with sunlight filtering through the canopy',
                caption: 'Enchanted Forest - Nature\'s cathedral'
            },
            {
                src: 'https://images.unsplash.com/photo-1441974231531-c6227db76b6e?w=500&h=300&fit=crop',
                alt: 'Misty pine forest with tall trees and foggy atmosphere',
                caption: 'Misty Pines - Morning fog in the woods'
            },
            {
                src: 'https://images.unsplash.com/photo-1519681393784-d120267933ba?w=500&h=300&fit=crop',
                alt: 'Starry night sky over a mountain range with Milky Way visible',
                caption: 'Starry Night - Milky Way over mountains'
            },
            {
                src: 'https://images.unsplash.com/photo-1501785888041-af3ef285b470?w=500&h=300&fit=crop',
                alt: 'Sunset over a calm lake with vibrant orange and pink colors',
                caption: 'Lake Sunset - Golden hour reflections'
            },
            {
                src: 'https://images.unsplash.com/photo-1504384308090-c894fdcc538d?w=500&h=300&fit=crop',
                alt: 'Autumn forest path with colorful red and orange leaves',
                caption: 'Autumn Path - Fall colors in the forest'
            }
        ];

        // Get the gallery container
        const galleryContainer = document.getElementById('galleryContainer');
        const statusDisplay = document.getElementById('statusDisplay');

        // Function to create gallery items
        function createGallery() {
            images.forEach((image, index) => {
                const item = document.createElement('div');
                item.className = 'gallery-item';
                item.setAttribute('tabindex', '0'); // Make focusable

                const img = document.createElement('img');
                img.src = image.src;
                img.alt = image.alt;
                img.setAttribute('loading', 'lazy');

                const caption = document.createElement('p');
                caption.textContent = image.caption;

                item.appendChild(img);
                item.appendChild(caption);
                galleryContainer.appendChild(item);

                // Add mouse events
                item.addEventListener('mouseover', function() {
                    statusDisplay.textContent = `Mouse is over: ${image.caption}`;
                    statusDisplay.style.backgroundColor = '#e8f4fd';
                });

                item.addEventListener('mouseleave', function() {
                    statusDisplay.textContent = 'Mouse left the image';
                    statusDisplay.style.backgroundColor = 'white';
                });

                // Add focus events
                item.addEventListener('focus', function() {
                    statusDisplay.textContent = `Keyboard focus on: ${image.caption}`;
                    statusDisplay.style.backgroundColor = '#d4edda';
                });

                item.addEventListener('blur', function() {
                    statusDisplay.textContent = 'Keyboard focus left the image';
                    statusDisplay.style.backgroundColor = 'white';
                });
            });
        }

        // Function to add tabfocus attribute and log
        function addTabFocus() {
            console.log('Tabfocus attribute added to gallery items');
            const items = document.querySelectorAll('.gallery-item');
            items.forEach(item => {
                item.setAttribute('tabfocus', 'true');
            });
        }

        // onload event handler
        function onPageLoad() {
            console.log('Page fully loaded');
            createGallery();
            addTabFocus();

            // Log all gallery items for verification
            const items = document.querySelectorAll('.gallery-item');
            console.log(`Number of gallery items: ${items.length}`);
            items.forEach((item, index) => {
                console.log(`Item ${index + 1} tabindex: ${item.getAttribute('tabindex')}`);
                console.log(`Item ${index + 1} tabfocus: ${item.getAttribute('tabfocus')}`);
            });

            statusDisplay.textContent = 'Gallery loaded! Hover or focus on images.';
        }

        // Add onload event listener
        window.addEventListener('load', onPageLoad);

        // Alternative way using window.onload (commented out as we used addEventListener above)
        // window.onload = onPageLoad;

        console.log('JavaScript loaded and ready');
    </script>
</body>
</html>
