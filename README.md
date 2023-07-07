<!DOCTYPE html>
<html>
<head>
    <title>Fill and Fly Balloon Game</title>
    <style>
        .balloon {
            width: 100px;
            height: 150px;
            background-color: red;
            border-radius: 50%;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            transition: transform 0.5s ease;
        }
    </style>
</head>
<body>
    <div class="balloon"></div>

    <script>
        var balloons = document.getElementsByClassName("balloon");
        var currentIndex = 0;

        fillBalloons();

        function fillBalloons() {
            if (currentIndex >= balloons.length) {
                flyAway(balloons[currentIndex - 1]);
                return;
            }

            var currentBalloon = balloons[currentIndex];
            var fillInterval = setInterval(function() {
                inflateBalloon(currentBalloon);

                if (currentBalloon.offsetWidth >= 200 && currentBalloon.offsetHeight >= 300) {
                    clearInterval(fillInterval);
                    currentIndex++;
                    fillBalloons();
                }
            }, 50);
        }

        function inflateBalloon(balloon) {
            balloon.style.transform = "scale(1.1)";
        }

        function flyAway(balloon) {
            balloon.style.animation = "flyaway 2s forwards";

            setTimeout(function() {
                balloon.remove();
            }, 2000);
        }
    </script>
</body>
</html>
