<!DOCTYPE html>
<html>
<head>
    <style>
        .input-group {
            margin-bottom: 10px;
        }
        .input-group label {
            display: block;
            margin-bottom: 5px;
        }
    </style>
</head>
<body>
    <div class="input-group">
        <label for="cabinCount">Number of Cabins:</label>
        <input type="number" id="cabinCount" value="0">
    </div>
    <div class="input-group">
        <label for="pricePerNight">Price per Night:</label>
        <input type="number" id="pricePerNight" value="0">
    </div>
    <div class="input-group">
        <label for="operationCost">Operation Cost (per cabin, per night):</label>
        <input type="number" id="operationCost" value="0">
    </div>
    <div class="input-group">
        <label for="cabinCost">Cost of each Cabin:</label>
        <input type="number" id="cabinCost" value="0">
    </div>
    <div class="input-group">
        <label for="occupancyDays">Occupancy Days (per year):</label>
        <input type="number" id="occupancyDays" value="0">
    </div>
    <button onclick="calculateROI()">Calculate ROI</button>

    <div id="results" style="margin-top: 20px;">
        <p id="cabinCostResult"></p>
        <p id="yearsToPayOff"></p>
        <p id="annualProfit"></p>
    </div>

    <script>
        function calculateROI() {
            var cabinCount = document.getElementById('cabinCount').value;
            var pricePerNight = document.getElementById('pricePerNight').value;
            var operationCost = document.getElementById('operationCost').value;
            var cabinCost = document.getElementById('cabinCost').value;
            var occupancyDays = document.getElementById('occupancyDays').value;

            var totalCabinCost = cabinCount * cabinCost;
            var yearsToPayOff = totalCabinCost / ((pricePerNight - operationCost) * cabinCount * occupancyDays);
            var annualProfit = (pricePerNight - operationCost) * cabinCount * occupancyDays * (1 - 1 / yearsToPayOff);

            document.getElementById('cabinCostResult').innerText = 'Total Cabin Cost: $' + totalCabinCost;
            document.getElementById('yearsToPayOff').innerText = 'Years to Pay Off: ' + yearsToPayOff.toFixed(2);
            document.getElementById('annualProfit').innerText = 'Annual Profit: $' + annualProfit.toFixed(2);
        }
    </script>
</body>
</html>
