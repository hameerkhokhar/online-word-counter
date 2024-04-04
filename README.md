<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Text Analysis Tool</title>
    <!-- Include Tailwind CSS -->
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <style>
        /* Optional: Additional custom styles */
        .text-analysis-container {
            max-width: 800px;
            margin: 50px auto;
        }
    </style>
</head>
<body class="bg-gray-100">
    <div class="text-analysis-container p-8 bg-white shadow-md rounded-md">
        <h1 class="text-2xl font-bold mb-4">Text Analysis Tool</h1>
        <textarea id="textInput" class="w-full h-32 border rounded-md p-2 mb-4" placeholder="Enter your text here..."></textarea>
        <button id="analyzeButton" class="bg-blue-500 text-white px-4 py-2 rounded-md">Analyze Text</button>
        <div id="analysisResults" class="mt-4"></div>
    </div>

    <!-- Include Tailwind CSS -->
    <script src="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.js"></script>
    <script>
        // JavaScript for text analysis
        document.getElementById('analyzeButton').addEventListener('click', function() {
            const text = document.getElementById('textInput').value;
            const wordCount = countWords(text);
            const charCount = countCharacters(text);
            const readingLevel = estimateReadingLevel(text);
            const readingTime = estimateReadingTime(text);
            const speakingTime = estimateSpeakingTime(text);

            displayAnalysisResults(wordCount, charCount, readingLevel, readingTime, speakingTime);
        });

        function countWords(text) {
            const words = text.match(/\b\w+\b/g);
            return words ? words.length : 0;
        }

        function countCharacters(text) {
            return text.length;
        }

        function estimateReadingLevel(text) {
            // Simple estimation of reading level based on word count
            const wordCount = countWords(text);
            if (wordCount < 100) {
                return "Beginner";
            } else if (wordCount < 500) {
                return "Intermediate";
            } else {
                return "Advanced";
            }
        }

        function estimateReadingTime(text) {
            // Average reading speed in words per minute
            const wordsPerMinute = 200;
            const wordCount = countWords(text);
            return Math.ceil(wordCount / wordsPerMinute);
        }

        function estimateSpeakingTime(text) {
            // Average speaking speed in words per minute
            const wordsPerMinute = 150;
            const wordCount = countWords(text);
            return Math.ceil(wordCount / wordsPerMinute);
        }

        function displayAnalysisResults(wordCount, charCount, readingLevel, readingTime, speakingTime) {
            const analysisResults = document.getElementById('analysisResults');
            analysisResults.innerHTML = `
                <p><strong>Word Count:</strong> ${wordCount}</p>
                <p><strong>Character Count:</strong> ${charCount}</p>
                <p><strong>Reading Level:</strong> ${readingLevel}</p>
                <p><strong>Reading Time:</strong> ${readingTime} minute(s)</p>
                <p><strong>Speaking Time:</strong> ${speakingTime} minute(s)</p>
            `;
        }
    </script>
</body>
</html>
