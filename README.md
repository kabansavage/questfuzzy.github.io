<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>🔍 Архив Сомнений | Детективный квест по нечёткой логике</title>
    <style>
        :root {
            --bg: #f5efe0;
            --card: #fffaf2;
            --accent: #8b5a2b;
            --success: #5c8a49;
            --error: #b3443c;
            --warn: #c47e3b;
            --text: #4a3320;
            --muted: #7a6a5a;
            --gold: #b68b40;
            --border: #d9c8b2;
            --shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
            --font-main: 'Georgia', 'Times New Roman', serif;
            --cafe: #8b5a2b;
            --park: #4a7c3f;
        }
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        body {
            background: #eaddcd;
            font-family: var(--font-main);
            color: var(--text);
            min-height: 100vh;
            padding: 20px;
            background-image: radial-gradient(circle at 20% 30%, #fff3e0 0%, #eaddcd 80%);
        }
        .wrap {
            max-width: 900px;
            margin: 0 auto;
        }
        header {
            text-align: center;
            margin-bottom: 25px;
            border-bottom: 2px solid var(--border);
            padding-bottom: 15px;
        }
        h1 {
            color: var(--accent);
            font-size: 2.2em;
            text-shadow: 1px 1px 0 rgba(255, 255, 255, 0.8);
            letter-spacing: 1px;
        }
        .subtitle {
            font-style: italic;
            color: var(--muted);
            margin-top: 5px;
        }
        .chapter {
            display: none;
            animation: fadeUp 0.5s ease;
        }
        .chapter.active {
            display: block;
        }
        @keyframes fadeUp {
            from {
                opacity: 0;
                transform: translateY(15px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        .ch-header {
            background: linear-gradient(135deg, #e7d7c1 0%, #f3e5d8 100%);
            padding: 18px 20px;
            border-radius: 8px;
            margin-bottom: 20px;
            border-left: 6px solid var(--accent);
            box-shadow: var(--shadow);
        }
        .ch-title {
            font-size: 1.4em;
            color: var(--accent);
            font-weight: bold;
        }
        .ch-story {
            font-style: italic;
            color: var(--muted);
            margin-top: 8px;
            font-size: 0.95em;
            line-height: 1.5;
        }
        .task {
            background: var(--card);
            border-radius: 8px;
            margin-bottom: 20px;
            border: 1px solid var(--border);
            overflow: hidden;
            box-shadow: var(--shadow);
        }
        .task.hidden {
            display: none;
        }
        .task-header {
            background: #f3ece2;
            padding: 14px 20px;
            border-bottom: 1px solid var(--border);
            font-weight: bold;
            color: var(--accent);
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.05em;
        }
        .task-body {
            padding: 20px;
        }
        .task-desc {
            margin-bottom: 15px;
            line-height: 1.6;
            color: var(--text);
        }
        .hint {
            background: rgba(196, 126, 59, 0.1);
            border-left: 4px solid var(--warn);
            padding: 10px 15px;
            border-radius: 4px;
            margin: 15px 0;
            font-size: 0.9em;
            color: #7a5a3a;
        }
        .input-group {
            margin: 12px 0;
        }
        label {
            display: block;
            margin-bottom: 5px;
            color: var(--accent);
            font-weight: bold;
            font-size: 0.9em;
        }
        input,
        select {
            width: 100%;
            padding: 10px 12px;
            background: #fffefb;
            border: 1px solid var(--border);
            color: var(--text);
            border-radius: 6px;
            font-size: 1em;
            font-family: var(--font-main);
        }
        input:focus,
        select:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 5px rgba(139, 90, 43, 0.2);
        }
        .slider-wrap {
            background: #fdf9f4;
            padding: 12px 15px;
            border-radius: 8px;
            margin: 12px 0;
            border: 1px solid var(--border);
        }
        .slider-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 5px;
        }
        .slider-val {
            background: var(--accent);
            color: white;
            padding: 4px 12px;
            border-radius: 20px;
            font-weight: bold;
            font-family: monospace;
            font-size: 0.95em;
        }
        input[type="range"] {
            width: 100%;
            height: 6px;
            -webkit-appearance: none;
            background: #ddd2c1;
            border-radius: 10px;
            cursor: pointer;
            margin: 8px 0;
        }
        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 22px;
            height: 22px;
            background: var(--accent);
            border-radius: 50%;
            cursor: pointer;
            box-shadow: 0 2px 8px rgba(139, 90, 43, 0.4);
            border: 2px solid white;
        }
        .btn {
            background: var(--accent);
            color: white;
            border: none;
            padding: 11px 22px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
            font-size: 0.95em;
            margin-top: 10px;
            transition: 0.2s;
            font-family: var(--font-main);
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        .btn:hover {
            background: #6b4226;
            transform: translateY(-1px);
        }
        .btn-next {
            background: var(--gold);
            color: #fff;
            width: 100%;
            margin-top: 25px;
            font-size: 1.1em;
            padding: 14px;
            display: none;
            border: 1px solid #9e7a3e;
        }
        .btn-next.show {
            display: block;
        }
        .btn-next:hover {
            background: #a07b36;
        }
        .feedback {
            padding: 12px;
            border-radius: 6px;
            margin-top: 12px;
            display: none;
            font-weight: bold;
        }
        .feedback.show {
            display: block;
            animation: slideIn 0.3s;
        }
        .feedback.ok {
            background: rgba(92, 138, 73, 0.1);
            border: 1px solid var(--success);
            color: #3a5e2f;
        }
        .feedback.err {
            background: rgba(179, 68, 60, 0.1);
            border: 1px solid var(--error);
            color: #8b2e28;
        }
        .feedback.info {
            background: rgba(139, 90, 43, 0.08);
            border: 1px solid var(--accent);
            color: var(--text);
        }
        .consequence-box {
            background: #fdf9f4;
            padding: 12px 15px;
            border-radius: 6px;
            margin-top: 12px;
            border-left: 4px solid var(--warn);
            font-size: 0.95em;
        }
        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(-10px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }
        .start-screen {
            background: linear-gradient(135deg, #e7d7c1 0%, #f3e5d8 100%);
            border-radius: 12px;
            padding: 30px;
            text-align: center;
            min-height: 45vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            border: 1px solid var(--border);
        }
        .start-box {
            background: rgba(255, 255, 255, 0.9);
            color: var(--text);
            padding: 30px;
            border-radius: 10px;
            max-width: 550px;
        }
        .ref-box {
            background: rgba(139, 90, 43, 0.05);
            border: 1px solid var(--border);
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 20px;
            font-size: 0.9em;
        }
        .ref-title {
            font-weight: bold;
            color: var(--accent);
            display: block;
            margin-bottom: 8px;
            font-size: 1em;
        }
        .ref-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
        }
        @media(max-width:600px) {
            .ref-grid {
                grid-template-columns: 1fr;
            }
        }
        .fuzzy-table {
            width: 100%;
            border-collapse: collapse;
            margin: 15px 0;
            font-size: 0.9em;
        }
        .fuzzy-table th {
            background: #f3ece2;
            padding: 10px;
            border: 1px solid var(--border);
            text-align: center;
            color: var(--accent);
        }
        .fuzzy-table td {
            padding: 10px;
            border: 1px solid var(--border);
            text-align: center;
        }
        .fuzzy-table .val-cell {
            font-family: monospace;
            font-size: 1.1em;
        }
        .in-set {
            background: rgba(139, 90, 43, 0.2);
            font-weight: bold;
            transition: 0.3s;
        }
        .not-in-set {
            background: transparent;
            color: var(--muted);
            transition: 0.3s;
        }
        .intersection-highlight {
            background: rgba(182, 139, 64, 0.35);
            font-weight: bold;
            border: 2px solid var(--gold);
        }
        .sliders-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin: 15px 0;
        }
        @media(max-width:600px) {
            .sliders-row {
                grid-template-columns: 1fr;
            }
        }
        .result-badge {
            display: inline-block;
            padding: 6px 14px;
            border-radius: 20px;
            font-weight: bold;
            font-size: 0.9em;
            margin: 5px;
        }
        .badge-yes {
            background: rgba(92, 138, 73, 0.2);
            color: #3a5e2f;
            border: 1px solid var(--success);
        }
        .badge-no {
            background: rgba(179, 68, 60, 0.1);
            color: #8b2e28;
            border: 1px solid var(--error);
        }
        .graph-box {
            background: #fdf9f4;
            border-radius: 8px;
            padding: 20px;
            margin: 15px 0;
            border: 1px solid var(--border);
            position: relative;
            height: 280px;
        }
        .graph-box canvas {
            width: 100%;
            height: 100%;
            display: block;
        }
        .min-visual {
            display: flex;
            align-items: center;
            gap: 12px;
            justify-content: center;
            margin: 10px 0;
            flex-wrap: wrap;
        }
        .min-block {
            text-align: center;
            padding: 10px 16px;
            border-radius: 8px;
            min-width: 80px;
        }
        .min-block-mu1 {
            background: rgba(139, 90, 43, 0.1);
            border: 2px solid var(--cafe);
        }
        .min-block-mu2 {
            background: rgba(74, 124, 63, 0.1);
            border: 2px solid var(--park);
        }
        .min-block-result {
            background: rgba(196, 126, 59, 0.15);
            border: 3px solid var(--warn);
        }
        .min-operator,
        .min-equals {
            font-size: 1.3em;
            font-weight: bold;
            color: var(--muted);
        }
        .big-number {
            font-size: 1.6em;
            font-weight: bold;
        }
        .legend-row {
            display: flex;
            gap: 15px;
            justify-content: center;
            margin-bottom: 10px;
            font-size: 0.8em;
            flex-wrap: wrap;
        }
        .legend-item {
            display: flex;
            align-items: center;
            gap: 5px;
        }
        .legend-line {
            width: 18px;
            height: 3px;
            border-radius: 2px;
        }
        .params-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }
        @media(max-width:650px) {
            .params-row {
                grid-template-columns: 1fr;
            }
            .min-visual {
                flex-direction: column;
            }
        }
        .witness-cards {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            margin: 15px 0;
        }
        .witness-card {
            border-radius: 8px;
            padding: 15px;
            text-align: center;
        }
        .card-expert {
            background: rgba(92, 138, 73, 0.08);
            border: 2px solid #5c8a49;
        }
        .card-normal {
            background: rgba(139, 90, 43, 0.08);
            border: 2px solid #8b5a2b;
        }
        .card-weak {
            background: rgba(179, 68, 60, 0.06);
            border: 2px solid #b3443c;
        }
        .witness-card h3 {
            margin-bottom: 5px;
        }
        .card-role {
            font-size: 0.8em;
            color: var(--muted);
            margin-bottom: 10px;
        }
        .data-table {
            width: 100%;
            border-collapse: collapse;
            margin: 15px 0;
            font-size: 0.95em;
        }
        .data-table th {
            background: #f3ece2;
            padding: 10px;
            border: 1px solid var(--border);
            text-align: center;
            color: var(--accent);
        }
        .data-table td {
            padding: 10px;
            border: 1px solid var(--border);
            text-align: center;
        }
        .data-table .val-cell {
            font-family: monospace;
            font-size: 1.1em;
            font-weight: bold;
        }
        .data-table .empty-cell {
            color: var(--muted);
            font-style: italic;
            font-weight: normal;
        }
        .data-table .new-row {
            background: rgba(196, 126, 59, 0.06);
        }
        .highlight-num {
            font-family: monospace;
            font-weight: bold;
            font-size: 1.1em;
        }
        @media(max-width:650px) {
            .witness-cards {
                grid-template-columns: 1fr;
            }
        }
        .progress-panel {
            background: var(--card);
            border: 2px solid var(--border);
            border-radius: 8px;
            padding: 15px 20px;
            margin-bottom: 20px;
            box-shadow: var(--shadow);
        }
        .progress-label {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
        }
        .progress-bar-outer {
            height: 24px;
            background: #e8ddd0;
            border-radius: 12px;
            overflow: hidden;
        }
        .progress-bar-inner {
            height: 100%;
            background: linear-gradient(90deg, #b3443c 0%, #c47e3b 40%, #b68b40 70%, #5c8a49 100%);
            border-radius: 12px;
            transition: width 0.6s ease;
        }
        .progress-stages {
            display: flex;
            justify-content: space-between;
            margin-top: 5px;
            font-size: 0.7em;
            color: var(--muted);
        }
        .info-row {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            gap: 15px;
            margin: 15px 0;
        }
        .info-card {
            border-radius: 8px;
            padding: 15px;
            text-align: center;
        }
        .card-day {
            background: rgba(139, 90, 43, 0.06);
            border: 2px solid #8b5a2b;
        }
        .card-place {
            background: rgba(74, 124, 63, 0.06);
            border: 2px solid #4a7c3f;
        }
        .card-time {
            background: rgba(196, 126, 59, 0.06);
            border: 2px solid var(--warn);
        }
        .info-card .info-value {
            font-size: 1.4em;
            font-weight: bold;
            margin-top: 5px;
        }
        .info-card .info-label {
            font-size: 0.8em;
            color: var(--muted);
        }
        .formula-box {
            background: #fdf9f4;
            border: 2px solid var(--accent);
            border-radius: 8px;
            padding: 20px;
            text-align: center;
            margin: 20px 0;
        }
        .formula {
            font-size: 1.3em;
            font-family: monospace;
            color: var(--accent);
        }
        .formula-result {
            font-size: 2em;
            font-weight: bold;
            color: var(--warn);
            margin-top: 8px;
        }
        .condition-cards {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            margin: 15px 0;
        }
        .condition-card {
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            border: 2px solid var(--border);
            background: #fdf9f4;
        }
        .condition-card .cond-icon {
            font-size: 2em;
            margin-bottom: 5px;
        }
        .condition-card .cond-mu {
            font-size: 1.6em;
            font-weight: bold;
            font-family: monospace;
        }
        .calc-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin: 20px 0;
        }
        .calc-block {
            background: #fdf9f4;
            border: 2px solid var(--border);
            border-radius: 8px;
            padding: 15px;
        }
        .calc-block h4 {
            text-align: center;
            color: var(--accent);
            margin-bottom: 12px;
        }
        .calc-answer {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .calc-answer label {
            white-space: nowrap;
            margin: 0;
        }
        .calc-answer input {
            flex: 1;
        }
        @media(max-width:650px) {
            .info-row,
            .condition-cards,
            .calc-row {
                grid-template-columns: 1fr;
            }
        }
        .place-cards {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
            margin: 15px 0;
        }
        .place-card {
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            border: 2px solid var(--border);
            transition: 0.3s;
        }
        .place-card.active {
            border-color: var(--success);
            background: rgba(92, 138, 73, 0.08);
        }
        .place-card.inactive {
            border-color: var(--error);
            background: rgba(179, 68, 60, 0.04);
            opacity: 0.6;
        }
        .place-card .place-mu {
            font-size: 1.4em;
            font-weight: bold;
            font-family: monospace;
        }
        .place-card .place-status {
            margin-top: 8px;
            font-weight: bold;
            font-size: 0.9em;
        }
        .timeline-events {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin: 15px 0;
        }
        .event-card {
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            cursor: pointer;
            transition: 0.2s;
            border: 2px solid var(--border);
        }
        .event-card:hover {
            border-color: var(--accent);
        }
        .event-card.selected {
            border-color: var(--accent);
            background: rgba(139, 90, 43, 0.06);
        }
        .event-card .event-icon {
            font-size: 2em;
            margin-bottom: 5px;
        }
        .final-cards {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            margin: 15px 0;
        }
        .final-card {
            border-radius: 8px;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            transition: 0.2s;
            border: 2px solid var(--border);
        }
        .final-card:hover {
            transform: translateY(-2px);
        }
        .final-card.selected {
            border-color: var(--accent);
            background: rgba(139, 90, 43, 0.06);
            box-shadow: 0 0 12px rgba(0, 0, 0, 0.1);
        }
        .final-card .fc-icon {
            font-size: 2.5em;
            margin-bottom: 8px;
        }
        .final-card h4 {
            margin-bottom: 8px;
            color: var(--accent);
        }
        .final-page {
            display: none;
            text-align: center;
            padding: 30px;
            background: var(--card);
            border-radius: 12px;
            border: 3px solid var(--accent);
            box-shadow: 0 0 30px rgba(139, 90, 43, 0.3);
            margin-top: 20px;
        }
        .final-page.show {
            display: block;
            animation: fadeUp 0.8s ease;
        }
        .final-page .fp-icon {
            font-size: 5em;
            margin-bottom: 15px;
        }
        .final-page h2 {
            color: var(--accent);
            font-size: 1.8em;
            margin-bottom: 10px;
        }
        .final-page .fp-code {
            font-size: 3em;
            font-weight: bold;
            color: var(--accent);
            letter-spacing: 12px;
            margin: 20px 0;
            font-family: monospace;
        }
        .final-page .fp-result {
            font-size: 1.1em;
            line-height: 1.7;
            margin: 20px 0;
            color: var(--text);
        }
        .final-page .fp-stats {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
            margin: 20px 0;
        }
        .fp-stat {
            background: #fdf9f4;
            border-radius: 8px;
            padding: 15px;
            border: 1px solid var(--border);
        }
        .fp-stat .stat-value {
            font-size: 1.5em;
            font-weight: bold;
            color: var(--accent);
        }
        .fp-stat .stat-label {
            font-size: 0.8em;
            color: var(--muted);
        }
        .fp-profile {
            background: #fdf9f4;
            border-radius: 8px;
            padding: 20px;
            border: 2px solid var(--accent);
            margin: 20px 0;
            text-align: center;
        }
        .fp-profile h3 {
            color: var(--accent);
            margin-bottom: 10px;
        }
        .fp-profile .profile-type {
            font-size: 1.3em;
            font-weight: bold;
            color: var(--warn);
        }
        @media(max-width:650px) {
            .summary-grid {
                grid-template-columns: 1fr 1fr;
            }
            .place-cards,
            .final-cards {
                grid-template-columns: 1fr;
            }
            .timeline-events {
                grid-template-columns: 1fr;
            }
            .fp-stats {
                grid-template-columns: 1fr 1fr;
            }
        }
        .summary-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 12px;
            margin: 15px 0;
        }
        .summary-card {
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            border: 2px solid var(--border);
            background: var(--card);
        }
        .summary-card .s-icon {
            font-size: 1.8em;
            margin-bottom: 5px;
        }
        .summary-card .s-value {
            font-size: 1.3em;
            font-weight: bold;
        }
        .summary-card .s-label {
            font-size: 0.75em;
            color: var(--muted);
        }
        .compromise-badge {
            display: inline-block;
            padding: 10px 20px;
            border-radius: 10px;
            font-weight: bold;
            font-size: 1.2em;
            margin: 8px 0;
            transition: 0.3s;
        }
        .badge-high {
            background: rgba(92, 138, 73, 0.2);
            border: 2px solid var(--success);
            color: #3a5e2f;
        }
        .badge-mid {
            background: rgba(196, 126, 59, 0.2);
            border: 2px solid var(--warn);
            color: #7a5a3a;
        }
        .badge-low {
            background: rgba(179, 68, 60, 0.15);
            border: 2px solid var(--error);
            color: #8b2e28;
        }
    </style>
</head>
<body>
    <div class="wrap">
        <header>
            <h1>🔍 Архив Сомнений</h1>
            <p class="subtitle">Интерактивный квест по нечёткой логике | 10 класс</p>
        </header>
        <div class="progress-panel">
            <div class="progress-label"><strong style="color:var(--accent);">🔍 Близость к цели:</strong><span id="progressText">Начало расследования</span></div>
            <div class="progress-bar-outer"><div class="progress-bar-inner" id="progressBar" style="width: 10%;"></div></div>
            <div class="progress-stages"><span>Начало</span><span>Зацепки</span><span>Поиск</span><span>След</span><span>Цель</span></div>
        </div>
        <div class="ref-box" id="refBox">
            <span class="ref-title">📋 СПРАВКА: Как работает нечёткая логика</span>
            <div class="ref-grid">
                <div><strong style="color:var(--accent);">1. Субъективность</strong><br>μ ∈ [0;1] — это не истина, а степень уверенности.<br>«Близко», «надёжно», «рискованно» зависят от контекста.</div>
                <div><strong style="color:var(--accent);">2. Порог уверенности</strong><br>Вы сами решаете, с какого значения μ считать утверждение «достаточно надёжным».<br>Порог влияет на результат — в этом суть нечёткой логики.</div>
            </div>
        </div>

        <!-- ВСТУПЛЕНИЕ -->
        <div class="chapter active" id="intro">
            <div class="start-screen"><div class="start-box"><h2 style="color:var(--accent); margin-bottom:15px;">📋 Дело №27030</h2><p style="margin-bottom:15px; line-height:1.6;">Вы — аналитик следственной группы. Пропал разработчик Даниил Савин. В его ноутбуке — размытые данные, противоречивые показания и субъективные оценки.</p><p style="margin-bottom:20px; color:var(--muted); font-style:italic;">Ваша задача: не просто «посчитать», а <strong>экспериментировать с неопределённостью</strong>, выбирать параметры, видеть последствия и принимать взвешенные решения.</p><button id="startBtn" class="btn" style="font-size:1.1em; padding:14px 30px;">🔎 Начать расследование</button></div></div>
        </div>

        <!-- ГЛАВА 1 -->
        <div class="chapter" id="ch1">
            <div class="ch-header"><div class="ch-title">📘 Глава 1: Субъективные шкалы</div><div class="ch-story">Переводим бытовые формулировки в измеримые степени уверенности. Нет «правильных» чисел — есть обоснованный порядок.</div></div>
            <div class="task" id="t1_1"><div class="task-header"><span>📊</span> Задание 1.1: Расположи по возрастанию надёжности</div><div class="task-body"><div class="task-desc">Расставьте характеристики свидетелей от <strong>наименее</strong> надёжного до <strong>наиболее</strong> надёжного.</div><div style="display:grid; grid-template-columns: repeat(5, 1fr); gap:8px; margin:15px 0;"><div><label style="text-align:center;">1-е (мин)</label><select id="o1"><option value="">—</option><option value="A">часто врёт</option><option value="B">иногда путает</option><option value="C">обычно честен</option><option value="D">эксперт</option><option value="E">почти всегда точен</option></select></div><div><label style="text-align:center;">2-е</label><select id="o2"><option value="">—</option><option value="A">часто врёт</option><option value="B">иногда путает</option><option value="C">обычно честен</option><option value="D">эксперт</option><option value="E">почти всегда точен</option></select></div><div><label style="text-align:center;">3-е</label><select id="o3"><option value="">—</option><option value="A">часто врёт</option><option value="B">иногда путает</option><option value="C">обычно честен</option><option value="D">эксперт</option><option value="E">почти всегда точен</option></select></div><div><label style="text-align:center;">4-е</label><select id="o4"><option value="">—</option><option value="A">часто врёт</option><option value="B">иногда путает</option><option value="C">обычно честен</option><option value="D">эксперт</option><option value="E">почти всегда точен</option></select></div><div><label style="text-align:center;">5-е (макс)</label><select id="o5"><option value="">—</option><option value="A">часто врёт</option><option value="B">иногда путает</option><option value="C">обычно честен</option><option value="D">эксперт</option><option value="E">почти всегда точен</option></select></div></div><div class="hint">💡 Подумайте: кто заслуживает наибольшего доверия — «обычно честен» или «почти всегда точен»? А эксперт — это надёжность или квалификация?</div><button class="btn check-btn" data-ch="1" data-t="1">✓ Проверить порядок</button><div class="feedback" id="f1_1"></div></div></div>
            <div class="task hidden" id="t1_2"><div class="task-header"><span>🎚️</span> Задание 1.2: Построй свою шкалу уверенности</div><div class="task-body"><div class="task-desc">Свидетель говорит: <em>«Даниил был в районе парка»</em>. Назначьте степень уверенности μ (от 0 до 1).</div><div class="slider-wrap"><div class="slider-header"><span>🎯 Уверенность (μ):</span><span class="slider-val" id="s1_2_val">0.50</span></div><input type="range" id="s1_2" min="0" max="1" step="0.05" value="0.5"><div style="display:flex; justify-content:space-between; margin-top:6px; font-size:0.8em; color:var(--muted);"><span>0.0 — точно нет</span><span>0.5 — не знаю</span><span>1.0 — точно да</span></div></div><div class="hint">💡 Значение 0.5 — полная неопределённость. Выберите значение, отражающее вашу готовность <strong>начать действовать</strong>.</div><button class="btn check-btn" data-ch="1" data-t="2">✓ Подтвердить выбор</button><div class="feedback" id="f1_2"></div></div></div>
            <div class="task hidden" id="t1_3"><div class="task-header"><span>🔍</span> Задание 1.3: Нечёткое пересечение показаний</div><div class="task-body"><div class="task-desc">У двух источников — <strong>Календаря</strong> и <strong>Активности</strong> — есть степени уверенности μ для каждого дня недели. Двигая пороги, добейтесь, чтобы <strong>ровно один день</strong> попал в пересечение.</div><table class="fuzzy-table"><thead><tr><th>День</th><th>Пн</th><th>Вт</th><th>Ср</th><th>Чт</th><th>Пт</th></tr></thead><tbody><tr><td><strong>Календарь (μ₁)</strong></td><td class="val-cell">0.4</td><td class="val-cell">0.5</td><td class="val-cell">0.9</td><td class="val-cell">0.3</td><td class="val-cell">0.6</td></tr><tr><td><strong>Активность (μ₂)</strong></td><td class="val-cell">0.6</td><td class="val-cell">0.3</td><td class="val-cell">0.8</td><td class="val-cell">0.5</td><td class="val-cell">0.2</td></tr></tbody></table>
            <div class="sliders-row">
                <div class="slider-wrap"><div class="slider-header"><span>📅 Порог для Календаря:</span><span class="slider-val" id="thresh1_val">0.20</span></div><input type="range" id="thresh1" min="0" max="1" step="0.05" value="0.2"><div style="font-size:0.8em; color:var(--muted); margin-top:4px;">Дни с μ₁ ≥ порог: <span id="days1_list" style="font-weight:bold; color:var(--accent);">Пн, Вт, Ср, Чт, Пт</span></div></div>
                <div class="slider-wrap"><div class="slider-header"><span>📱 Порог для Активности:</span><span class="slider-val" id="thresh2_val">0.20</span></div><input type="range" id="thresh2" min="0" max="1" step="0.05" value="0.2"><div style="font-size:0.8em; color:var(--muted); margin-top:4px;">Дни с μ₂ ≥ порог: <span id="days2_list" style="font-weight:bold; color:var(--accent);">Пн, Вт, Ср, Чт, Пт</span></div></div>
            </div>
            <div class="consequence-box" style="text-align:center;"><strong>🔎 Пересечение:</strong><br><div id="intersection_result" style="margin-top:8px; font-size:1.1em;"><span class="result-badge badge-yes">Пн</span><span class="result-badge badge-yes">Вт</span><span class="result-badge badge-yes">Ср</span><span class="result-badge badge-yes">Чт</span><span class="result-badge badge-yes">Пт</span></div><div id="intersection_count" style="margin-top:5px; color:var(--muted); font-size:0.9em;">Дней в пересечении: <strong>5</strong> — Слишком много, повысьте пороги</div></div>
            <div class="hint">💡 Если порог низкий — много шума. Если высокий — можно потерять данные. Найдите баланс, чтобы остался ровно один день.</div>
            <div class="input-group"><label>Какой день остался единственным?</label><select id="v1_3"><option value="">— Выберите —</option><option value="Пн">Понедельник</option><option value="Вт">Вторник</option><option value="Ср">Среда</option><option value="Чт">Четверг</option><option value="Пт">Пятница</option></select></div><button class="btn check-btn" data-ch="1" data-t="3">✓ Проверить</button><div class="feedback" id="f1_3"></div></div></div>
            <button class="btn btn-next" id="next1">→ Перейти к главе 2</button>
        </div>

        <!-- ГЛАВА 2 -->
        <div class="chapter" id="ch2">
            <div class="ch-header"><div class="ch-title">📘 Глава 2: Функции принадлежности</div><div class="ch-story">«Близко» и «далеко» — это не точки на карте, а плавные переходы. Строим функции, которые превращают слова в числа.</div></div>
            <div class="task" id="t2_1"><div class="task-header"><span>📐</span> Задание 2.1: Построй функцию «близко»</div><div class="task-body"><div class="task-desc">Свидетель: <em>«Я видел Даниила недалеко от кафе»</em>. Кафе в <strong>400 метрах</strong>. Постройте треугольную функцию. <strong>Условие:</strong> μ(400м) ≥ 0.6, и a < 400 < c.</div><div class="slider-wrap"><div class="slider-header"><span>a — начало (м):</span><span class="slider-val" id="v2_1a_val">100</span></div><input type="range" id="v2_1a" min="0" max="390" step="10" value="100"></div><div class="slider-wrap"><div class="slider-header"><span>b — пик (м):</span><span class="slider-val" id="v2_1b_val">200</span></div><input type="range" id="v2_1b" min="10" max="700" step="10" value="200"></div><div class="slider-wrap"><div class="slider-header"><span>c — конец (м):</span><span class="slider-val" id="v2_1c_val">600</span></div><input type="range" id="v2_1c" min="410" max="1000" step="10" value="600"></div><div class="graph-box"><canvas id="canvas2_1"></canvas></div><div class="consequence-box">📐 <strong>μ(400м) = <span id="mu2_1_display" style="color:var(--accent); font-size:1.2em;">0.67</span></strong></div><button class="btn check-btn" data-ch="2" data-t="1">✓ Проверить функцию</button><div class="feedback" id="f2_1"></div></div></div>
            <div class="task hidden" id="t2_2"><div class="task-header"><span>🔗</span> Задание 2.2: Оператор min — слабое звено</div><div class="task-body"><div class="task-desc">Чтобы выехать, нужно два условия одновременно: Савин в районе <strong>И</strong> есть транспорт. <strong>μ_итог = min(μ_район, μ_транспорт)</strong>.</div><div style="display:grid;grid-template-columns:1fr 1fr;gap:15px;"><div class="slider-wrap"><div class="slider-header"><span>🏙️ μ_район:</span><span class="slider-val" id="muA_val">0.70</span></div><input type="range" id="muA" min="0" max="1" step="0.05" value="0.7"></div><div class="slider-wrap"><div class="slider-header"><span>🚕 μ_транспорт:</span><span class="slider-val" id="muB_val">0.50</span></div><input type="range" id="muB" min="0" max="1" step="0.05" value="0.5"></div></div><div class="min-visual"><div class="min-block min-block-mu1"><div style="font-size:0.8em;color:var(--muted);">μ_район</div><div class="big-number" id="vis_muA" style="color:var(--cafe);">0.70</div></div><div class="min-operator">∩</div><div class="min-block min-block-mu2"><div style="font-size:0.8em;color:var(--muted);">μ_транспорт</div><div class="big-number" id="vis_muB" style="color:var(--park);">0.50</div></div><div class="min-equals">=</div><div class="min-block min-block-result"><div style="font-size:0.8em;color:var(--muted);">μ_итог</div><div class="big-number" id="vis_result" style="color:var(--warn);">0.50</div></div></div><div class="consequence-box"><span id="min_comment" style="font-size:0.9em;">Итог = меньшее из двух. Слабое звено решает всё.</span></div><div class="input-group"><label>Если μ_район = 0.7, а μ_транспорт = 0.4, то μ_итог = ?</label><select id="v2_2"><option value="">—</option><option value="0.7">0.7</option><option value="0.4">0.4</option><option value="0.55">0.55</option></select></div><button class="btn check-btn" data-ch="2" data-t="2">✓ Проверить</button><div class="feedback" id="f2_2"></div></div></div>
            <div class="task hidden" id="t2_3"><div class="task-header"><span>🤝</span> Задание 2.3: Найди точку согласия</div><div class="task-body"><div class="task-desc">Два свидетеля спорят. Один говорит: <em>«Савин был недалеко от кафе»</em> (кафе на <strong>300 м</strong>). Второй: <em>«Нет, ближе к парку»</em> (парк на <strong>500 м</strong>).</div><div class="task-desc">У каждого — <strong>своё понимание</strong> слова «недалеко». Для кафе функция: a=100, b=300, c=500. Для парка: a=300, b=500, c=700. Эти функции показаны на графике.</div><div class="task-desc">Двигайте точку X и следите за значением <strong>min</strong>. Это — <strong>совместная уверенность</strong>: насколько оба свидетеля согласны, что Савин был именно там. Найдите X, где min <strong>максимален</strong>.</div><div class="legend-row"><div class="legend-item"><span class="legend-line" style="background:var(--cafe);"></span> μ_кафе</div><div class="legend-item"><span class="legend-line" style="background:var(--park);"></span> μ_парк</div><div class="legend-item"><span style="border-top:3px dashed var(--warn); width:18px; display:inline-block;"></span> min — совместная уверенность</div></div><div class="slider-wrap"><div class="slider-header"><span>📍 Точка X (м):</span><span class="slider-val" id="x_val">50</span></div><input type="range" id="xPos" min="50" max="750" step="5" value="50"></div><div class="graph-box"><canvas id="canvas2_3"></canvas></div><div style="text-align:center; margin:15px 0;"><div style="font-size:0.9em; color:var(--muted); margin-bottom:5px;">Совместная уверенность в точке X:</div><div class="compromise-badge badge-mid" id="minBadge">min = 0.00</div></div><div class="hint">💡 Двигайте X и смотрите на жёлтую точку. Где она выше всего? Там, где две функции пересекаются — в этой точке оба свидетеля имеют одинаковую уверенность, и она максимальна.</div><div class="input-group"><label>Максимальное значение совместной уверенности min (округлите до сотых):</label><input type="number" id="v2_3" step="0.01" placeholder="0.00"></div><button class="btn check-btn" data-ch="2" data-t="3">✓ Проверить</button><div class="feedback" id="f2_3"></div></div></div>
            <button class="btn btn-next" id="next2">→ Перейти к главе 3</button>
        </div>

        <!-- ГЛАВА 3 -->
        <div class="chapter" id="ch3">
            <div class="ch-header"><div class="ch-title">📘 Глава 3: Взвешенные голоса</div><div class="ch-story">Три свидетеля. Разная надёжность. Как найти время, когда их показания максимально согласованы?</div></div>
            <div class="task" id="t3_1"><div class="task-header"><span>⚖️</span> Задание 3.1: Назначь веса свидетелям</div><div class="task-body"><div class="task-desc">Назначьте веса трём свидетелям так, чтобы сумма была равна 1.0, а порядок соответствовал надёжности.</div><div class="witness-cards"><div class="witness-card card-expert"><h3 style="color:#5c8a49;">👨‍💼 Свидетель А</h3><div class="card-role">Эксперт по безопасности</div><div style="font-size:0.85em;">Знает Савина лично. Говорит: <em>«Около 21:00»</em>.</div></div><div class="witness-card card-normal"><h3 style="color:#8b5a2b;">🙋 Свидетель Б</h3><div class="card-role">Обычный прохожий</div><div style="font-size:0.85em;">Видел похожего человека. Говорит: <em>«Где-то в 20:30»</em>.</div></div><div class="witness-card card-weak"><h3 style="color:#b3443c;">🤷 Свидетель В</h3><div class="card-role">Рассеянный сосед</div><div style="font-size:0.85em;">Часто путает время. Говорит: <em>«Вроде около 20:45»</em>.</div></div></div><div style="display:grid; grid-template-columns: repeat(3, 1fr); gap: 12px; margin: 15px 0;"><div class="input-group"><label>w₁ — Эксперт (А):</label><input type="number" id="w1" step="0.05" min="0" max="1" placeholder="0.00"></div><div class="input-group"><label>w₂ — Прохожий (Б):</label><input type="number" id="w2" step="0.05" min="0" max="1" placeholder="0.00"></div><div class="input-group"><label>w₃ — Сосед (В):</label><input type="number" id="w3" step="0.05" min="0" max="1" placeholder="0.00"></div></div><div class="consequence-box">Σ весов = <strong id="sum3_1" style="font-size:1.2em;">—</strong></div><button class="btn check-btn" data-ch="3" data-t="1">✓ Проверить веса</button><div class="feedback" id="f3_1"></div></div></div>
            <div class="task hidden" id="t3_2"><div class="task-header"><span>🕐</span> Задание 3.2: Найди время максимального согласия</div><div class="task-body"><div class="task-desc">Двигайте ползунок времени и найдите момент, где <strong>взвешенная сумма Σ(wᵢ × μᵢ) максимальна</strong>.</div><div class="legend-row"><div class="legend-item"><span class="legend-line" style="background:#5c8a49;"></span> А (пик 21:00)</div><div class="legend-item"><span class="legend-line" style="background:#8b5a2b;"></span> Б (пик 20:30)</div><div class="legend-item"><span class="legend-line" style="background:#b3443c;"></span> В (пик 20:45)</div><div class="legend-item"><span class="legend-line" style="background:#c47e3b; height:3px;"></span> Σ(w×μ)</div></div><div class="slider-wrap"><div class="slider-header"><span>🕐 Время:</span><span class="slider-val" id="time_val">20:45</span></div><input type="range" id="timeSlider" min="0" max="24" step="1" value="9"><div style="display:flex; justify-content:space-between; font-size:0.8em; color:var(--muted);"><span>20:00</span><span>20:30</span><span>21:00</span><span>21:30</span><span>22:00</span></div></div><div class="graph-box"><canvas id="canvas3_2"></canvas></div><div class="consequence-box">📊 <strong>Взвешенная сумма = <span id="res3_2" style="color:var(--accent); font-size:1.2em;">—</span></strong></div><div class="input-group"><label>В какое время Σ(w×μ) максимальна? (ЧЧ:ММ)</label><input type="text" id="v3_2" placeholder="Например: 20:45"></div><button class="btn check-btn" data-ch="3" data-t="2">✓ Проверить время</button><div class="feedback" id="f3_2"></div></div></div>
            <div class="task hidden" id="t3_3"><div class="task-header"><span>🧮</span> Задание 3.3: Рассчитай итоговую уверенность</div><div class="task-body"><div class="task-desc">Ползунок зафиксирован на оптимальном времени. Даны веса и μ. <strong>Вычислите</strong> μ_итог = w₁×μ₁ + w₂×μ₂ + w₃×μ₃.</div><table class="data-table"><thead><tr><th>Свидетель</th><th>Вес (w)</th><th>μ в оптимальной точке</th><th>w × μ</th></tr></thead><tbody><tr><td style="color:#5c8a49;">👨‍💼 Эксперт А</td><td class="val-cell" id="d_w1">—</td><td class="val-cell" id="d_mu1">—</td><td class="empty-cell" id="d_wm1">?</td></tr><tr><td style="color:#8b5a2b;">🙋 Прохожий Б</td><td class="val-cell" id="d_w2">—</td><td class="val-cell" id="d_mu2">—</td><td class="empty-cell" id="d_wm2">?</td></tr><tr><td style="color:#b3443c;">🤷 Сосед В</td><td class="val-cell" id="d_w3">—</td><td class="val-cell" id="d_mu3">—</td><td class="empty-cell" id="d_wm3">?</td></tr></tbody></table><div class="consequence-box"><strong>μ_итог = w₁×μ₁ + w₂×μ₂ + w₃×μ₃ = ?</strong></div><div class="input-group"><label>Впишите μ_итог (округлите до сотых):</label><input type="number" id="v3_3" step="0.01" placeholder="0.00"></div><button class="btn check-btn" data-ch="3" data-t="3">✓ Проверить расчёт</button><div class="feedback" id="f3_3"></div></div></div>
            <button class="btn btn-next" id="next3">→ Перейти к главе 4</button>
        </div>

        <!-- ГЛАВА 4 -->
        <div class="chapter" id="ch4">
            <div class="ch-header"><div class="ch-title">📘 Глава 4: Решение на основе данных</div><div class="ch-story">Все предыдущие главы дали нам числа. Теперь нужно применить их.</div></div>
            <div class="info-row"><div class="info-card card-day"><div class="info-label">📅 День</div><div class="info-value" style="color:#8b5a2b;">Среда</div></div><div class="info-card card-place"><div class="info-label">📍 Место</div><div class="info-value" style="color:#4a7c3f;">Кафе — Парк</div></div><div class="info-card card-time"><div class="info-label">🕐 Время</div><div class="info-value" style="color:var(--warn);">21:00</div></div></div>
            <div class="task" id="t4_1"><div class="task-header"><span>🔗</span> Задание 4.1: Уверенность всей операции</div><div class="task-body"><div class="task-desc">Три условия одновременно. Для «И» — оператор <strong>min</strong>.</div><div class="condition-cards"><div class="condition-card"><div class="cond-icon">📍</div><strong>Место верное</strong><div class="cond-mu" style="color:#4a7c3f;">0.61</div></div><div class="condition-card"><div class="cond-icon">🕐</div><strong>Время верное</strong><div class="cond-mu" style="color:#c47e3b;">0.61</div></div><div class="condition-card"><div class="cond-icon">🚗</div><strong>Транспорт доступен</strong><div class="cond-mu" style="color:#8b5a2b;">0.85</div></div></div><div class="formula-box"><div class="formula">μ_операции = min(μ_место, μ_время, μ_транспорт)</div><div class="formula-result">= ?</div></div><div class="input-group"><label>Рассчитайте μ_операции (округлите до сотых):</label><input type="number" id="v4_1" step="0.01" placeholder="0.00"></div><button class="btn check-btn" data-ch="4" data-t="1">✓ Проверить</button><div class="feedback" id="f4_1"></div></div></div>
            <div class="task hidden" id="t4_2"><div class="task-header"><span>🆕</span> Задание 4.2: Новые данные</div><div class="task-body"><div class="task-desc">Новый свидетель — охранник. Видел Савина в <strong>21:15 у офиса</strong>. Вес: <strong>0.25</strong>. Старые веса умножены на 0.75. Рассчитайте взвешенную сумму для двух вариантов времени.</div><table class="data-table"><thead><tr><th>Свидетель</th><th>Вес (w)</th><th>μ в 21:00</th><th>μ в 21:15</th></tr></thead><tbody><tr><td style="color:#5c8a49;">👨‍💼 Эксперт А</td><td class="highlight-num">0.375</td><td class="highlight-num">1.00</td><td class="highlight-num">0.50</td></tr><tr><td style="color:#8b5a2b;">🙋 Прохожий Б</td><td class="highlight-num">0.225</td><td class="highlight-num">0.00</td><td class="highlight-num">0.00</td></tr><tr><td style="color:#b3443c;">🤷 Сосед В</td><td class="highlight-num">0.150</td><td class="highlight-num">0.57</td><td class="highlight-num">0.14</td></tr><tr class="new-row"><td style="color:#c47e3b;">🆕 Охранник</td><td class="highlight-num">0.250</td><td class="highlight-num">0.17</td><td class="highlight-num">1.00</td></tr></tbody></table><div class="calc-row"><div class="calc-block"><h4>Для 21:00</h4><div class="calc-answer"><label>Σ =</label><input type="number" id="v4_2_2100" step="0.001" placeholder="0.000"></div></div><div class="calc-block"><h4>Для 21:15</h4><div class="calc-answer"><label>Σ =</label><input type="number" id="v4_2_2115" step="0.001" placeholder="0.000"></div></div></div><button class="btn check-btn" data-ch="4" data-t="2">✓ Проверить</button><div class="feedback" id="f4_2"></div></div></div>
            <div class="task hidden" id="t4_3"><div class="task-header"><span>🎯</span> Задание 4.3: Баланс точности и уверенности</div><div class="task-body"><div class="task-desc">Зона поиска — нечёткая функция. Найдите минимальный радиус, при котором <strong>μ в центре ≥ 0.6</strong>.</div><div class="slider-wrap"><div class="slider-header"><span>🔍 Радиус зоны (м):</span><span class="slider-val" id="radius_val">300</span></div><input type="range" id="radiusSlider" min="100" max="600" step="25" value="300"></div><div class="graph-box"><canvas id="canvas4_3"></canvas></div><div style="display:grid; grid-template-columns: 1fr 1fr; gap: 15px; margin: 15px 0;"><div class="consequence-box">🎯 <strong>μ в центре:</strong> <span id="muCenter" style="font-size:1.2em; color:var(--accent);">1.00</span></div><div class="consequence-box">📐 <strong>Площадь (усл. ед.):</strong> <span id="zoneArea" style="font-size:1.2em; color:var(--accent);">—</span></div></div><div class="input-group"><label>При каком минимальном радиусе μ в центре = 0.6?</label><input type="number" id="v4_3" step="25" min="100" max="600" placeholder="Введите значение"></div><button class="btn check-btn" data-ch="4" data-t="3">✓ Проверить</button><div class="feedback" id="f4_3"></div></div></div>
            <button class="btn btn-next" id="next4">→ Перейти к главе 5</button>
        </div>

        <!-- ГЛАВА 5 -->
        <div class="chapter" id="ch5">
            <div class="ch-header"><div class="ch-title">📘 Глава 5: Точка на карте</div><div class="ch-story">Все данные собраны. Осталось отсечь лишние версии, учесть последнюю улику и принять окончательное решение.</div></div>
            <div class="summary-grid"><div class="summary-card"><div class="s-icon">📅</div><div class="s-value" style="color:#8b5a2b;">Среда</div><div class="s-label">День</div></div><div class="summary-card"><div class="s-icon">🕐</div><div class="s-value" style="color:var(--warn);">21:00</div><div class="s-label">Время</div></div><div class="summary-card"><div class="s-icon">📍</div><div class="s-value" style="color:#4a7c3f;">360 м</div><div class="s-label">Радиус зоны</div></div><div class="summary-card"><div class="s-icon">📊</div><div class="s-value" style="color:var(--accent);">0.61</div><div class="s-label">Уверенность</div></div></div>
            <div class="task" id="t5_1"><div class="task-header"><span>🗺️</span> Задание 5.1: Отсечение версий</div><div class="task-body"><div class="task-desc">Три возможных места. Двигайте порог — точки с μ ниже порога отсеиваются. Найдите порог, где останется ровно одна точка.</div><div class="place-cards" id="placeCards"><div class="place-card active" data-place="cafe"><strong>☕ Кафе</strong><div class="place-mu" style="color:#4a7c3f;">0.61</div><div style="font-size:0.8em; color:var(--muted);">Основная версия</div><div class="place-status" style="color:var(--success);">✓ Выезжаем</div></div><div class="place-card active" data-place="office"><strong>🏢 Офис</strong><div class="place-mu" style="color:#c47e3b;">0.45</div><div style="font-size:0.8em; color:var(--muted);">Охранник видел</div><div class="place-status" style="color:var(--success);">✓ Выезжаем</div></div><div class="place-card active" data-place="metro"><strong>🚇 Метро</strong><div class="place-mu" style="color:#b3443c;">0.30</div><div style="font-size:0.8em; color:var(--muted);">Сомнительный свидетель</div><div class="place-status" style="color:var(--success);">✓ Выезжаем</div></div></div><div class="slider-wrap"><div class="slider-header"><span>🔧 Порог:</span><span class="slider-val" id="thresh_val">0.20</span></div><input type="range" id="threshSlider" min="0.2" max="0.7" step="0.05" value="0.2"></div><div class="task-desc">Какая точка осталась единственной?</div><div class="input-group"><label>Оставшаяся точка:</label><select id="v5_1"><option value="">— Выберите —</option><option value="cafe">Кафе</option><option value="office">Офис</option><option value="metro">Метро</option></select></div><button class="btn check-btn" data-ch="5" data-t="1">✓ Проверить</button><div class="feedback" id="f5_1"></div></div></div>
            <div class="task hidden" id="t5_2"><div class="task-header"><span>📱</span> Задание 5.2: Неожиданная улика</div><div class="task-body"><div class="task-desc">В 20:40 зафиксирован короткий звонок с телефона Савина. Вышка — рядом с офисом. Как интерпретировать?</div><div class="timeline-events"><div class="event-card" data-event="confirm"><div class="event-icon">🔗</div><strong>Подтверждает версию офиса</strong><p style="font-size:0.85em; color:var(--muted);">μ офиса → 0.55.</p></div><div class="event-card" data-event="ignore"><div class="event-icon">❓</div><strong>Случайность</strong><p style="font-size:0.85em; color:var(--muted);">Ничего не доказывает.</p></div></div><div class="input-group"><label>Ваша интерпретация:</label><select id="v5_2"><option value="">— Выберите —</option><option value="confirm">Подтверждает версию офиса</option><option value="ignore">Случайность</option></select></div><button class="btn check-btn" data-ch="5" data-t="2">✓ Подтвердить</button><div class="feedback" id="f5_2"></div></div></div>
            <div class="task hidden" id="t5_3"><div class="task-header"><span>🚗</span> Задание 5.3: Окончательное решение</div><div class="task-body"><div class="task-desc">Группа ждёт приказа. Ваш выбор определит исход расследования.</div><div class="final-cards"><div class="final-card" data-final="cafe"><div class="fc-icon">☕</div><h4>К кафе</h4><p style="font-size:0.85em; color:var(--muted);">Основная версия. μ = 0.61.</p></div><div class="final-card" data-final="office"><div class="fc-icon">🏢</div><h4>К офису</h4><p style="font-size:0.85em; color:var(--muted);">Версия охранника.</p></div><div class="final-card" data-final="center"><div class="fc-icon">📍</div><h4>Центр зоны</h4><p style="font-size:0.85em; color:var(--muted);">Компромисс. μ = 0.5.</p></div></div><div class="input-group"><label>Ваш выбор:</label><select id="v5_3"><option value="">— Выберите —</option><option value="cafe">Кафе</option><option value="office">Офис</option><option value="center">Центр зоны</option></select></div><button class="btn btn-final" id="btnFinish">🔓 Завершить расследование</button><div class="feedback" id="f5_3"></div></div></div>
        </div>

        <!-- Финальная страница -->
        <div class="final-page" id="finalPage">
            <div class="fp-icon" id="fpIcon">🔍</div>
            <h2 id="fpTitle">Расследование завершено</h2>
            <div class="fp-code">Дело №27030</div>
            <div class="fp-result" id="fpResult"></div>
            <div class="fp-stats">
                <div class="fp-stat"><div class="stat-value" id="fpDecision">—</div><div class="stat-label">Куда выехали</div></div>
                <div class="fp-stat"><div class="stat-value" id="fpProgress">70%</div><div class="stat-label">Эффективность</div></div>
                <div class="fp-stat"><div class="stat-value" id="fpTime">—</div><div class="stat-label">Время прохождения</div></div>
                <div class="fp-stat"><div class="stat-value" id="fpErrors">—</div><div class="stat-label">Ошибок в заданиях</div></div>
            </div>
            <div class="fp-profile" id="fpProfile"><h3>🎯 Ваш стиль расследования</h3><p class="profile-type" id="fpProfileType"></p><p style="font-size:0.9em; color:var(--muted);" id="fpProfileDesc"></p></div>
            <p style="color: var(--muted); font-size: 0.9em; margin-top: 15px;">Архив пополнен. Спасибо за работу, аналитик.</p>
        </div>
    </div>

    <script>
        (function() {
            const state = { tasks: {} };
            let progressScore = 10;
            let decisionLog = [];
            let totalErrors = 0;
            const startTime = Date.now();
            const val = id => parseFloat(document.getElementById(id).value) || 0;
            const txt = id => { const el = document.getElementById(id); return el ? el.value.trim().toUpperCase() : ''; };
            function fb(id, msg, type) { const el = document.getElementById(id); if (!el) return; el.textContent = msg; el.className = `feedback show ${type || 'info'}`; }
            function updateProgress(inc) { progressScore = Math.min(100, Math.max(0, progressScore + inc)); document.getElementById('progressBar').style.width = progressScore + '%'; let t; if (progressScore < 25) t = 'Начало расследования'; else if (progressScore < 45) t = 'Есть зацепки'; else if (progressScore < 65) t = 'Активный поиск'; else if (progressScore < 85) t = 'Горячий след'; else t = 'Цель близко!'; document.getElementById('progressText').textContent = t; }
            function logDecision(choice) { decisionLog.push(choice); }
            function incErrors() { totalErrors++; }
            function goToChapter(chNum) { document.querySelectorAll('.chapter').forEach(c => c.classList.remove('active')); const target = document.getElementById(chNum === 0 ? 'intro' : `ch${chNum}`); if (target) { target.classList.add('active'); target.scrollIntoView({ behavior: 'smooth' }); } if (chNum >= 4) document.getElementById('refBox').style.display = 'none'; }
            function showFinalPage(finalChoice) { document.querySelectorAll('.chapter').forEach(c => c.classList.remove('active')); document.getElementById('refBox').style.display = 'none'; document.querySelector('.progress-panel').style.display = 'none'; const fp = document.getElementById('finalPage'); fp.classList.add('show'); fp.scrollIntoView({ behavior: 'smooth' }); const placeNames = { cafe: 'Кафе', office: 'Офис', center: 'Центр зоны' }; document.getElementById('fpDecision').textContent = placeNames[finalChoice] || '—'; document.getElementById('fpProgress').textContent = progressScore + '%'; const elapsed = Math.floor((Date.now() - startTime) / 1000); const mins = Math.floor(elapsed / 60); const secs = elapsed % 60; document.getElementById('fpTime').textContent = mins + ' мин ' + secs + ' сек'; document.getElementById('fpErrors').textContent = totalErrors; let resultText = ''; if (finalChoice === 'cafe') { if (progressScore >= 75) { document.getElementById('fpIcon').textContent = '✅'; document.getElementById('fpTitle').textContent = 'Дело раскрыто!'; document.getElementById('fpTitle').style.color = 'var(--success)'; resultText = 'Группа выехала к кафе. <strong>Савин найден.</strong> Он был там в среду около 21:00. Разработчик тестировал новое приложение и отключил телефон. Ваш систематический анализ привёл группу точно к цели.'; } else { document.getElementById('fpIcon').textContent = '⚠️'; document.getElementById('fpTitle').textContent = 'Частичный успех'; document.getElementById('fpTitle').style.color = 'var(--warn)'; resultText = 'Группа выехала к кафе, но с опозданием. Савина нашли через день — он ушёл дальше в парк. Он в порядке, но расследование затянулось.'; } } else if (finalChoice === 'office') { document.getElementById('fpIcon').textContent = '⚠️'; document.getElementById('fpTitle').textContent = 'Ложный след'; document.getElementById('fpTitle').style.color = 'var(--warn)'; resultText = 'Группа выехала к офису. Савина там не оказалось. Пока проверяли офис, он ушёл из района кафе. Его нашли позже — он жив, но следствие пошло по ложному пути.'; } else if (finalChoice === 'center') { if (progressScore >= 60) { document.getElementById('fpIcon').textContent = '✅'; document.getElementById('fpTitle').textContent = 'Дело раскрыто!'; document.getElementById('fpTitle').style.color = 'var(--success)'; resultText = 'Группа выехала в центр зоны. <strong>Савин найден неподалёку.</strong> Он действительно был в этом районе. Ваша осторожность оправдалась.'; } else { document.getElementById('fpIcon').textContent = '⚠️'; document.getElementById('fpTitle').textContent = 'Частичный успех'; document.getElementById('fpTitle').style.color = 'var(--warn)'; resultText = 'Группа выехала в центр зоны, но из-за долгих колебаний Савин успел уйти дальше. Его нашли через два дня.'; } } document.getElementById('fpResult').innerHTML = resultText; let profileType, profileDesc; const decisive = decisionLog.filter(d => ['cafe', 'confirm'].includes(d)).length; const cautious = decisionLog.filter(d => ['ignore', 'center'].includes(d)).length; if (decisive > cautious + 1) { profileType = 'Решительный аналитик'; profileDesc = 'Вы предпочитаете действовать быстро, доверяя основной версии. Это экономит время, но повышает риск ошибки.'; } else if (cautious > decisive + 1) { profileType = 'Осторожный аналитик'; profileDesc = 'Вы тщательно проверяете данные и избегаете поспешных выводов. Это снижает риск ошибки, но может стоить времени.'; } else { profileType = 'Сбалансированный аналитик'; profileDesc = 'Вы сочетаете решительность с осторожностью, адаптируя стиль к ситуации. Это наиболее гибкий подход.'; } document.getElementById('fpProfileType').textContent = profileType; document.getElementById('fpProfileDesc').textContent = profileDesc; }

            document.getElementById('startBtn').addEventListener('click', () => goToChapter(1));
            document.getElementById('next1').addEventListener('click', () => goToChapter(2));
            document.getElementById('next2').addEventListener('click', () => goToChapter(3));
            document.getElementById('next3').addEventListener('click', () => goToChapter(4));
            document.getElementById('next4').addEventListener('click', () => goToChapter(5));

            const mu1 = [0.4, 0.5, 0.9, 0.3, 0.6];
            const mu2 = [0.6, 0.3, 0.8, 0.5, 0.2];
            const dayNames = ['Пн', 'Вт', 'Ср', 'Чт', 'Пт'];
            function updateIntersection() { const t1 = val('thresh1'), t2 = val('thresh2'); document.getElementById('thresh1_val').textContent = t1.toFixed(2); document.getElementById('thresh2_val').textContent = t2.toFixed(2); const days1 = [], days2 = [], intersection = []; for (let i = 0; i < 5; i++) { if (mu1[i] >= t1) days1.push(dayNames[i]); if (mu2[i] >= t2) days2.push(dayNames[i]); if (mu1[i] >= t1 && mu2[i] >= t2) intersection.push(dayNames[i]); } document.getElementById('days1_list').textContent = days1.length > 0 ? days1.join(', ') : '—'; document.getElementById('days2_list').textContent = days2.length > 0 ? days2.join(', ') : '—'; const resultDiv = document.getElementById('intersection_result'); const countDiv = document.getElementById('intersection_count'); if (intersection.length === 0) { resultDiv.innerHTML = '<span class="result-badge badge-no">Нет пересечения</span>'; countDiv.innerHTML = 'Дней в пересечении: <strong>0</strong>'; } else { resultDiv.innerHTML = intersection.map(d => `<span class="result-badge badge-yes">${d}</span>`).join(' '); countDiv.innerHTML = `Дней в пересечении: <strong>${intersection.length}</strong>`; if (intersection.length === 1) countDiv.innerHTML += ' ✅'; else if (intersection.length > 1) countDiv.innerHTML += ' — Слишком много, повысьте пороги'; } document.querySelectorAll('.fuzzy-table td.val-cell').forEach(cell => { cell.classList.remove('in-set', 'intersection-highlight'); }); const rows = document.querySelectorAll('.fuzzy-table tbody tr'); if (rows.length >= 2) { const cells1 = rows[0].querySelectorAll('.val-cell'); const cells2 = rows[1].querySelectorAll('.val-cell'); for (let i = 0; i < 5; i++) { if (mu1[i] >= t1) cells1[i].classList.add('in-set'); if (mu2[i] >= t2) cells2[i].classList.add('in-set'); if (mu1[i] >= t1 && mu2[i] >= t2) { cells1[i].classList.add('intersection-highlight'); cells2[i].classList.add('intersection-highlight'); } } } }
            document.getElementById('thresh1').addEventListener('input', updateIntersection);
            document.getElementById('thresh2').addEventListener('input', updateIntersection);
            document.getElementById('s1_2').addEventListener('input', () => { document.getElementById('s1_2_val').textContent = parseFloat(document.getElementById('s1_2').value).toFixed(2); });

            function triangularMu(x, a, b, c) { if (x <= a || x >= c) return 0; if (x <= b) return (x - a) / (b - a); return (c - x) / (c - b); }
            function drawGraph2_1() { const canvas = document.getElementById('canvas2_1'); if (!canvas) return; const container = canvas.parentElement; canvas.width = container.clientWidth; canvas.height = container.clientHeight; const ctx = canvas.getContext('2d'); const W = canvas.width, H = canvas.height; const pad = { top: 30, right: 40, bottom: 40, left: 50 }; const pw = W - pad.left - pad.right, ph = H - pad.top - pad.bottom; ctx.clearRect(0, 0, W, H); ctx.strokeStyle = '#e8ddd0'; ctx.lineWidth = 1; for (let i = 0; i <= 10; i++) { const x = pad.left + (i / 10) * pw, y = pad.top + (i / 10) * ph; ctx.beginPath(); ctx.moveTo(x, pad.top); ctx.lineTo(x, pad.top + ph); ctx.stroke(); ctx.beginPath(); ctx.moveTo(pad.left, y); ctx.lineTo(pad.left + pw, y); ctx.stroke(); ctx.fillStyle = '#7a6a5a'; ctx.font = '11px Georgia'; ctx.textAlign = 'center'; ctx.fillText((i * 100).toString(), x, pad.top + ph + 20); ctx.textAlign = 'right'; ctx.fillText((1 - i / 10).toFixed(1), pad.left - 8, y + 4); } ctx.strokeStyle = '#4a3320'; ctx.lineWidth = 2; ctx.beginPath(); ctx.moveTo(pad.left, pad.top + ph); ctx.lineTo(pad.left + pw, pad.top + ph); ctx.stroke(); ctx.beginPath(); ctx.moveTo(pad.left, pad.top); ctx.lineTo(pad.left, pad.top + ph); ctx.stroke(); const a = val('v2_1a'), b = val('v2_1b'), c = val('v2_1c'); document.getElementById('v2_1a_val').textContent = a; document.getElementById('v2_1b_val').textContent = b; document.getElementById('v2_1c_val').textContent = c; const toX = v => pad.left + (v / 1000) * pw; const toY = mu => pad.top + (1 - mu) * ph; const ax = toX(a), ay = toY(0), bx = toX(b), by = toY(1), cx = toX(c), cy = toY(0); ctx.fillStyle = 'rgba(139,90,43,0.15)'; ctx.strokeStyle = '#8b5a2b'; ctx.lineWidth = 2.5; ctx.beginPath(); ctx.moveTo(ax, ay); ctx.lineTo(bx, by); ctx.lineTo(cx, cy); ctx.closePath(); ctx.fill(); ctx.stroke(); [{ x: ax, y: ay, l: 'a' }, { x: bx, y: by, l: 'b' }, { x: cx, y: cy, l: 'c' }].forEach(pt => { ctx.fillStyle = '#8b5a2b'; ctx.beginPath(); ctx.arc(pt.x, pt.y, 5, 0, Math.PI * 2); ctx.fill(); ctx.fillStyle = '#fff'; ctx.beginPath(); ctx.arc(pt.x, pt.y, 2.5, 0, Math.PI * 2); ctx.fill(); ctx.fillStyle = '#4a3320'; ctx.font = 'bold 13px Georgia'; ctx.textAlign = 'center'; ctx.fillText(pt.l, pt.x, pt.y - 12); }); const x400 = toX(400); ctx.strokeStyle = '#c47e3b'; ctx.lineWidth = 1.5; ctx.setLineDash([5, 5]); ctx.beginPath(); ctx.moveTo(x400, pad.top); ctx.lineTo(x400, pad.top + ph); ctx.stroke(); ctx.setLineDash([]); const mu400 = triangularMu(400, a, b, c); ctx.fillStyle = '#c47e3b'; ctx.beginPath(); ctx.arc(x400, toY(mu400), 7, 0, Math.PI * 2); ctx.fill(); document.getElementById('mu2_1_display').textContent = mu400.toFixed(2); }
            ['v2_1a', 'v2_1b', 'v2_1c'].forEach(id => document.getElementById(id).addEventListener('input', drawGraph2_1));
            function updateMin() { const muA = val('muA'), muB = val('muB'), result = Math.min(muA, muB); document.getElementById('muA_val').textContent = muA.toFixed(2); document.getElementById('muB_val').textContent = muB.toFixed(2); document.getElementById('vis_muA').textContent = muA.toFixed(2); document.getElementById('vis_muB').textContent = muB.toFixed(2); document.getElementById('vis_result').textContent = result.toFixed(2); const c = document.getElementById('min_comment'); if (Math.abs(muA - muB) < 0.05) c.textContent = 'Значения почти равны.'; else if (muA < muB) c.textContent = `Район — слабое звено.`; else c.textContent = `Транспорт — слабое звено.`; }
            ['muA', 'muB'].forEach(id => document.getElementById(id).addEventListener('input', updateMin));

            const cafeFixed = { a: 100, b: 300, c: 500 };
            const parkFixed = { a: 300, b: 500, c: 700 };
            function drawGraph2_3() { const canvas = document.getElementById('canvas2_3'); if (!canvas) return; const container = canvas.parentElement; canvas.width = container.clientWidth; canvas.height = container.clientHeight; const ctx = canvas.getContext('2d'); const W = canvas.width, H = canvas.height; const pad = { top: 35, right: 30, bottom: 45, left: 55 }; const pw = W - pad.left - pad.right, ph = H - pad.top - pad.bottom; ctx.clearRect(0, 0, W, H); const toX = v => pad.left + (v / 750) * pw; const toY = mu => pad.top + (1 - mu) * ph; ctx.strokeStyle = '#e8ddd0'; ctx.lineWidth = 1; for (let i = 0; i <= 10; i++) { const x = pad.left + (i / 10) * pw, y = pad.top + (i / 10) * ph; ctx.beginPath(); ctx.moveTo(x, pad.top); ctx.lineTo(x, pad.top + ph); ctx.stroke(); ctx.beginPath(); ctx.moveTo(pad.left, y); ctx.lineTo(pad.left + pw, y); ctx.stroke(); ctx.fillStyle = '#7a6a5a'; ctx.font = '10px Georgia'; ctx.textAlign = 'center'; ctx.fillText(Math.round(i * 75).toString(), x, pad.top + ph + 18); ctx.textAlign = 'right'; ctx.fillText((1 - i / 10).toFixed(1), pad.left - 8, y + 4); } ctx.strokeStyle = '#4a3320'; ctx.lineWidth = 2; ctx.beginPath(); ctx.moveTo(pad.left, pad.top + ph); ctx.lineTo(pad.left + pw, pad.top + ph); ctx.stroke(); ctx.beginPath(); ctx.moveTo(pad.left, pad.top); ctx.lineTo(pad.left, pad.top + ph); ctx.stroke(); [{ p: cafeFixed, color: '#8b5a2b' }, { p: parkFixed, color: '#4a7c3f' }].forEach(({ p, color }) => { ctx.strokeStyle = color; ctx.lineWidth = 3; ctx.beginPath(); let first = true; for (let x = 0; x <= 750; x += 2) { const mu = triangularMu(x, p.a, p.b, p.c), sx = toX(x), sy = toY(mu); if (first) { ctx.moveTo(sx, sy); first = false; } else ctx.lineTo(sx, sy); } ctx.stroke(); }); ctx.strokeStyle = '#c47e3b'; ctx.lineWidth = 3.5; ctx.setLineDash([8, 4]); ctx.beginPath(); let first = true; for (let x = 0; x <= 750; x += 2) { const mu1 = triangularMu(x, cafeFixed.a, cafeFixed.b, cafeFixed.c), mu2 = triangularMu(x, parkFixed.a, parkFixed.b, parkFixed.c), m = Math.min(mu1, mu2), sx = toX(x), sy = toY(m); if (first) { ctx.moveTo(sx, sy); first = false; } else ctx.lineTo(sx, sy); } ctx.stroke(); ctx.setLineDash([]); const xVal = val('xPos'); const muCafeX = triangularMu(xVal, cafeFixed.a, cafeFixed.b, cafeFixed.c); const muParkX = triangularMu(xVal, parkFixed.a, parkFixed.b, parkFixed.c); const muMinX = Math.min(muCafeX, muParkX); const xx = toX(xVal); [{ mu: muCafeX, color: '#8b5a2b' }, { mu: muParkX, color: '#4a7c3f' }].forEach(d => { const sy = toY(d.mu); ctx.fillStyle = d.color; ctx.beginPath(); ctx.arc(xx, sy, 7, 0, Math.PI * 2); ctx.fill(); }); const syMin = toY(muMinX); ctx.fillStyle = '#c47e3b'; ctx.beginPath(); ctx.arc(xx, syMin, 10, 0, Math.PI * 2); ctx.fill(); ctx.fillStyle = '#fff'; ctx.beginPath(); ctx.arc(xx, syMin, 4, 0, Math.PI * 2); ctx.fill(); ctx.fillStyle = '#8b5a2b'; ctx.font = 'bold 12px Georgia'; ctx.textAlign = 'left'; ctx.fillText('μ_кафе', toX(80), toY(0.88)); ctx.fillStyle = '#4a7c3f'; ctx.fillText('μ_парк', toX(620), toY(0.92)); ctx.fillStyle = '#c47e3b'; ctx.fillText('min', toX(390), toY(0.55)); ctx.fillStyle = '#8b5a2b'; ctx.font = 'bold 11px Georgia'; ctx.textAlign = 'center'; ctx.fillText('☕ кафе', toX(300), pad.top + ph + 28); ctx.fillStyle = '#4a7c3f'; ctx.fillText('🌳 парк', toX(500), pad.top + ph + 28); document.getElementById('x_val').textContent = xVal + ' м'; const minBadge = document.getElementById('minBadge'); minBadge.textContent = 'min = ' + muMinX.toFixed(2); if (muMinX >= 0.45) minBadge.className = 'compromise-badge badge-high'; else if (muMinX >= 0.25) minBadge.className = 'compromise-badge badge-mid'; else minBadge.className = 'compromise-badge badge-low'; }
            document.getElementById('xPos').addEventListener('input', drawGraph2_3);

            let savedWeights = null, optimalTimeMin = null, optimalMus = null;
            function updateWeightsDisplay() { const w1 = val('w1'), w2 = val('w2'), w3 = val('w3'), sum = w1 + w2 + w3; document.getElementById('sum3_1').textContent = sum.toFixed(2); document.getElementById('sum3_1').style.color = Math.abs(sum - 1.0) < 0.01 ? 'var(--success)' : 'var(--error)'; }
            ['w1', 'w2', 'w3'].forEach(id => document.getElementById(id).addEventListener('input', updateWeightsDisplay));
            function timeToMinutes(sliderVal) { return 20 * 60 + Math.round(sliderVal * 5); }
            function minutesToTimeStr(minutes) { const h = Math.floor(minutes / 60), m = minutes % 60; return `${h}:${m < 10 ? '0' : ''}${m}`; }
            function triangularMuMinutes(minutes, aMin, bMin, cMin) { if (minutes <= aMin || minutes >= cMin) return 0; if (minutes <= bMin) return (minutes - aMin) / (bMin - aMin); return (cMin - minutes) / (cMin - bMin); }
            const witA = { a: 20 * 60 + 30, b: 21 * 60, c: 21 * 60 + 30, label: 'А', color: '#5c8a49' };
            const witB = { a: 20 * 60 + 5, b: 20 * 60 + 30, c: 20 * 60 + 55, label: 'Б', color: '#8b5a2b' };
            const witC = { a: 20 * 60 + 10, b: 20 * 60 + 45, c: 21 * 60 + 20, label: 'В', color: '#b3443c' };
            function getWeights() { return savedWeights ? savedWeights : [val('w1'), val('w2'), val('w3')]; }
            function findOptimalTime(weights) { const startMin = 20 * 60; let maxSum = 0, maxMin = startMin; const mus = [0, 0, 0]; for (let m = startMin; m <= startMin + 120; m++) { const muA = triangularMuMinutes(m, witA.a, witA.b, witA.c), muB = triangularMuMinutes(m, witB.a, witB.b, witB.c), muC = triangularMuMinutes(m, witC.a, witC.b, witC.c); const wSum = weights[0] * muA + weights[1] * muB + weights[2] * muC; if (wSum > maxSum) { maxSum = wSum; maxMin = m; mus[0] = muA; mus[1] = muB; mus[2] = muC; } } return { time: maxMin, mus, sum: maxSum }; }
            function drawGraph3_2() { const canvas = document.getElementById('canvas3_2'); if (!canvas) return; const container = canvas.parentElement; canvas.width = container.clientWidth; canvas.height = container.clientHeight; const ctx = canvas.getContext('2d'); const W = canvas.width, H = canvas.height; const pad = { top: 30, right: 30, bottom: 45, left: 55 }; const pw = W - pad.left - pad.right, ph = H - pad.top - pad.bottom; ctx.clearRect(0, 0, W, H); const totalMin = 120, startMin = 20 * 60; const toX = (m) => pad.left + ((m - startMin) / totalMin) * pw; const toY = (mu) => pad.top + (1 - mu) * ph; ctx.strokeStyle = '#e8ddd0'; ctx.lineWidth = 1; for (let i = 0; i <= 8; i++) { const x = pad.left + (i / 8) * pw, y = pad.top + (i / 4) * ph; ctx.beginPath(); ctx.moveTo(x, pad.top); ctx.lineTo(x, pad.top + ph); ctx.stroke(); ctx.beginPath(); ctx.moveTo(pad.left, y); ctx.lineTo(pad.left + pw, y); ctx.stroke(); ctx.fillStyle = '#7a6a5a'; ctx.font = '10px Georgia'; ctx.textAlign = 'center'; ctx.fillText(minutesToTimeStr(Math.round(startMin + (i / 8) * totalMin)), x, pad.top + ph + 18); ctx.textAlign = 'right'; ctx.fillText((1 - i / 4).toFixed(2), pad.left - 8, y + 4); } ctx.strokeStyle = '#4a3320'; ctx.lineWidth = 2; ctx.beginPath(); ctx.moveTo(pad.left, pad.top + ph); ctx.lineTo(pad.left + pw, pad.top + ph); ctx.stroke(); const sliderVal = val('timeSlider'); const currentMin = timeToMinutes(sliderVal); document.getElementById('time_val').textContent = minutesToTimeStr(currentMin); const weights = getWeights(); [{ wit: witA, w: weights[0] }, { wit: witB, w: weights[1] }, { wit: witC, w: weights[2] }].forEach(c => { ctx.strokeStyle = c.wit.color; ctx.lineWidth = 2.5; ctx.beginPath(); let first = true; for (let m = startMin; m <= startMin + totalMin; m++) { const mu = triangularMuMinutes(m, c.wit.a, c.wit.b, c.wit.c), sx = toX(m), sy = toY(mu); if (first) { ctx.moveTo(sx, sy); first = false; } else ctx.lineTo(sx, sy); } ctx.stroke(); }); ctx.strokeStyle = '#c47e3b'; ctx.lineWidth = 3.5; ctx.setLineDash([8, 4]); ctx.beginPath(); let first = true; for (let m = startMin; m <= startMin + totalMin; m++) { const muA = triangularMuMinutes(m, witA.a, witA.b, witA.c), muB = triangularMuMinutes(m, witB.a, witB.b, witB.c), muC = triangularMuMinutes(m, witC.a, witC.b, witC.c), wSum = weights[0] * muA + weights[1] * muB + weights[2] * muC, sx = toX(m), sy = toY(wSum); if (first) { ctx.moveTo(sx, sy); first = false; } else ctx.lineTo(sx, sy); } ctx.stroke(); ctx.setLineDash([]); const muACur = triangularMuMinutes(currentMin, witA.a, witA.b, witA.c); const muBCur = triangularMuMinutes(currentMin, witB.a, witB.b, witB.c); const muCCur = triangularMuMinutes(currentMin, witC.a, witC.b, witC.c); const wSumCur = weights[0] * muACur + weights[1] * muBCur + weights[2] * muCCur; [{ mu: muACur, color: witA.color }, { mu: muBCur, color: witB.color }, { mu: muCCur, color: witC.color }].forEach(d => { ctx.fillStyle = d.color; ctx.beginPath(); ctx.arc(toX(currentMin), toY(d.mu), 5, 0, Math.PI * 2); ctx.fill(); }); ctx.fillStyle = '#c47e3b'; ctx.beginPath(); ctx.arc(toX(currentMin), toY(wSumCur), 8, 0, Math.PI * 2); ctx.fill(); document.getElementById('res3_2').textContent = wSumCur.toFixed(2); }
            document.getElementById('timeSlider').addEventListener('input', drawGraph3_2);
            function fillTask3_3() { if (!optimalTimeMin || !optimalMus) return; const weights = getWeights(); document.getElementById('d_w1').textContent = weights[0].toFixed(2); document.getElementById('d_w2').textContent = weights[1].toFixed(2); document.getElementById('d_w3').textContent = weights[2].toFixed(2); document.getElementById('d_mu1').textContent = optimalMus[0].toFixed(2); document.getElementById('d_mu2').textContent = optimalMus[1].toFixed(2); document.getElementById('d_mu3').textContent = optimalMus[2].toFixed(2); document.getElementById('d_wm1').textContent = '?'; document.getElementById('d_wm2').textContent = '?'; document.getElementById('d_wm3').textContent = '?'; }
            function drawZoneGraph() { const canvas = document.getElementById('canvas4_3'); if (!canvas) return; const container = canvas.parentElement; canvas.width = container.clientWidth; canvas.height = container.clientHeight; const ctx = canvas.getContext('2d'); const W = canvas.width, H = canvas.height; const pad = { top: 30, right: 30, bottom: 45, left: 55 }; const pw = W - pad.left - pad.right, ph = H - pad.top - pad.bottom; ctx.clearRect(0, 0, W, H); const radius = val('radiusSlider'); document.getElementById('radius_val').textContent = radius + ' м'; ctx.strokeStyle = '#e8ddd0'; ctx.lineWidth = 1; for (let i = 0; i <= 10; i++) { const x = pad.left + (i / 10) * pw, y = pad.top + (i / 10) * ph; ctx.beginPath(); ctx.moveTo(x, pad.top); ctx.lineTo(x, pad.top + ph); ctx.stroke(); ctx.beginPath(); ctx.moveTo(pad.left, y); ctx.lineTo(pad.left + pw, y); ctx.stroke(); ctx.fillStyle = '#7a6a5a'; ctx.font = '10px Georgia'; ctx.textAlign = 'center'; ctx.fillText((i * 100).toString(), x, pad.top + ph + 18); ctx.textAlign = 'right'; ctx.fillText((1 - i / 10).toFixed(1), pad.left - 8, y + 4); } ctx.strokeStyle = '#4a3320'; ctx.lineWidth = 2; ctx.beginPath(); ctx.moveTo(pad.left, pad.top + ph); ctx.lineTo(pad.left + pw, pad.top + ph); ctx.stroke(); const toX = v => pad.left + (v / 600) * pw; const toY = mu => pad.top + (1 - mu) * ph; ctx.fillStyle = 'rgba(74,124,63,0.15)'; ctx.strokeStyle = '#4a7c3f'; ctx.lineWidth = 3; ctx.beginPath(); let first = true; for (let x = 0; x <= 600; x += 2) { const dist = Math.abs(x - 300); const mu = dist > radius ? 0 : 1 - dist / radius; const sx = toX(x), sy = toY(mu); if (first) { ctx.moveTo(sx, sy); first = false; } else ctx.lineTo(sx, sy); } ctx.lineTo(toX(600), toY(0)); ctx.lineTo(toX(0), toY(0)); ctx.closePath(); ctx.fill(); ctx.stroke(); const muC = Math.min(1.0, radius / 600); document.getElementById('muCenter').textContent = muC.toFixed(2); document.getElementById('zoneArea').textContent = ((radius / 100) ** 2).toFixed(1); }
            document.getElementById('radiusSlider').addEventListener('input', drawZoneGraph);
            const places = [{ id: 'cafe', mu: 0.61 }, { id: 'office', mu: 0.45 }, { id: 'metro', mu: 0.30 }];
            function updatePlaces() { const threshold = val('threshSlider'); document.getElementById('thresh_val').textContent = threshold.toFixed(2); places.forEach(p => { const card = document.querySelector(`[data-place="${p.id}"]`); if (!card) return; const status = card.querySelector('.place-status'); if (p.mu >= threshold) { card.className = 'place-card active'; status.textContent = '✓ Выезжаем'; status.style.color = 'var(--success)'; } else { card.className = 'place-card inactive'; status.textContent = '✗ Не выезжаем'; status.style.color = 'var(--error)'; } }); }
            document.getElementById('threshSlider').addEventListener('input', updatePlaces);
            document.querySelectorAll('.event-card').forEach(card => { card.addEventListener('click', () => { document.querySelectorAll('.event-card').forEach(c => c.classList.remove('selected')); card.classList.add('selected'); document.getElementById('v5_2').value = card.dataset.event; }); });
            document.querySelectorAll('.final-card').forEach(card => { card.addEventListener('click', () => { document.querySelectorAll('.final-card').forEach(c => c.classList.remove('selected')); card.classList.add('selected'); document.getElementById('v5_3').value = card.dataset.final; }); });

            document.querySelectorAll('.check-btn').forEach(btn => { btn.addEventListener('click', function() { const ch = parseInt(this.dataset.ch); const t = parseInt(this.dataset.t); const key = `${ch}_${t}`; if (ch === 1 && t === 1) { const o = [txt('o1'), txt('o2'), txt('o3'), txt('o4'), txt('o5')]; if (o.join('') === 'ABCED') { fb('f1_1', '✓ Верно! Порядок: часто врёт → иногда путает → обычно честен → почти всегда точен → эксперт.', 'ok'); state.tasks[key] = true; updateProgress(8); document.getElementById('t1_2').classList.remove('hidden'); document.getElementById('t1_2').scrollIntoView({ behavior: 'smooth' }); } else { incErrors(); fb('f1_1', '✗ Порядок нарушен. «Эксперт» — высшая степень надёжности.', 'err'); } } else if (ch === 1 && t === 2) { const v = val('s1_2'); if (v > 0.5) { fb('f1_2', `✓ Вы выбрали μ = ${v.toFixed(2)}. Обсудите: почему именно это значение?`, 'ok'); state.tasks[key] = true; updateProgress(8); document.getElementById('t1_3').classList.remove('hidden'); updateIntersection(); document.getElementById('t1_3').scrollIntoView({ behavior: 'smooth' }); } else { incErrors(); fb('f1_2', `✗ μ = ${v.toFixed(2)} — порог неопределённости. Нужно значение > 0.5.`, 'err'); } } else if (ch === 1 && t === 3) { const answer = txt('v1_3'); const t1 = val('thresh1'), t2 = val('thresh2'); const intersection = []; for (let i = 0; i < 5; i++) { if (mu1[i] >= t1 && mu2[i] >= t2) intersection.push(dayNames[i]); } if (intersection.length !== 1) { incErrors(); fb('f1_3', '⚠️ Сейчас в пересечении не ровно один день. Подберите пороги.', 'err'); } else if (answer === intersection[0].toUpperCase()) { fb('f1_3', `✓ Верно! Только ${intersection[0]} попадает в пересечение.`, 'ok'); state.tasks[key] = true; updateProgress(10); document.getElementById('next1').classList.add('show'); document.getElementById('next1').scrollIntoView({ behavior: 'smooth' }); } else { incErrors(); fb('f1_3', `✗ При текущих порогах в пересечении только ${intersection[0]}.`, 'err'); } } else if (ch === 2 && t === 1) { const a = val('v2_1a'), b = val('v2_1b'), c = val('v2_1c'); const mu400 = triangularMu(400, a, b, c); if (a < 400 && c > 400 && mu400 >= 0.6) { fb('f2_1', `✓ Верно! μ(400м) = ${mu400.toFixed(2)} ≥ 0.6.`, 'ok'); state.tasks[key] = true; updateProgress(8); document.getElementById('t2_2').classList.remove('hidden'); updateMin(); document.getElementById('t2_2').scrollIntoView({ behavior: 'smooth' }); } else { incErrors(); fb('f2_1', `✗ μ(400м) = ${mu400.toFixed(2)}. Нужно a < 400 < c и μ ≥ 0.6.`, 'err'); } } else if (ch === 2 && t === 2) { if (txt('v2_2') === '0.4') { fb('f2_2', '✓ Верно! min(0.7, 0.4) = 0.4.', 'ok'); state.tasks[key] = true; updateProgress(8); document.getElementById('t2_3').classList.remove('hidden'); setTimeout(drawGraph2_3, 300); document.getElementById('t2_3').scrollIntoView({ behavior: 'smooth' }); } else { incErrors(); fb('f2_2', '✗ min берёт меньшее. Что меньше: 0.7 или 0.4?', 'err'); } } else if (ch === 2 && t === 3) { const answer = val('v2_3'); const trueMax = 0.50; if (Math.abs(answer - trueMax) <= 0.03) { fb('f2_3', `✓ Верно! Максимум совместной уверенности = ${trueMax.toFixed(2)}. Это точка компромисса между кафе и парком.`, 'ok'); state.tasks[key] = true; updateProgress(10); document.getElementById('next2').classList.add('show'); document.getElementById('next2').scrollIntoView({ behavior: 'smooth' }); } else { incErrors(); fb('f2_3', `✗ Вы ввели ${answer.toFixed(2)}. Подвигайте точку X — максимум min равен 0.50 в точке пересечения функций.`, 'err'); } } else if (ch === 3 && t === 1) { const w1 = val('w1'), w2 = val('w2'), w3 = val('w3'); const sum = w1 + w2 + w3; if (Math.abs(sum - 1.0) > 0.015) { incErrors(); fb('f3_1', `✗ Сумма весов = ${sum.toFixed(2)}. Должна быть 1.0.`, 'err'); return; } if (!(w1 > w2 && w2 > w3 && w3 > 0)) { incErrors(); fb('f3_1', '✗ Нарушен порядок. Эксперт > Прохожий > Сосед, все > 0.', 'err'); return; } savedWeights = [w1, w2, w3]; fb('f3_1', `✓ Веса назначены верно.`, 'ok'); state.tasks[key] = true; updateProgress(8); document.getElementById('t3_2').classList.remove('hidden'); setTimeout(drawGraph3_2, 200); document.getElementById('t3_2').scrollIntoView({ behavior: 'smooth' }); } else if (ch === 3 && t === 2) { if (!savedWeights) { fb('f3_2', '⚠️ Сначала задайте веса.', 'err'); return; } const answer = txt('v3_2'); const weights = getWeights(); const opt = findOptimalTime(weights); const answerMin = answer.includes(':') ? parseInt(answer.split(':')[0]) * 60 + parseInt(answer.split(':')[1]) : 0; if (Math.abs(answerMin - opt.time) <= 5) { fb('f3_2', `✓ Верно! Оптимальное время: ${minutesToTimeStr(opt.time)}.`, 'ok'); state.tasks[key] = true; updateProgress(8); optimalTimeMin = opt.time; optimalMus = opt.mus; document.getElementById('timeSlider').value = Math.round((opt.time - 20 * 60) / 5); document.getElementById('time_val').textContent = minutesToTimeStr(opt.time); drawGraph3_2(); document.getElementById('t3_3').classList.remove('hidden'); fillTask3_3(); document.getElementById('t3_3').scrollIntoView({ behavior: 'smooth' }); } else { incErrors(); fb('f3_2', `✗ Вы ввели ${answer}. Оптимум около ${minutesToTimeStr(opt.time)}.`, 'err'); } } else if (ch === 3 && t === 3) { const answer = val('v3_3'); if (!optimalMus || !savedWeights) { fb('f3_3', '⚠️ Сначала выполните задание 3.2.', 'err'); return; } const trueSum = savedWeights[0] * optimalMus[0] + savedWeights[1] * optimalMus[1] + savedWeights[2] * optimalMus[2]; if (Math.abs(answer - trueSum) < 0.03) { fb('f3_3', `✓ Верно! μ_итог = ${trueSum.toFixed(2)}.`, 'ok'); state.tasks[key] = true; updateProgress(8); document.getElementById('next3').classList.add('show'); document.getElementById('next3').scrollIntoView({ behavior: 'smooth' }); } else { incErrors(); fb('f3_3', `✗ Вы ввели ${answer.toFixed(2)}. Правильное значение: ${trueSum.toFixed(2)}.`, 'err'); } } else if (ch === 4 && t === 1) { const answer = val('v4_1'); if (Math.abs(answer - 0.61) < 0.02) { fb('f4_1', '✓ Верно! min(0.61, 0.61, 0.85) = 0.61.', 'info'); state.tasks[key] = true; updateProgress(5); document.getElementById('t4_2').classList.remove('hidden'); document.getElementById('t4_2').scrollIntoView({ behavior: 'smooth' }); } else { incErrors(); fb('f4_1', '✗ min выбирает наименьшее из трёх.', 'info'); } } else if (ch === 4 && t === 2) { const ans2100 = val('v4_2_2100'), ans2115 = val('v4_2_2115'); const ok2100 = Math.abs(ans2100 - 0.503) < 0.005; const ok2115 = Math.abs(ans2115 - 0.4585) < 0.005; if (!ok2100 || !ok2115) { incErrors(); fb('f4_2', 'Одно или оба значения неверны. Перемножьте w и μ для каждого свидетеля и сложите.', 'info'); } else { fb('f4_2', '✓ Оба верны! 21:00 (0.503) > 21:15 (0.459). Основная версия устояла.', 'info'); state.tasks[key] = true; updateProgress(5); document.getElementById('t4_3').classList.remove('hidden'); setTimeout(drawZoneGraph, 200); document.getElementById('t4_3').scrollIntoView({ behavior: 'smooth' }); } } else if (ch === 4 && t === 3) { const answer = val('v4_3'); if (Math.abs(answer - 360) <= 30) { fb('f4_3', '✓ Отлично! При радиусе 360 м μ = 0.6.', 'info'); state.tasks[key] = true; updateProgress(4); document.getElementById('next4').classList.add('show'); document.getElementById('next4').scrollIntoView({ behavior: 'smooth' }); } else { incErrors(); fb('f4_3', `При радиусе ${answer} м μ в центре = ${(answer/600).toFixed(2)}. Нужно 0.6.`, 'info'); } } else if (ch === 5 && t === 1) { const answer = txt('v5_1'); const threshold = val('threshSlider'); if (threshold <= 0.45) { fb('f5_1', '⚠️ Повысьте порог выше 0.45, чтобы отсечь офис и метро.', 'info'); return; } if (threshold > 0.61) { fb('f5_1', '⚠️ Снизьте порог до 0.61 или ниже.', 'info'); return; } if (answer !== 'CAFE') { incErrors(); fb('f5_1', '✗ При текущем пороге осталось только кафе.', 'info'); return; } fb('f5_1', '✓ Верно! Остаётся только кафе.', 'info'); logDecision('cafe'); state.tasks[key] = true; document.getElementById('t5_2').classList.remove('hidden'); document.getElementById('t5_2').scrollIntoView({ behavior: 'smooth' }); } else if (ch === 5 && t === 2) { const answer = txt('v5_2'); if (!answer) { fb('f5_2', '⚠️ Выберите интерпретацию.', 'info'); return; } logDecision(answer.toLowerCase()); fb('f5_2', answer === 'CONFIRM' ? '✓ Вы считаете звонок подтверждением.' : '✓ Вы считаете звонок случайностью.', 'info'); state.tasks[key] = true; document.getElementById('t5_3').classList.remove('hidden'); document.getElementById('t5_3').scrollIntoView({ behavior: 'smooth' }); } }); });

            document.getElementById('btnFinish').addEventListener('click', function() { const answer = document.getElementById('v5_3').value; if (!answer) { fb('f5_3', '⚠️ Выберите, куда выезжать.', 'info'); return; } logDecision(answer); showFinalPage(answer); });

            updateIntersection();
            drawGraph2_1();
            updateMin();
            updateWeightsDisplay();
            updatePlaces();
            updateProgress(0);
            window.addEventListener('resize', () => { if (document.getElementById('ch2').classList.contains('active')) { drawGraph2_1(); if (document.getElementById('t2_3').offsetParent) drawGraph2_3(); } if (document.getElementById('ch3').classList.contains('active') && document.getElementById('t3_2').offsetParent) drawGraph3_2(); if (document.getElementById('ch4').classList.contains('active') && document.getElementById('t4_3').offsetParent) drawZoneGraph(); });
        })();
    </script>
</body>
</html>
