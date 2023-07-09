<!DOCTYPE html>
<html>
<head>
    <title>Speed Run Game</title>
    <style>
        #player {
            width: 20px;
            height: 20px;
            background-color: red;
            position: absolute;
            top: 0;
            left: 0;
        }
    </style>
</head>
<body>
    <h1>Speed Run Game</h1>
    <p>Use the arrow keys to move the player to the finish line as quickly as possible.</p>
    <div id="player"></div>

    <script>
        document.addEventListener("keydown", movePlayer);

        function movePlayer(event) {
            var player = document.getElementById("player");
            var playerPos = player.getBoundingClientRect();
            var speed = 5;

            switch (event.key) {
                case "ArrowUp":
                    player.style.top = (playerPos.top - speed) + "px";
                    break;
                case "ArrowDown":
                    player.style.top = (playerPos.top + speed) + "px";
                    break;
                case "ArrowLeft":
                    player.style.left = (playerPos.left - speed) + "px";
                    break;
                case "ArrowRight":
                    player.style.left = (playerPos.left + speed) + "px";
                    break;
            }

            checkFinishLine(playerPos);
        }

        function checkFinishLine(playerPos) {
            var finishLine = document.body.getBoundingClientRect();

            if (playerPos.right >= finishLine.right && playerPos.bottom >= finishLine.bottom) {
                alert("Congratulations! You completed the speed run!");
                resetGame();
            }
        }

        function resetGame() {
            var player = document.getElementById("player");
            player.style.top = "0";
            player.style.left = "0";
        }
    </script>
</body>
</html>

