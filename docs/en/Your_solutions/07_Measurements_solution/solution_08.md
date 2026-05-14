<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Task 08 – Mass-Spring Oscillation Simulator</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            max-width: 900px;
            margin: 50px auto;
            padding: 20px;
            background-color: #f5f5f5;
        }
        .container {
            background-color: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        h1, h2 {
            color: #333;
        }
        .simulator {
            text-align: center;
            margin: 20px 0;
            padding: 20px;
            background-color: #e8e8e8;
            border-radius: 8px;
        }
        canvas {
            background-color: white;
            border: 1px solid #ccc;
            margin: 10px 0;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }
        .controls {
            margin: 15px 0;
        }
        button {
            padding: 10px 20px;
            margin: 5px;
            font-size: 14px;
            cursor: pointer;
            background-color: #007acc;
            color: white;
            border: none;
            border-radius: 5px;
            transition: background-color 0.2s;
        }
        button:hover {
            background-color: #005a9e;
        }
        button:disabled {
            background-color: #aaa;
            cursor: not-allowed;
        }
        .measurement-table {
            margin: 20px 0;
            overflow-x: auto;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            background-color: white;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 8px;
            text-align: center;
        }
        th {
            background-color: #007acc;
            color: white;
        }
        .result {
            background-color: #d9f0ff;
            padding: 15px;
            border-radius: 5px;
            margin: 15px 0;
            font-family: monospace;
        }
        .formula {
            background-color: #f9f9f9;
            padding: 10px;
            border-left: 4px solid #007acc;
            margin: 10px 0;
            font-family: monospace;
        }
        input {
            padding: 5px;
            margin: 5px;
            width: 80px;
            text-align: center;
        }
        .note {
            font-size: 0.9em;
            color: #555;
            margin-top: 15px;
            padding: 10px;
            background-color: #fafafa;
            border-left: 3px solid #ffaa00;
        }
    </style>
</head>
<body>
<div class="container">
    <h1>Task 08 – Mass-Spring System: Period Measurements</h1>

    <div class="simulator">
        <h2>Mass-Spring Oscillator Simulator</h2>
        <canvas id="springCanvas" width="400" height="400"></canvas>
        <div class="controls">
            <div>
                <label>Mass (kg): <input type="number" id="massInput" value="0.5" step="0.1" min="0.1"></label>
                <label>Spring Constant (N/m): <input type="number" id="kInput" value="20" step="5" min="5"></label>
            </div>
            <div>
                <button id="startBtn">Start 10 Oscillations</button>
                <button id="resetBtn">Reset</button>
            </div>
            <div>
                <button id="measureBtn" disabled>Record Time (10 oscillations)</button>
            </div>
        </div>
    </div>

    <div class="measurement-table">
        <h3>Time Measurements (10 complete oscillations)</h3>
        <table id="dataTable">
            <thead>
                <tr><th>Measurement #</th><th>Time for 10 oscillations (s)</th><th>Period T (s)</th></tr>
            </thead>
            <tbody id="tableBody"></tbody>
        </table>
        <div style="margin-top: 10px;">
            <button id="clearDataBtn">Clear All Data</button>
        </div>
    </div>

    <div class="result" id="results">
        <h3>Calculated Spring Constant & Uncertainty</h3>
        <p id="calcResults">(Perform 10 measurements to see results)</p>
    </div>

    <div class="note">
        <strong>Note:</strong> The theoretical period for a mass-spring system is $T = 2\pi \sqrt{m/k}$.<br>
        Each "measurement" simulates timing 10 oscillations with ±0.05 s random uncertainty (simulating human reaction time).<br>
        Use the data to calculate the mean period and standard deviation, then determine $k$ and its uncertainty.
    </div>
</div>

<script>
    // Canvas setup
    const canvas = document.getElementById('springCanvas');
    const ctx = canvas.getContext('2d');
    
    // Simulation parameters
    let yOffset = 0;           // displacement from equilibrium (m)
    let velocity = 0;
    let mass = 0.5;            // kg
    let k = 20;                // N/m
    let equilibriumY = 200;    // equilibrium position (pixels)
    let amplitude = 0;         // current amplitude (m)
    let time = 0;
    let animFrameId = null;
    let isOscillating = false;
    let oscillationCount = 0;
    let maxOscillations = 10;
    let measuringActive = false;
    let measurementTimes = [];   // store measured times for 10 oscillations
    let measurementIndex = 0;
    let startTime = null;
    let oscillationStartCount = 0;
    let lastCrossTime = null;
    let crossDirection = 0;
    
    // DOM elements
    const massInput = document.getElementById('massInput');
    const kInput = document.getElementById('kInput');
    const startBtn = document.getElementById('startBtn');
    const resetBtn = document.getElementById('resetBtn');
    const measureBtn = document.getElementById('measureBtn');
    const clearDataBtn = document.getElementById('clearDataBtn');
    const tableBody = document.getElementById('tableBody');
    const calcResults = document.getElementById('calcResults');
    
    // Data storage for measurements
    let measurementList = [];   // stores {time10osc, period}
    
    // Physics constants
    let omega = Math.sqrt(k / mass);
    let theoreticalT = 2 * Math.PI / omega;
    
    function updatePhysicsParams() {
        mass = parseFloat(massInput.value);
        k = parseFloat(kInput.value);
        omega = Math.sqrt(k / mass);
        theoreticalT = 2 * Math.PI / omega;
    }
    
    function startOscillation() {
        if (animFrameId) cancelAnimationFrame(animFrameId);
        updatePhysicsParams();
        amplitude = 0.1;        // 10 cm initial displacement
        yOffset = amplitude;
        velocity = 0;
        time = 0;
        oscillationCount = 0;
        isOscillating = true;
        measuringActive = true;
        measureBtn.disabled = false;
        
        // Reset crossing detection
        lastCrossTime = null;
        crossDirection = 0;
        startTime = performance.now() / 1000;
        oscillationStartCount = 0;
        
        animate();
    }
    
    function resetSimulation() {
        if (animFrameId) cancelAnimationFrame(animFrameId);
        isOscillating = false;
        measuringActive = false;
        measureBtn.disabled = true;
        yOffset = 0;
        velocity = 0;
        oscillationCount = 0;
        time = 0;
        draw();
    }
    
    function animate() {
        if (!isOscillating) return;
        
        const dt = 1/60;  // 60 FPS simulation step
        const currentTimeSec = performance.now() / 1000;
        
        // Simple harmonic motion: x(t) = A * cos(omega * t)
        // Use simulation time
        time += dt;
        yOffset = amplitude * Math.cos(omega * time);
        velocity = -amplitude * omega * Math.sin(omega * time);
        
        // Count oscillations by zero crossing with direction
        const threshold = 0.001;
        const currentPos = yOffset;
        const currentVel = velocity;
        
        // Detect crossing from negative to positive (upward through equilibrium)
        if (Math.abs(currentPos) < threshold && currentVel > 0 && crossDirection !== 1) {
            crossDirection = 1;
            oscillationCount++;
            
            // Measure time for 10 oscillations
            if (measuringActive && oscillationCount % 10 === 0 && oscillationCount <= maxOscillations) {
                const now = performance.now() / 1000;
                if (oscillationCount === 10) {
                    const elapsed = now - startTime;
                    // Add simulated measurement uncertainty (±0.05 s random)
                    const uncertainty = (Math.random() - 0.5) * 0.1;
                    const measuredTime = elapsed + uncertainty;
                    recordMeasurement(measuredTime);
                    
                    if (measurementList.length >= 10) {
                        measuringActive = false;
                        measureBtn.disabled = true;
                        calculateResults();
                    }
                }
            }
        }
        // Reset direction detection
        if (Math.abs(currentPos) > 0.01) {
            if (currentPos > 0 && currentVel < 0) crossDirection = -1;
            else if (currentPos < 0 && currentVel > 0) crossDirection = 0;
        }
        
        draw();
        animFrameId = requestAnimationFrame(animate);
    }
    
    function recordMeasurement(time10osc) {
        const period = time10osc / 10;
        measurementList.push({
            time10osc: time10osc,
            period: period
        });
        updateTable();
    }
    
    function updateTable() {
        tableBody.innerHTML = '';
        for (let i = 0; i < measurementList.length; i++) {
            const row = tableBody.insertRow();
            row.insertCell(0).innerText = i + 1;
            row.insertCell(1).innerText = measurementList[i].time10osc.toFixed(2);
            row.insertCell(2).innerText = measurementList[i].period.toFixed(3);
        }
        // Fill empty rows if less than 10
        for (let i = measurementList.length; i < 10; i++) {
            const row = tableBody.insertRow();
            row.insertCell(0).innerText = i + 1;
            row.insertCell(1).innerText = '—';
            row.insertCell(2).innerText = '—';
        }
    }
    
    function clearData() {
        measurementList = [];
        updateTable();
        calcResults.innerHTML = '(Perform 10 measurements to see results)';
        measureBtn.disabled = true;
        measuringActive = false;
        if (isOscillating) resetSimulation();
    }
    
    function calculateResults() {
        if (measurementList.length < 2) {
            calcResults.innerHTML = 'Not enough data. Need at least 2 measurements.';
            return;
        }
        
        const massVal = parseFloat(massInput.value);
        
        // Extract periods
        const periods = measurementList.map(m => m.period);
        const N = periods.length;
        
        // Mean period
        const meanT = periods.reduce((a,b) => a + b, 0) / N;
        
        // Standard deviation of period
        let sumSq = 0;
        for (let T of periods) {
            sumSq += (T - meanT) ** 2;
        }
        const stdT = Math.sqrt(sumSq / (N - 1));
        
        // Calculate spring constant from mean period: T = 2π √(m/k) => k = 4π² m / T²
        const kCalc = (4 * Math.PI * Math.PI * massVal) / (meanT * meanT);
        
        // Uncertainty propagation: Δk/k = 2 ΔT/T (since m has zero uncertainty)
        const relUncertaintyK = 2 * (stdT / meanT);
        const absUncertaintyK = kCalc * relUncertaintyK;
        
        // Theoretical k from input
        const theoreticalK = parseFloat(kInput.value);
        
        calcResults.innerHTML = `
            <strong>Mean period:</strong> T̄ = ${meanT.toFixed(4)} s<br>
            <strong>Standard deviation of period:</strong> σ<sub>T</sub> = ${stdT.toFixed(4)} s<br>
            <strong>Calculated spring constant:</strong> k = ${kCalc.toFixed(2)} N/m<br>
            <strong>Absolute uncertainty (Δk):</strong> ${absUncertaintyK.toFixed(2)} N/m<br>
            <strong>Result:</strong> k = (${kCalc.toFixed(2)} ± ${absUncertaintyK.toFixed(2)}) N/m<br>
            <strong>Theoretical k (simulator):</strong> ${theoreticalK.toFixed(2)} N/m<br>
            <strong>Relative uncertainty in k:</strong> ${(relUncertaintyK * 100).toFixed(2)}%
        `;
    }
    
    function draw() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        
        // Draw background
        ctx.fillStyle = '#f0f0f0';
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        
        // Draw support
        ctx.fillStyle = '#888';
        ctx.fillRect(150, 20, 100, 20);
        ctx.fillStyle = '#666';
        ctx.fillRect(190, 40, 20, 60);
        
        // Draw spring (coil approximation)
        const yTop = 100;
        const yBottom = equilibriumY + yOffset * 100;  // scale 1 m = 100 pixels
        ctx.beginPath();
        ctx.moveTo(200, yTop);
        const coils = 12;
        for (let i = 0; i <= coils; i++) {
            const t = i / coils;
            const y = yTop + (yBottom - yTop) * t;
            const x = 200 + (i % 2 === 0 ? 15 : -15);
            ctx.lineTo(x, y);
        }
        ctx.lineTo(200, yBottom);
        ctx.strokeStyle = '#b87333';
        ctx.lineWidth = 3;
        ctx.stroke();
        
        // Draw mass
        ctx.fillStyle = '#3a6ea5';
        ctx.fillRect(175, yBottom - 20, 50, 40);
        ctx.fillStyle = '#2c4d6e';
        ctx.fillRect(175, yBottom - 20, 50, 10);
        
        // Draw equilibrium line
        ctx.beginPath();
        ctx.moveTo(150, equilibriumY);
        ctx.lineTo(250, equilibriumY);
        ctx.strokeStyle = '#aaa';
        ctx.setLineDash([5, 5]);
        ctx.stroke();
        ctx.setLineDash([]);
        
        // Display info
        ctx.font = '14px Arial';
        ctx.fillStyle = '#333';
        ctx.fillText(`Oscillations: ${oscillationCount}`, 10, 30);
        ctx.fillText(`Measurements: ${measurementList.length}/10`, 10, 50);
    }
    
    // Event listeners
    startBtn.addEventListener('click', () => {
        if (measurementList.length >= 10) {
            alert('Already have 10 measurements. Click "Clear All Data" to start over.');
            return;
        }
        startOscillation();
    });
    
    resetBtn.addEventListener('click', () => {
        resetSimulation();
        draw();
    });
    
    clearDataBtn.addEventListener('click', clearData);
    
    // Initial draw
    draw();
    updateTable();
</script>
</body>
</html>
