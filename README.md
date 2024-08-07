<!DOCTYPE html>
<html>
<head>
    <title>Rock Paper Scissors Lizard Spock</title>
</head>
<body>
    <h1>Rock Paper Scissors Lizard Spock</h1>
    <button onclick="playGame()">Play</button>
    <p id="result"></p>
    
    <script>
        function nameToNumber(name) {
            switch (name.toLowerCase()) {
                case "rock":
                    return 0;
                case "spock":
                    return 1;
                case "paper":
                    return 2;
                case "lizard":
                    return 3;
                case "scissors":
                    return 4;
                default:
                    return -1;
            }
        }

        function numberToName(number) {
            switch (number) {
                case 0:
                    return "rock";
                case 1:
                    return "Spock";
                case 2:
                    return "paper";
                case 3:
                    return "lizard";
                case 4:
                    return "scissors";
                default:
                    return "Invalid number";
            }
        }

        function playGame() {
            let playerChoice = prompt("Enter your choice (rock, Spock, paper, lizard, scissors):");
            let resultText = "";

            if (playerChoice === null) {
                resultText = "Game cancelled.";
                document.getElementById("result").innerText = resultText;
                return;
            }

            playerChoice = playerChoice.trim().toLowerCase();
            let playerNumber = nameToNumber(playerChoice);

            if (playerNumber === -1) {
                resultText = "Invalid player choice.";
                document.getElementById("result").innerText = resultText;
                return;
            }

            let compNumber = Math.floor(Math.random() * 5);
            let compChoice = numberToName(compNumber);

            resultText += "Player chooses " + playerChoice + "\n";
            resultText += "Computer chooses " + compChoice + "\n";

            let difference = (compNumber - playerNumber + 5) % 5;

            if (difference === 0) {
                resultText += "It's a tie!";
            } else if (difference === 1 || difference === 2) {
                resultText += "Computer wins!";
            } else {
                resultText += "Player wins!";
            }

            document.getElementById("result").innerText = resultText;
        }
    </script>
</body>
</html>
