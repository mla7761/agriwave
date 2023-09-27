<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rice Crop Analyzer</title>
    <style>
        /* Add your CSS styling here */
    </style>
</head>
<body>
    <h1>Paddy Crop Analyzer</h1>
    
    <div id="input-form">
        <label for="nitrogen">N (Nitrogen) content (kg/hec):</label>
        <input type="number" id="nitrogen" min="0"><br>

        <label for="phosphorus">P (Phosphorus) content (kg/hec):</label>
        <input type="number" id="phosphorus" min="0"><br>

        <label for="potassium">K (Potassium) content (kg/hec):</label>
        <input type="number" id="potassium" min="0"><br>

        <label for="moisture">Soil Moisture (%):</label>
        <input type="number" id="moisture" min="270" max="430"><br>

        <button onclick="analyzeCrop()">Analyze</button>
    </div>

    <div id="results">
        <h2>Analysis Results:</h2>
        <p id="analysis-output"></p>
    </div>

    <script>
        function analyzeCrop() {
            // Replace these values with actual recommendations
            const recommendedValues = {
                nitrogen: 123,
                phosphorus: 29.65,
                potassium: 29.65,
            };

            const nitrogen = parseFloat(document.getElementById('nitrogen').value);
            const phosphorus = parseFloat(document.getElementById('phosphorus').value);
            const potassium = parseFloat(document.getElementById('potassium').value);
            const moisture = parseFloat(document.getElementById('moisture').value);
            
            let analysisResult = "Crop Analysis Results:\n\n";

            if (isNaN(nitrogen) || isNaN(phosphorus) || isNaN(potassium) || isNaN(moisture)) {
                analysisResult += "Please enter valid numeric values for all inputs.";
            } else {
                analysisResult += `N (Nitrogen): ${nitrogen} kg/hec\n`;
                analysisResult += `P (Phosphorus): ${phosphorus} kg/hec\n`;
                analysisResult += `K (Potassium): ${potassium} kg/hec\n`;
                analysisResult += `Soil Moisture: ${moisture}%\n\n`;
                
                // Compare values to recommended values
                if (nitrogen < recommendedValues.nitrogen) {
                    analysisResult += `Warning: Low nitrogen levels detected. Recommended fertilizer: Nitrogen-based fertilizer with ${recommendedValues.nitrogen - nitrogen} kg/hec\n`;
                }
                if (phosphorus < recommendedValues.phosphorus) {
                    analysisResult += `Warning: Low phosphorus levels detected. Recommended fertilizer: Phosphorus-based fertilizer with ${recommendedValues.phosphorus - phosphorus} kg/hec\n`;
                }
                if (potassium < recommendedValues.potassium) {
                    analysisResult += `Warning: Low potassium levels detected. Recommended fertilizer: Potassium-based fertilizer with ${recommendedValues.potassium - potassium} kg/hec\n`;
                }
                if (moisture < 270) {
                    analysisResult += "Watering Recommendation: Increase irrigation.\n";
                } else if (moisture > 430) {
                    analysisResult += "Watering Recommendation: Reduce irrigation.\n";
                } else {
                    analysisResult += "Watering Recommendation: Maintain current irrigation levels.\n";
                }
            }

            document.getElementById('analysis-output').textContent = analysisResult;
        }
    </script>
</body>
</html>
![image](https://github.com/mla7761/agriwave/assets/146155253/02d39cde-8a96-4f18-bb44-b719b69693ec)
