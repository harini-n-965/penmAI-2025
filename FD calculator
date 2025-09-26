<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fixed Deposit Calculator</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* A little extra style for the pie chart animation */
        .chart-slice {
            transition: stroke-dashoffset 0.5s ease-in-out;
        }
    </style>
</head>
<body class="bg-slate-100 flex items-center justify-center min-h-screen p-4 font-sans">

    <div class="w-full max-w-4xl bg-white rounded-2xl shadow-lg p-6 md:p-8 grid md:grid-cols-2 gap-8">
        
        <div class="flex flex-col">
            <h1 class="text-2xl md:text-3xl font-bold text-slate-800 mb-6">Fixed Deposit Calculator 💰</h1>
            
            <form id="fd-form" class="space-y-5">
                <div>
                    <label for="principal" class="block text-sm font-medium text-slate-600 mb-1">Principal Amount (₹)</label>
                    <input type="number" id="principal" name="principal" class="w-full p-3 bg-slate-50 border border-slate-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition" placeholder="e.g., 100000" required>
                </div>

                <div>
                    <label for="interestRate" class="block text-sm font-medium text-slate-600 mb-1">Annual Interest Rate (%)</label>
                    <input type="number" id="interestRate" name="interestRate" step="0.01" class="w-full p-3 bg-slate-50 border border-slate-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition" placeholder="e.g., 7.1" required>
                </div>

                <div>
                    <label class="block text-sm font-medium text-slate-600 mb-1">Tenure</label>
                    <div class="flex items-center gap-4">
                        <input type="number" id="years" name="years" class="w-full p-3 bg-slate-50 border border-slate-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition" placeholder="Years" min="0">
                        <input type="number" id="months" name="months" class="w-full p-3 bg-slate-50 border border-slate-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition" placeholder="Months" min="0" max="11">
                    </div>
                </div>
                
                <div>
                    <label for="compounding" class="block text-sm font-medium text-slate-600 mb-1">Compounding Frequency</label>
                    <select id="compounding" name="compounding" class="w-full p-3 bg-slate-50 border border-slate-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition">
                        <option value="12">Monthly</option>
                        <option value="4" selected>Quarterly</option>
                        <option value="2">Half-Yearly</option>
                        <option value="1">Annually</option>
                    </select>
                </div>

                <button type="submit" class="w-full bg-blue-600 text-white font-bold py-3 px-4 rounded-lg hover:bg-blue-700 focus:outline-none focus:ring-4 focus:ring-blue-300 transition-all duration-300 ease-in-out">
                    Calculate
                </button>
            </form>
        </div>

        <div id="results-section" class="bg-blue-50 rounded-lg p-6 md:p-8 flex-col justify-center items-center text-center hidden">
            <h2 class="text-xl font-semibold text-slate-700 mb-6">Maturity Details</h2>
            
            <div class="w-48 h-48 mb-6 relative">
                <svg viewBox="0 0 36 36" class="w-full h-full">
                    <path class="text-slate-200" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" fill="none" stroke="currentColor" stroke-width="3"></path>
                    <path id="interest-slice" class="chart-slice text-green-500" stroke="currentColor" stroke-width="3" fill="none" stroke-linecap="round" stroke-dasharray="0, 100" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831"></path>
                </svg>
                <div class="absolute inset-0 flex flex-col items-center justify-center">
                    <span class="text-xs text-slate-500">Maturity Value</span>
                    <span id="maturity-amount-chart" class="text-2xl font-bold text-slate-800"></span>
                </div>
            </div>

            <div class="w-full space-y-4 text-left">
                <div class="flex justify-between items-center p-3 bg-white/50 rounded-lg">
                    <span class="text-slate-600">Invested Amount</span>
                    <span id="invested-amount" class="font-semibold text-slate-800 text-lg"></span>
                </div>
                <div class="flex justify-between items-center p-3 bg-white/50 rounded-lg">
                    <span class="text-slate-600">Total Interest</span>
                    <span id="total-interest" class="font-semibold text-green-600 text-lg"></span>
                </div>
                <div class="flex justify-between items-center p-3 bg-blue-100 rounded-lg">
                    <span class="text-slate-600 font-bold">Maturity Amount</span>
                    <span id="maturity-amount" class="font-bold text-blue-700 text-lg"></span>
                </div>
            </div>
        </div>

        <div id="placeholder-section" class="bg-blue-50 rounded-lg p-8 flex flex-col justify-center items-center text-center">
             <svg xmlns="http://www.w3.org/2000/svg" class="h-20 w-20 text-blue-300 mb-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
            </svg>
            <h2 class="text-xl font-semibold text-slate-700">Your results will appear here</h2>
            <p class="text-slate-500 mt-2">Fill in the details on the left to get started.</p>
        </div>

    </div>

    <script>
        const form = document.getElementById('fd-form');
        const resultsSection = document.getElementById('results-section');
        const placeholderSection = document.getElementById('placeholder-section');

        // Result display elements
        const investedAmountEl = document.getElementById('invested-amount');
        const totalInterestEl = document.getElementById('total-interest');
        const maturityAmountEl = document.getElementById('maturity-amount');
        const maturityAmountChartEl = document.getElementById('maturity-amount-chart');
        const interestSliceEl = document.getElementById('interest-slice');

        // Indian Rupee currency formatter
        const currencyFormatter = new Intl.NumberFormat('en-IN', {
            style: 'currency',
            currency: 'INR',
            minimumFractionDigits: 2,
            maximumFractionDigits: 2,
        });

        form.addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent form from submitting the traditional way

            // 1. Get and Parse Inputs
            const principal = parseFloat(document.getElementById('principal').value);
            const rate = parseFloat(document.getElementById('interestRate').value);
            const years = parseInt(document.getElementById('years').value) || 0;
            const months = parseInt(document.getElementById('months').value) || 0;
            const n = parseInt(document.getElementById('compounding').value);

            // Basic validation
            if (isNaN(principal) || principal <= 0 || isNaN(rate) || rate <= 0 || (years <= 0 && months <= 0)) {
                alert("Please enter valid positive values for all fields.");
                return;
            }

            // 2. Calculate
            const rateDecimal = rate / 100;
            const totalYears = years + (months / 12);

            // A = P(1 + r/n)^(nt)
            const maturityAmount = principal * Math.pow((1 + rateDecimal / n), (n * totalYears));
            const totalInterest = maturityAmount - principal;
            
            // 3. Display Results
            displayResults(principal, totalInterest, maturityAmount);
        });

        function displayResults(principal, interest, maturity) {
            // Show results and hide placeholder
            resultsSection.classList.remove('hidden');
            resultsSection.classList.add('flex'); // Use flex to ensure proper alignment
            placeholderSection.classList.add('hidden');

            // Update text content
            investedAmountEl.textContent = currencyFormatter.format(principal);
            totalInterestEl.textContent = currencyFormatter.format(interest);
            maturityAmountEl.textContent = currencyFormatter.format(maturity);
            maturityAmountChartEl.textContent = currencyFormatter.format(maturity).replace('.00', '');

            // Update chart
            const interestPercentage = (interest / maturity) * 100;
            // The timeout makes the animation restart on each calculation
            setTimeout(() => {
                interestSliceEl.style.strokeDasharray = `${interestPercentage}, 100`;
            }, 10);
        }

    </script>
</body>
</html>
