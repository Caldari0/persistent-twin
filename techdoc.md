<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aspect: Pilot Sector Strategy</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&family=Orbitron:wght@400;700;900&display=swap');

        :root {
            --bg: #050508;
            --card-bg: #0b0c15;
            --text-main: #e2e8f0;
            --text-muted: #94a3b8;
            --accent: #00f3ff;
            --accent-dim: rgba(0, 243, 255, 0.1);
            --border: rgba(0, 243, 255, 0.2);
            --success: #05ffa1;
            --danger: #ff2a6d;
        }

        body {
            background-color: var(--bg);
            color: var(--text-main);
            font-family: 'Inter', sans-serif;
            margin: 0;
            padding: 40px;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
        }

        h1, h2, h3, .brand {
            font-family: 'Orbitron', sans-serif;
            letter-spacing: 0.05em;
        }

        .header {
            text-align: center;
            margin-bottom: 60px;
        }

        .header h1 {
            font-size: 3rem;
            margin: 0;
            background: linear-gradient(to right, #fff, var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .header p {
            color: var(--accent);
            text-transform: uppercase;
            letter-spacing: 0.2em;
            font-size: 0.8rem;
            margin-top: 10px;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 24px;
            max-width: 1200px;
            width: 100%;
        }

        .card {
            background: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: 12px;
            padding: 32px;
            transition: transform 0.2s, box-shadow 0.2s;
            display: flex;
            flex-col: column;
            position: relative;
            overflow: hidden;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px -10px rgba(0, 243, 255, 0.15);
            border-color: var(--accent);
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0; height: 1px;
            background: linear-gradient(90deg, transparent, var(--accent), transparent);
            opacity: 0.5;
        }

        .card-tag {
            position: absolute;
            top: 20px;
            right: 20px;
            font-size: 0.7rem;
            text-transform: uppercase;
            letter-spacing: 0.1em;
            color: var(--accent);
            border: 1px solid var(--border);
            padding: 4px 8px;
            border-radius: 4px;
        }

        .card h2 {
            margin-top: 0;
            color: var(--accent);
            font-size: 1.5rem;
            margin-bottom: 16px;
        }

        .card p {
            color: var(--text-muted);
            line-height: 1.6;
            margin-bottom: 20px;
        }

        .list-group {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .list-group li {
            padding: 12px 0;
            border-bottom: 1px solid rgba(255,255,255,0.05);
            display: flex;
            align-items: start;
            gap: 10px;
        }

        .list-group li:last-child {
            border-bottom: none;
        }

        .list-group li::before {
            content: '>';
            color: var(--accent);
            font-family: monospace;
            font-weight: bold;
        }

        .highlight {
            color: #fff;
            font-weight: 600;
        }

        .phase-badge {
            display: inline-block;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: bold;
            background: rgba(255,255,255,0.1);
            margin-right: 8px;
        }
        
        .accent-box {
            background: var(--accent-dim);
            border-left: 3px solid var(--accent);
            padding: 15px;
            margin-top: auto;
            border-radius: 0 4px 4px 0;
            font-size: 0.9rem;
        }

    </style>
</head>
<body>

    <div class="header">
        <h1>ASPECT // PROGRESSION</h1>
        <p>Technical Blueprint v2.1 • Data & Logistics Pilot</p>
    </div>

    <div class="grid">

        <!-- Card 1: The Core Concept -->
        <div class="card">
            <span class="card-tag">Vision</span>
            <h2>The Vertical Slice</h2>
            <p>Instead of building a massive LMS, we are shipping a <strong>single, high-value pilot sector</strong>.</p>
            <ul class="list-group">
                <li><span class="highlight">Domain:</span> Logistics Numeracy L1</li>
                <li><span class="highlight">Goal:</span> Teach ops staff to sanity-check shipping manifests.</li>
                <li><span class="highlight">Format:</span> 3-Mission Micro-Loop.</li>
                <li><span class="highlight">UX:</span> Dual-Skin (Voyager vs. Professional).</li>
            </ul>
        </div>

        <!-- Card 2: The User Experience -->
        <div class="card">
            <span class="card-tag">UX Flow</span>
            <h2>The "First 5 Minutes"</h2>
            <p>We solve the "Empty Cockpit" problem by simulating a system calibration.</p>
            <ul class="list-group">
                <li><span class="highlight">Minute 0:</span> Calibration (System Setup). No empty dashboard.</li>
                <li><span class="highlight">Minute 1:</span> Mission 1 (Pattern Recognition). Pick the wrong row.</li>
                <li><span class="highlight">Minute 3:</span> Mission 2 (Math Verification). Prove the fix.</li>
                <li><span class="highlight">Minute 5:</span> Mission 3 (Report). Write the log entry.</li>
            </ul>
        </div>

        <!-- Card 3: The Architecture -->
        <div class="card">
            <span class="card-tag">Tech Stack</span>
            <h2>System Architecture</h2>
            <p>Four core components powering the progression universe.</p>
            <ul class="list-group">
                <li><span class="highlight">Engine:</span> Ruleset for XP, streaks, and difficulty curves.</li>
                <li><span class="highlight">Twin:</span> The persistent dashboard (Learner Cockpit).</li>
                <li><span class="highlight">Veil:</span> AI Guide using optimistic UI + background LLM.</li>
                <li><span class="highlight">Journal:</span> Reflection layer to capture emotional data.</li>
            </ul>
            <div class="accent-box">
                <strong>Sage Advice:</strong> Use "Optimistic UI" for Veil. Don't make users wait 3s for an AI response. Fake the immediate ack.
            </div>
        </div>

        <!-- Card 4: The Content Strategy -->
        <div class="card">
            <span class="card-tag">Content</span>
            <h2>The "Gold Standard"</h2>
            <p>We do not generate thousands of AI questions immediately. We hand-craft the perfect loop first.</p>
            <ul class="list-group">
                <li><span class="highlight">Manifest Schema:</span> Strictly typed JSON for shipping data.</li>
                <li><span class="highlight">World Bible:</span> Defined terminology (e.g., "Signal Corruption" vs "Error").</li>
                <li><span class="highlight">Scaling:</span> Once the Gold Standard works, we use it as a few-shot prompt for the AI to generate 50+ variants.</li>
            </ul>
        </div>

        <!-- Card 5: Roadmap -->
        <div class="card" style="grid-column: span 1;">
            <span class="card-tag">Execution</span>
            <h2>16-Week Roadmap</h2>
            <ul class="list-group">
                <li><span class="phase-badge">Wk 1-4</span> <strong>Skeleton:</strong> React App, Dual Skin, Hard-coded Mission 1.</li>
                <li><span class="phase-badge">Wk 5-8</span> <strong>Brain:</strong> Hook up Veil API, Grading Logic, Journal V1.</li>
                <li><span class="phase-badge">Wk 9-12</span> <strong>Map:</strong> Twin Dashboard V2, Risk/Streak Logic.</li>
                <li><span class="phase-badge">Wk 13-16</span> <strong>Scale:</strong> Mass-generate content variants.</li>
            </ul>
        </div>

        <!-- Card 6: Success Metrics -->
        <div class="card">
            <span class="card-tag">KPIs</span>
            <h2>Success Criteria</h2>
            <p>How we know the pilot is working.</p>
            <ul class="list-group">
                <li><span class="highlight">Time-to-Proficiency:</span> Do users spot errors faster after 5 loops?</li>
                <li><span class="highlight">Engagement:</span> Do users toggle themes or stick to one?</li>
                <li><span class="highlight">Journaling:</span> Are we getting honest "Mood" tags?</li>
            </ul>
        </div>

    </div>

</body>
</html>
