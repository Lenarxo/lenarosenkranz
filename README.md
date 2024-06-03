<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lenas Plants</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            overflow: hidden;
            font-family: basteleur, bold;
            background: url('Topf 2024-06-03 06_49_08.jpg') no-repeat center center fixed;
            background-size: cover;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            height: 100vh;
        }

        h1 {
            text-align: center;
            font-size: 3em;
            color: green;
            margin-top: 30px;
            position: relative;
            z-index: 1;
        }

        .leaf {
            position: absolute;
            width: 30px;
            height: 30px;
            background: pink;
            opacity: 0.8;
            border-radius: 50%;
            animation: fall linear infinite;
        }

        @keyframes fall {
            to {
                transform: translateY(100vh) rotate(360deg);
            }
        }

        #model-viewer-container {
            width: 60%;
            height: 400px;
            margin-top: 20px;
            position: relative;
            z-index: 1;
        }

        model-viewer {
            width: 100%;
            height: 100%;
        }
    </style>
</head>
<body>
    <h1>Lenas Plants</h1>

    <div id="model-viewer-container">
        <model-viewer src="Kaktus.glb" alt="A 3D model of a plant" auto-rotate camera-controls></model-viewer>
    </div>

    <script>
        // Function to create falling leaves
        function createLeaf() {
            const leaf = document.createElement('div');
            leaf.classList.add('leaf');
            leaf.style.left = Math.random() * 100 + 'vw';
            leaf.style.animationDuration = Math.random() * 3 + 2 + 's';
            leaf.style.animationDelay = Math.random() * 5 + 's';
            document.body.appendChild(leaf);

            setTimeout(() => {
                leaf.remove();
            }, 7000); // Remove leaf after animation
        }

        // Create multiple leaves
        for (let i = 0; i < 20; i++) {
            createLeaf();
        }

        // Continuously create new leaves
        setInterval(createLeaf, 1000);
    </script>

    <script type="module" src="https://unpkg.com/@google/model-viewer/dist/model-viewer.min.js"></script>
</body>
</html>
