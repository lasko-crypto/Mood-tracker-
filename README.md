<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mood Tracker</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; background: #f4f4f4; padding: 20px; }
        #moodContainer { background: white; padding: 20px; border-radius: 10px; box-shadow: 2px 2px 10px rgba(0,0,0,0.2); display: inline-block; }
        button { padding: 10px 15px; font-size: 16px; margin: 5px; cursor: pointer; border-radius: 5px; border: none; }
        .happy { background: #ffcc00; }
        .neutral { background: #999; color: white; }
        .sad { background: #3498db; color: white; }
        #log { margin-top: 20px; }
        .entry { background: white; padding: 10px; margin: 5px; border-radius: 5px; box-shadow: 1px 1px 5px rgba(0,0,0,0.2); }
    </style>
</head>
<body>

    <h1>How Are You Feeling Today?</h1>
    <div id="moodContainer">
        <button class="happy" onclick="logMood('Happy')">😊 Happy</button>
        <button class="neutral" onclick="logMood('Neutral')">😐 Neutral</button>
        <button class="sad" onclick="logMood('Sad')">😢 Sad</button>
    </div>

    <h2>Your Mood Log</h2>
    <div id="log"></div>

    <script>
        function logMood(mood) {
            const messages = {
                "Happy": "Keep smiling! 😊",
                "Neutral": "Stay balanced and take it easy. 😌",
                "Sad": "It's okay to have bad days. You're strong! 💪"
            };

            let log = document.getElementById('log');
            let entry = document.createElement('div');
            entry.className = "entry";
            entry.innerHTML = `<strong>${mood}</strong> - ${messages[mood]} (${new Date().toLocaleString()})`;
            log.prepend(entry);

            localStorage.setItem('moodLog', log.innerHTML);
        }

        window.onload = function() {
            if (localStorage.getItem('moodLog')) {
                document.getElementById('log').innerHTML = localStorage.getItem('moodLog');
            }
        };
    </script>

</body>
</html>

