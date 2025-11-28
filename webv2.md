<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aspect: Vision & Strategy Dashboard</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        /* Custom font settings and transitions */
        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            transition: background-color 0.3s ease;
        }
        .skin-transition {
            transition: all 0.3s ease-in-out;
        }
        
        /* Chart Container Strict Styling */
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px; /* Max width to prevent stretching */
            height: 300px;    /* Base height */
            max-height: 350px;
            margin-left: auto;
            margin-right: auto;
        }

        /* Mission Node Styling */
        .mission-node {
            transition: all 0.2s ease;
        }
        .mission-node.active {
            transform: scale(1.05);
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-800">

    <!-- Application Structure Plan:
         1. Header & Context: Introduces the "North Star" vision. Includes the "Dual Skin" toggle (Voyager vs. Professional) as a primary interaction to demonstrate the branding strategy.
         2. The 4 Pillars (Architecture): A grid layout explaining Engine, Twin, Veil, Journal. Content updates based on the Skin Toggle.
         3. The Mission Loop (Interactive Demo): A linear flow visualization of the "Numeracy L1" specific example. Users click nodes (Vision -> Action -> Resolve -> Log) to see the specific prompts/UI for that stage.
         4. Strategy & Logic (Data Viz): Charts showing the Scoring Logic (Pass/Near Miss/Fail) and the Roadmap Scope (Tiny POC vs Full Universe) to validate the "build small" advice.
    -->

    <!-- Chosen Palette: Warm Neutrals (Slate-50) with 'Voyager' Amber-600 and 'Professional' Blue-600 accents. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->

    <!-- Navigation / Header -->
    <nav class="w-full bg-white border-b border-slate-200 sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16 items-center">
                <div class="flex items-center gap-3">
                    <div class="w-8 h-8 bg-slate-800 rounded-sm flex items-center justify-center text-white font-bold text-xl">A</div>
                    <span class="font-bold text-xl tracking-tight">Aspect <span class="font-normal text-slate-500">Mission Control</span></span>
                </div>
                <div class="flex items-center gap-4">
                    <span class="text-sm font-medium text-slate-500">View Mode:</span>
                    <button id="skinToggle" class="relative inline-flex h-8 w-40 items-center justify-center rounded-full bg-slate-200 p-1 transition-colors focus:outline-none">
                        <div id="skinIndicator" class="absolute left-1 top-1 h-6 w-[48%] rounded-full bg-white shadow-sm transition-all duration-300"></div>
                        <span class="z-10 w-1/2 text-center text-xs font-bold text-slate-700" id="btn-pro">Professional</span>
                        <span class="z-10 w-1/2 text-center text-xs font-medium text-slate-500" id="btn-voyager">Voyager</span>
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 space-y-12">

        <!-- Hero: The Vision -->
        <section class="text-center max-w-4xl mx-auto">
            <h1 class="text-4xl font-extrabold tracking-tight text-slate-900 sm:text-5xl mb-4 skin-target" 
                data-pro="The Unified Progression Layer" 
                data-voyager="The Skill Universe">
                The Unified Progression Layer
            </h1>
            <p class="text-lg text-slate-600 mb-8 skin-target" 
               data-pro="A persistent progression engine that sits on top of any curriculum. It organizes learning into sectors and presents it through one consistent cockpit."
               data-voyager="A Mission Control System for personal growth. Not just a skill tree, but a persistent mirror of your journey through the galaxy of skills.">
                A persistent progression engine that sits on top of any curriculum. It organizes learning into sectors and presents it through one consistent cockpit.
            </p>
            <div class="flex justify-center gap-2">
                <span class="inline-flex items-center rounded-full bg-blue-50 px-3 py-1 text-xs font-medium text-blue-700 ring-1 ring-inset ring-blue-700/10">Architecture v2</span>
                <span class="inline-flex items-center rounded-full bg-green-50 px-3 py-1 text-xs font-medium text-green-700 ring-1 ring-inset ring-green-600/20">Status: Defined</span>
            </div>
        </section>

        <!-- Section 1: The 4 Pillars Architecture -->
        <section>
            <div class="mb-6 border-l-4 border-blue-500 pl-4">
                <h2 class="text-2xl font-bold text-slate-900">Core Architecture</h2>
                <p class="text-slate-600 mt-1">The system is built on four immutable pillars that drive every interaction, regardless of the subject matter.</p>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                <!-- Pillar 1: Engine -->
                <div class="bg-white rounded-xl shadow-sm border border-slate-200 p-6 hover:shadow-md transition-shadow">
                    <div class="h-10 w-10 rounded-lg bg-slate-100 flex items-center justify-center mb-4 text-2xl">⚙️</div>
                    <h3 class="text-lg font-bold mb-2 skin-target text-slate-900" 
                        data-pro="Adaptive Engine" 
                        data-voyager="The Engine">Adaptive Engine</h3>
                    <p class="text-sm text-slate-600 skin-target"
                       data-pro="The backend logic that handles rules, state, difficulty adjustments, and outcome calculations."
                       data-voyager="The invisible laws of physics that govern the universe, difficulty, and your survival probabilities.">
                       The backend logic that handles rules, state, difficulty adjustments, and outcome calculations.
                    </p>
                </div>

                <!-- Pillar 2: Twin -->
                <div class="bg-white rounded-xl shadow-sm border border-slate-200 p-6 hover:shadow-md transition-shadow">
                    <div class="h-10 w-10 rounded-lg bg-slate-100 flex items-center justify-center mb-4 text-2xl">🪞</div>
                    <h3 class="text-lg font-bold mb-2 skin-target text-slate-900" 
                        data-pro="User Dashboard" 
                        data-voyager="The Twin">User Dashboard</h3>
                    <p class="text-sm text-slate-600 skin-target"
                       data-pro="The persistent UI layer showing XP, skill trees, and sector progress. The 'Cockpit'."
                       data-voyager="Your digital mirror. A persistent reflection of your capabilities, growing as you grow.">
                       The persistent UI layer showing XP, skill trees, and sector progress. The 'Cockpit'.
                    </p>
                </div>

                <!-- Pillar 3: Veil -->
                <div class="bg-white rounded-xl shadow-sm border border-slate-200 p-6 hover:shadow-md transition-shadow">
                    <div class="h-10 w-10 rounded-lg bg-slate-100 flex items-center justify-center mb-4 text-2xl">🤖</div>
                    <h3 class="text-lg font-bold mb-2 skin-target text-slate-900" 
                        data-pro="AI Tutor / Co-Pilot" 
                        data-voyager="The Veil">AI Tutor / Co-Pilot</h3>
                    <p class="text-sm text-slate-600 skin-target"
                       data-pro="The interactive interface delivering content, instructions, and real-time feedback."
                       data-voyager="The interface between you and the raw data. Your ship's AI voice guiding you through the noise.">
                       The interactive interface delivering content, instructions, and real-time feedback.
                    </p>
                </div>

                <!-- Pillar 4: Journal -->
                <div class="bg-white rounded-xl shadow-sm border border-slate-200 p-6 hover:shadow-md transition-shadow">
                    <div class="h-10 w-10 rounded-lg bg-slate-100 flex items-center justify-center mb-4 text-2xl">📓</div>
                    <h3 class="text-lg font-bold mb-2 skin-target text-slate-900" 
                        data-pro="Reflection Console" 
                        data-voyager="The Journal">Reflection Console</h3>
                    <p class="text-sm text-slate-600 skin-target"
                       data-pro="Structured inputs for metacognition and emotional logging after tasks."
                       data-voyager="Where you log the psychological toll of the mission. The Captain's Log.">
                       Structured inputs for metacognition and emotional logging after tasks.
                    </p>
                </div>
            </div>
        </section>

        <!-- Section 2: Interactive Mission Loop -->
        <section class="bg-slate-900 rounded-2xl overflow-hidden shadow-xl text-white">
            <div class="p-6 md:p-8 border-b border-slate-700 bg-slate-800/50">
                <div class="flex flex-col md:flex-row md:items-center justify-between gap-4">
                    <div>
                        <h2 class="text-2xl font-bold text-white mb-1">Mission Simulator: <span class="text-blue-400">Numeracy L1</span></h2>
                        <p class="text-slate-400 text-sm">Experience the "Find the Off Signal" mission loop. Click the phases below.</p>
                    </div>
                    <div class="flex items-center gap-2 bg-slate-900 px-3 py-1 rounded-lg border border-slate-700">
                        <span class="h-2 w-2 rounded-full bg-green-500 animate-pulse"></span>
                        <span class="text-xs font-mono uppercase tracking-widest text-slate-400">System Online</span>
                    </div>
                </div>
            </div>

            <!-- Flow Diagram / Stepper -->
            <div class="p-6 md:p-8 grid grid-cols-4 gap-2 relative">
                <!-- Connecting Line -->
                <div class="absolute top-[3.25rem] left-[10%] right-[10%] h-0.5 bg-slate-700 -z-10"></div>
                
                <!-- Step 1 -->
                <div onclick="setMissionStep(0)" class="mission-node cursor-pointer group text-center" id="step-0">
                    <div class="w-12 h-12 mx-auto rounded-full bg-blue-600 border-4 border-slate-900 flex items-center justify-center text-white font-bold mb-3 shadow-lg group-hover:bg-blue-500 transition-colors relative z-10">1</div>
                    <span class="text-sm font-medium text-blue-400 uppercase tracking-wide">Vision</span>
                </div>
                <!-- Step 2 -->
                <div onclick="setMissionStep(1)" class="mission-node cursor-pointer group text-center opacity-50" id="step-1">
                    <div class="w-12 h-12 mx-auto rounded-full bg-slate-700 border-4 border-slate-900 flex items-center justify-center text-white font-bold mb-3 shadow-lg group-hover:bg-slate-600 transition-colors relative z-10">2</div>
                    <span class="text-sm font-medium text-slate-400 uppercase tracking-wide">Action</span>
                </div>
                <!-- Step 3 -->
                <div onclick="setMissionStep(2)" class="mission-node cursor-pointer group text-center opacity-50" id="step-2">
                    <div class="w-12 h-12 mx-auto rounded-full bg-slate-700 border-4 border-slate-900 flex items-center justify-center text-white font-bold mb-3 shadow-lg group-hover:bg-slate-600 transition-colors relative z-10">3</div>
                    <span class="text-sm font-medium text-slate-400 uppercase tracking-wide">Resolve</span>
                </div>
                <!-- Step 4 -->
                <div onclick="setMissionStep(3)" class="mission-node cursor-pointer group text-center opacity-50" id="step-3">
                    <div class="w-12 h-12 mx-auto rounded-full bg-slate-700 border-4 border-slate-900 flex items-center justify-center text-white font-bold mb-3 shadow-lg group-hover:bg-slate-600 transition-colors relative z-10">4</div>
                    <span class="text-sm font-medium text-slate-400 uppercase tracking-wide">Log</span>
                </div>
            </div>

            <!-- Dynamic Content Area -->
            <div class="px-6 md:px-8 pb-8">
                <div class="bg-slate-800 rounded-xl p-6 border border-slate-700 min-h-[300px] flex flex-col md:flex-row gap-8">
                    
                    <!-- Left: The Interface (Veil) -->
                    <div class="flex-1 space-y-4">
                        <div class="flex items-center gap-2 mb-2">
                            <span class="text-xs font-mono text-blue-400 uppercase" id="phase-label">Phase: Vision (Low Cognitive Load)</span>
                        </div>
                        <div class="bg-slate-900 rounded-lg p-4 font-mono text-sm text-green-400 border-l-2 border-green-500 shadow-inner">
                            <p class="mb-2 opacity-75">// Veil Interface</p>
                            <p id="veil-text" class="text-lg leading-relaxed text-slate-200">
                                "Operator, I’ve pulled yesterday’s delivery log. One of these rows is lying. Don’t calculate everything. Just scan and trust your sense of ‘that looks off’."
                            </p>
                        </div>
                        <div class="bg-white rounded-lg p-3 shadow-sm border border-slate-200 overflow-hidden">
                            <table class="w-full text-xs text-left text-slate-600">
                                <thead class="bg-slate-100 font-bold">
                                    <tr><th class="p-2">ID</th><th class="p-2">Boxes</th><th class="p-2">Unit Kg</th><th class="p-2">Total Kg</th></tr>
                                </thead>
                                <tbody>
                                    <tr class="border-b"><td class="p-2">101</td><td class="p-2">40</td><td class="p-2">2.0</td><td class="p-2">80</td></tr>
                                    <tr class="border-b bg-red-50"><td class="p-2 font-bold text-red-600">105</td><td class="p-2">10</td><td class="p-2">1.5</td><td class="p-2 font-bold">10</td></tr>
                                    <tr><td class="p-2">103</td><td class="p-2">20</td><td class="p-2">3.0</td><td class="p-2">60</td></tr>
                                </tbody>
                            </table>
                        </div>
                        <p class="text-xs text-slate-500 italic mt-2" id="user-task">User Task: Select row 105.</p>
                    </div>

                    <!-- Right: The Engine Logic -->
                    <div class="w-full md:w-1/3 border-l border-slate-700 pl-0 md:pl-8 flex flex-col justify-center">
                        <h4 class="text-sm font-bold text-slate-400 uppercase tracking-widest mb-4">Engine Logic</h4>
                        <div class="space-y-3" id="engine-stats">
                            <!-- Injected via JS -->
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section 3: Data & Strategy (Visualizations) -->
        <section class="grid grid-cols-1 lg:grid-cols-2 gap-8">
            <!-- Viz 1: Scoring Logic -->
            <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                <div class="mb-6">
                    <h3 class="text-lg font-bold text-slate-900">Engine Grading Logic</h3>
                    <p class="text-sm text-slate-500">How the "Off Signal" mission is scored to determine progression.</p>
                </div>
                
                <!-- Chart Container 1 -->
                <div class="chart-container">
                    <canvas id="scoringChart"></canvas>
                </div>
                <div class="mt-4 text-xs text-slate-500 text-center">
                    Logic: Prioritizes "attempting to scan" (Near Miss) over pure guessing.
                </div>
            </div>

            <!-- Viz 2: Roadmap Scope -->
            <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
                <div class="mb-6">
                    <h3 class="text-lg font-bold text-slate-900">Strategic Roadmap</h3>
                    <p class="text-sm text-slate-500">Value vs. Effort: Why "Tiny POC" is the next step.</p>
                </div>
                
                <!-- Chart Container 2 -->
                <div class="chart-container">
                    <canvas id="roadmapChart"></canvas>
                </div>
                <div class="mt-4 text-xs text-slate-500 text-center">
                    Recommendation: Focus on the "Tiny POC" zone (High Value, Low Effort).
                </div>
            </div>
        </section>

        <!-- Footer -->
        <footer class="border-t border-slate-200 pt-8 pb-12">
            <div class="text-center">
                <p class="text-slate-400 text-sm">Aspect Internal Strategy Doc • Version 2.0 (Universe)</p>
                <p class="text-slate-300 text-xs mt-2">Use strictly for architecture planning. Do not use for v1 sales.</p>
            </div>
        </footer>

    </main>

    <script>
        // --- State Management ---
        const state = {
            skin: 'pro', // 'pro' or 'voyager'
            currentMissionStep: 0
        };

        // --- Data: Mission Steps ---
        const missionData = [
            {
                phase: "Phase 1: Vision (Pattern Recognition)",
                veil: "\"Operator, I’ve pulled yesterday’s delivery log. One of these rows is lying. Don’t calculate everything. Just scan and trust your sense of 'that looks off'.\"",
                task: "User Task: Identify the suspicious row without calculation tools.",
                engine: `
                    <div class="bg-slate-900 p-3 rounded text-xs font-mono text-green-300 mb-2">
                        mission_id: NUM_L1_M1<br>
                        outcome:<br>
                        &nbsp;&nbsp;PASS -> score 1.0<br>
                        &nbsp;&nbsp;NEAR_MISS -> score 0.6<br>
                        &nbsp;&nbsp;FAIL -> score 0.0
                    </div>
                    <p class="text-xs text-slate-400">Near Miss Trigger: User selects wrong row but takes >10s scanning.</p>
                `
            },
            {
                phase: "Phase 2: Action (Calculation)",
                veil: "\"Now let’s confirm your suspicion with real numbers. Same table, but this time you must calculate the correct weight.\"",
                task: "User Task: Enter the correct value (15) for shipment 105.",
                engine: `
                    <div class="bg-slate-900 p-3 rounded text-xs font-mono text-green-300 mb-2">
                        mission_id: NUM_L1_M2<br>
                        outcome:<br>
                        &nbsp;&nbsp;FULL_PASS -> 1.0<br>
                        &nbsp;&nbsp;PARTIAL_MATH -> 0.7<br>
                        &nbsp;&nbsp;PARTIAL_PATTERN -> 0.5
                    </div>
                    <p class="text-xs text-slate-400">Differentiates between math errors and logic errors.</p>
                `
            },
            {
                phase: "Phase 3: Resolve (Communication)",
                veil: "\"In real operations, someone has to explain what’s wrong in plain language. You’re writing that explanation now, for a busy supervisor.\"",
                task: "User Task: Write 2-3 sentences explaining the error and the fix.",
                engine: `
                    <div class="bg-slate-900 p-3 rounded text-xs font-mono text-green-300 mb-2">
                        mission_id: NUM_L1_M3<br>
                        Keyword Check:<br>
                        [x] '105' OR 'South Hub'<br>
                        [x] '15' OR 'incorrect total'<br>
                        [x] 'fix' OR 'update'
                    </div>
                    <p class="text-xs text-slate-400">Simple keyword heuristic for v1 grading.</p>
                `
            },
            {
                phase: "Phase 4: Log (Reflection)",
                veil: "\"In one sentence: what made this feel easy or hard? (e.g. 'I felt rushed', 'Too many numbers', 'I just guessed')\"",
                task: "User Task: Select a journal tag or write a brief reflection.",
                engine: `
                    <div class="bg-slate-900 p-3 rounded text-xs font-mono text-green-300 mb-2">
                        journal_tag:<br>
                        "felt_rushed" / "guessed"<br>
                        sector_status:<br>
                        IF avg_score > 0.7 -> STABLE
                    </div>
                    <p class="text-xs text-slate-400">Data feeds back into the Engine to adjust future difficulty.</p>
                `
            }
        ];

        // --- Interaction Logic: Mission Loop ---
        function setMissionStep(index) {
            state.currentMissionStep = index;
            
            // Update UI Nodes
            document.querySelectorAll('.mission-node').forEach((node, i) => {
                const circle = node.querySelector('div');
                const label = node.querySelector('span');
                
                if (i === index) {
                    node.classList.remove('opacity-50');
                    node.classList.add('active');
                    circle.classList.remove('bg-slate-700', 'group-hover:bg-slate-600');
                    circle.classList.add('bg-blue-600', 'group-hover:bg-blue-500');
                    label.classList.remove('text-slate-400');
                    label.classList.add('text-blue-400');
                } else {
                    node.classList.add('opacity-50');
                    node.classList.remove('active');
                    circle.classList.add('bg-slate-700', 'group-hover:bg-slate-600');
                    circle.classList.remove('bg-blue-600', 'group-hover:bg-blue-500');
                    label.classList.add('text-slate-400');
                    label.classList.remove('text-blue-400');
                }
            });

            // Update Content
            const data = missionData[index];
            document.getElementById('phase-label').textContent = data.phase;
            document.getElementById('veil-text').textContent = data.veil;
            document.getElementById('user-task').textContent = data.task;
            document.getElementById('engine-stats').innerHTML = data.engine;
        }

        // --- Interaction Logic: Dual Skin Toggle ---
        function toggleSkin() {
            state.skin = state.skin === 'pro' ? 'voyager' : 'pro';
            updateSkinUI();
        }

        function updateSkinUI() {
            const isPro = state.skin === 'pro';
            const btnPro = document.getElementById('btn-pro');
            const btnVoyager = document.getElementById('btn-voyager');
            const indicator = document.getElementById('skinIndicator');

            // Button Styles
            if (isPro) {
                indicator.style.transform = 'translateX(0)';
                btnPro.classList.add('font-bold', 'text-slate-700');
                btnPro.classList.remove('font-medium', 'text-slate-500');
                btnVoyager.classList.remove('font-bold', 'text-slate-700');
                btnVoyager.classList.add('font-medium', 'text-slate-500');
            } else {
                indicator.style.transform = 'translateX(100%)';
                btnVoyager.classList.add('font-bold', 'text-slate-700');
                btnVoyager.classList.remove('font-medium', 'text-slate-500');
                btnPro.classList.remove('font-bold', 'text-slate-700');
                btnPro.classList.add('font-medium', 'text-slate-500');
            }

            // Text Content Swap
            document.querySelectorAll('.skin-target').forEach(el => {
                const newText = el.getAttribute(`data-${state.skin}`);
                if (newText) {
                    // Simple fade effect
                    el.style.opacity = '0';
                    setTimeout(() => {
                        el.textContent = newText;
                        el.style.opacity = '1';
                    }, 200);
                }
            });
        }

        document.getElementById('skinToggle').addEventListener('click', toggleSkin);

        // --- Charts Initialization ---
        document.addEventListener('DOMContentLoaded', () => {
            // Initialize Default State
            setMissionStep(0);
            
            // Chart 1: Scoring Logic (Bar)
            const ctxScore = document.getElementById('scoringChart').getContext('2d');
            new Chart(ctxScore, {
                type: 'bar',
                data: {
                    labels: ['Pass (Full)', 'Near Miss (Tried)', 'Fail (Skipped)'],
                    datasets: [{
                        label: 'Engine Score Value',
                        data: [1.0, 0.6, 0.0],
                        backgroundColor: ['#2563eb', '#93c5fd', '#e2e8f0'],
                        borderRadius: 6,
                        barThickness: 40
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: { display: false },
                        tooltip: {
                            callbacks: {
                                label: (ctx) => `Score: ${ctx.raw} (Logic applied)`
                            }
                        }
                    },
                    scales: {
                        y: { beginAtZero: true, max: 1.2 }
                    }
                }
            });

            // Chart 2: Roadmap Scope (Bubble/Scatter)
            // Visualizing "Tiny POC" vs "Full Universe" in terms of Effort vs Value
            const ctxRoadmap = document.getElementById('roadmapChart').getContext('2d');
            new Chart(ctxRoadmap, {
                type: 'bubble',
                data: {
                    datasets: [
                        {
                            label: 'Tiny POC (Recommended)',
                            data: [{x: 2, y: 8, r: 15}], // Low Effort, High Proof Value
                            backgroundColor: '#22c55e'
                        },
                        {
                            label: 'Small v1',
                            data: [{x: 5, y: 7, r: 10}], // Med Effort, Med Value
                            backgroundColor: '#3b82f6'
                        },
                        {
                            label: 'Full Universe (Vision)',
                            data: [{x: 9, y: 9, r: 25}], // High Effort, High Long-term Value
                            backgroundColor: '#fbbf24'
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        x: {
                            title: { display: true, text: 'Dev Effort / Complexity (Months)' },
                            min: 0, max: 10
                        },
                        y: {
                            title: { display: true, text: 'Strategic Validation Value' },
                            min: 0, max: 10
                        }
                    },
                    plugins: {
                        tooltip: {
                            callbacks: {
                                label: (ctx) => `${ctx.dataset.label}: Effort ${ctx.raw.x}, Value ${ctx.raw.y}`
                            }
                        }
                    }
                }
            });
        });
    </script>
</body>
</html>
