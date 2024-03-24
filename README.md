<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Color Matching Game</title>
    <link href="https://cdn.jsdelivr.net/npm/@heroicons/react@latest/dist/cdn.js" rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css" integrity="sha512-IMpHvv7s6Cg/NXaOsbPFZYvCV56vxVoUU7mI6Y4twbcIFyEUQ+gv3SgEzh1j9z77ITgSJ3JJdO9rGrSQ00kXg==" crossorigin="anonymous" referrerpolicy="no-referrer" />
    <style>
        body {
            font-family: Georgia , Serif;
            background-image: url("bgg.jpg");           
        }

        .header {
            background-image: url("af.avif");
            background-size: cover;
            background-position: center;
            padding: 2rem 0;
            text-align: center;
        }

        .header h1 {
            font-size: 3rem;
            font-weight: bold;
            color: black;
        }
    </style>
</head>
<body>

    <header class="header">
        <div class="container mx-auto flex justify-between items-center"></div>
        <h1 class="text-3xl font-semibold text-black">Color Matching Game</h1>
        <h3 class="text-black">By Asmita(22BCM010)</h3>
    </header>
    <br/>
    <div class="flex justify-center ">
        <div id="box1" class="w-64 h-64 flex justify-center items-center bg-indigo-500 text-white cursor-pointer">
            <p>I'm ur colour</p>
        </div>
        <div id="box2" class="w-64 h-64 flex justify-center items-center bg-Cyan-500 text-white ml-4 cursor-pointer" onmouseover="changeColorRandom()" >
            <p>Hover over me</p>
        </div>
    </div>
    <br/>
    <button id="matchButton" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-4 mx-auto block">Match Colors</button>
    <audio id="clapSound">
        <source src="clap.wav" type="audio/mpeg">
    </audio>
    <script>
        const colors = [
            'Red',
            'Blue',
            'Green',
            'Yellow',
            'Black',
            'Cream',
            'Gray',
            'Purple',
            'Orange',
            'Brown',
            'Pink',
            'Cyan',
            'Maroon',
            'Indigo',
            'Turquoise',
            'Lavender',
            'Magenta',
            'Teal',
            'Beige',
            'Crimson'
        ];

        let intervalId;

        function getRandomColor() {
            return colors[Math.floor(Math.random() * colors.length)];
        }

        function changeColor() {
            const box1 = document.getElementById('box1');
            const randomColor = getRandomColor();
            box1.style.backgroundColor = randomColor;
        }

        function playClapSound() {
            const audio = document.getElementById('clapSound');
            audio.play();
        }

        function changeColorRandom() {
            const box2 = document.getElementById('box2');
            const randomColor = getRandomColor();
            box2.style.backgroundColor = randomColor;
        }

        function startChangingColor() {
            intervalId = setInterval(changeColorRandom, 500); 
        }

        function stopChangingColor() {
            clearInterval(intervalId); 
        }

        function checkColor() {
            const box1 = document.getElementById('box1');
            const box2 = document.getElementById('box2');
            const box1Color = box1.style.backgroundColor;
            const box2Color = box2.style.backgroundColor;
            if (box1Color === box2Color) {
                playClapSound();
                alert("Congratulations! You win!");
            } else {
                alert("Sorry, try again!");
            }
        }

        document.getElementById('matchButton').addEventListener('click', checkColor);

        window.onload = function() {
            changeColor(); 
        };
    </script>
</body>
</html>
