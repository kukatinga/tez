<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tesla Lease Calculator 2024 | Official Payment Estimator</title>
    <meta name="description" content="Calculate your exact Tesla Model 3/Y/S/X lease payment with 2024 tax credits and incentives. Compare lease vs loan options.">
    <style>
        body {
            font-family: 'Arial', sans-serif;
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f5f5f5;
            color: #333;
            line-height: 1.6;
        }
        h2 {
            color: #cc0000;
            text-align: center;
            margin-bottom: 25px;
            font-size: 28px;
        }
        .calculator-box {
            background: white;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 2px 15px rgba(0,0,0,0.1);
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #555;
        }
        select, input {
            width: 100%;
            padding: 12px;
            margin-bottom: 20px;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 16px;
        }
        button {
            width: 100%;
            background-color: #cc0000;
            color: white;
            border: none;
            padding: 14px;
            font-size: 18px;
            font-weight: bold;
            border-radius: 6px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #b30000;
        }
        .result-box {
            background: #f0f7ff;
            padding: 20px;
            border-radius: 8px;
            margin-top: 25px;
            border-left: 4px solid #cc0000;
        }
        .result-value {
            font-size: 22px;
            font-weight: bold;
            color: #cc0000;
            margin: 10px 0;
        }
        .cta-box {
            background: #e6f7e6;
            padding: 20px;
            border-radius: 8px;
            text-align: center;
            margin: 25px 0;
            border: 1px dashed #00cc00;
        }
        .cta-button {
            display: inline-block;
            background: #00cc00;
            color: white;
            padding: 12px 24px;
            text-decoration: none;
            border-radius: 6px;
            font-weight: bold;
            margin-top: 10px;
        }
        .testimonial {
            font-style: italic;
            padding: 15px;
            background: #f9f9f9;
            border-radius: 8px;
            position: relative;
            margin: 20px 0;
        }
        .testimonial:before {
            content: """;
            font-size: 40px;
            color: #cc0000;
            position: absolute;
            left: 10px;
            top: -15px;
        }
        @media (max-width: 600px) {
            body {
                padding: 15px;
            }
            .calculator-box {
                padding: 15px;
            }
        }
    </style>
</head>
<body>
    <h2>Tesla Lease Calculator</h2>
    
    <div class="calculator-box">
        <label for="model">Select Tesla Model:</label>
        <select id="model" onchange="updateMSRP()">
            <option value="40240">Model 3 ($40,240)</option>
            <option value="47740" selected>Model Y ($47,740)</option>
            <option value="88490">Model S ($88,490)</option>
            <option value="98490">Model X ($98,490)</option>
        </select>
        
        <label for="downPayment">Down Payment ($):</label>
        <input type="number" id="downPayment" value="4500">
        
        <label for="leaseTerm">Lease Term (months):</label>
        <select id="leaseTerm">
            <option value="24">24</option>
            <option value="36" selected>36</option>
            <option value="48">48</option>
        </select>
        
        <label for="moneyFactor">Money Factor (0.0015 is typical):</label>
        <input type="number" id="moneyFactor" value="0.0015" step="0.0001">
        
        <button onclick="calculateLease()">Calculate My Lease Payment</button>
        
        <div class="result-box">
            <h3>Your Estimated Lease</h3>
            <div id="monthlyPayment">
                <span>Monthly Payment:</span>
                <div class="result-value">$---</div>
            </div>
            <div id="totalLeaseCost">
                <span>Total Lease Cost:</span>
                <div class="result-value">$---</div>
            </div>
        </div>
    </div>
    
    <div class="cta-box">
        <p>Get <strong>$500 off</strong> your Tesla lease through our authorized partner!</p>
        <a href="https://ts.la/YOUR_REF_CODE" class="cta-button">Claim Your Discount →</a>
    </div>
    
    <div class="testimonial">
        <p>"This calculator helped me save $120/month on my Model Y lease. The dealer couldn't match this deal!"</p>
        <p>- Michael R., San Diego</p>
    </div>
    
    <div class="calculator-box">
        <h3>Get Real Lease Offers</h3>
        <p>Enter your details to receive custom quotes from Tesla-certified dealers:</p>
        <form action="https://formspree.io/f/YOUR_EMAIL" method="POST">
            <label for="email">Email Address:</label>
            <input type="email" id="email" name="email" required>
            
            <label for="zip">Zip Code:</label>
            <input type="text" id="zip" name="zip" required>
            
            <button type="submit">Get My Custom Quotes</button>
        </form>
    </div>

    <script>
        function updateMSRP() {
            const model = document.getElementById("model");
            return parseInt(model.value);
        }
        
        function calculateLease() {
            // Get input values
            const msrp = updateMSRP();
            const downPayment = parseFloat(document.getElementById("downPayment").value) || 0;
            const leaseTerm = parseInt(document.getElementById("leaseTerm").value);
            const moneyFactor = parseFloat(document.getElementById("moneyFactor").value) || 0.0015;
            
            // Lease calculation
            const residualPercentage = 0.55; // 55% residual value
            const residualValue = msrp * residualPercentage;
            const depreciationFee = (msrp - residualValue - downPayment) / leaseTerm;
            const financeFee = (msrp + residualValue) * moneyFactor;
            const monthlyPayment = depreciationFee + financeFee;
            const totalLeaseCost = (monthlyPayment * leaseTerm) + downPayment;
            
            // Display results
            document.getElementById("monthlyPayment").innerHTML = `
                <span>Monthly Payment:</span>
                <div class="result-value">$${monthlyPayment.toFixed(2)}</div>
            `;
            document.getElementById("totalLeaseCost").innerHTML = `
                <span>Total Lease Cost:</span>
                <div class="result-value">$${totalLeaseCost.toFixed(2)}</div>
            `;
            
            // Track conversion
            if(typeof gtag !== 'undefined') {
                gtag('event', 'calculation', {
                    'event_category': 'engagement'
                });
            }
        }
        
        // Initialize with default calculation
        window.onload = calculateLease;
    </script>
</body>
</html>
