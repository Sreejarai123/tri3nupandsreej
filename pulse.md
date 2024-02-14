---
layout: default
title: Index
---
# Heart Rate Analysis

Enter your age and heart rate below:

Age: <input type="number" id="ageInput" min="1" max="120">
Heart Rate: <input type="number" id="heartRateInput" min="1" max="300">

<button onclick="analyzeHeartRate()">Analyze</button>

<p id="analysisResult"></p>

<div style="width: 800px; height: 400px;">
    <canvas id="heartRateChart"></canvas>
</div>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
    function analyzeHeartRate() {
        var age = document.getElementById('ageInput').value;
        var heartRate = document.getElementById('heartRateInput').value;

        var maxHeartRate = 220 - age;

        var healthyRangeMin = 0.5 * maxHeartRate;
        var healthyRangeMax = 0.85 * maxHeartRate;

        var analysisResult = document.getElementById('analysisResult');

        if (heartRate < healthyRangeMin) {
            analysisResult.innerText = 'Your heart rate is below the healthy range.';
        } else if (heartRate >= healthyRangeMin && heartRate <= healthyRangeMax) {
            analysisResult.innerText = 'Your heart rate is within the healthy range.';
        } else {
            analysisResult.innerText = 'Your heart rate is above the healthy range.';
        }

        var ctx = document.getElementById('heartRateChart').getContext('2d');
        var myChart = new Chart(ctx, {
            type: 'line',
            data: {
                labels: ['0-10', '11-20', '21-30', '31-40', '41-50', '51-60', '61-70', '71-80', '81-90', '91-100', '101-110'],
                datasets: [{
                    label: '0-10 Years',
                    data: [80, 85, 90, 95, 100, 105, 110, 115, 120, 125, 130],
                    borderColor: 'rgba(255, 182, 193, 1)',
                    backgroundColor: 'rgba(255, 182, 193, 0.2)',
                    borderWidth: 1
                }, {
                    label: '11-20 Years',
                    data: [85, 90, 95, 100, 105, 110, 115, 120, 125, 130, 135],
                    borderColor: 'rgba(255, 182, 193, 1)',
                    backgroundColor: 'rgba(255, 182, 193, 0.2)',
                    borderWidth: 1
                }, {
                    label: '21-30 Years',
                    data: [90, 95, 100, 105, 110, 115, 120, 125, 130, 135, 140],
                    borderColor: 'rgba(255, 182, 193, 1)',
                    backgroundColor: 'rgba(255, 182, 193, 0.2)',
                    borderWidth: 1
                }, {
                    label: '31-40 Years',
                    data: [95, 100, 105, 110, 115, 120, 125, 130, 135, 140, 145],
                    borderColor: 'rgba(255, 182, 193, 1)',
                    backgroundColor: 'rgba(255, 182, 193, 0.2)',
                    borderWidth: 1
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    yAxes: [{
                        scaleLabel: {
                            display: true,
                            labelString: 'Average Heart Rate (bpm)'
                        }
                    }],
                    xAxes: [{
                        scaleLabel: {
                            display: true,
                            labelString: 'Age Group (years)'
                        }
                    }]
                }
            }
        });
    }
</script>

