<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ScamBase — база мошенников | @UrumaKap</title>
    <style>
        :root {
            --bg: #08080f;
            --bg2: #0c0c18;
            --surface: #13132a;
            --surface2: #1a1a35;
            --border: #2a2a45;
            --border-accent: #7c3aed;
            --text: #e8e8f5;
            --text2: #9a9abf;
            --accent: #8b5cf6;
            --accent2: #a78bfa;
            --accent-glow: rgba(139, 92, 246, 0.25);
            --red: #ef4444;
            --red-glow: rgba(239, 68, 68, 0.25);
            --green: #22c55e;
            --blue: #3b82f6;
            --yellow: #f59e0b;
            --radius: 14px;
            --radius-sm: 8px;
            --radius-xs: 6px;
            --font: 'Segoe UI', system-ui, -apple-system, sans-serif;
            --shadow: 0 2px 16px rgba(0, 0, 0, 0.5);
            --shadow-lg: 0 8px 32px rgba(0, 0, 0, 0.7);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: var(--font);
            background: var(--bg);
            background-image:
                radial-gradient(ellipse at 15% 0%, rgba(139, 92, 246, 0.07) 0%, transparent 55%),
                radial-gradient(ellipse at 85% 100%, rgba(139, 92, 246, 0.05) 0%, transparent 55%),
                radial-gradient(ellipse at 50% 50%, rgba(120, 80, 220, 0.03) 0%, transparent 70%);
            background-attachment: fixed;
            color: var(--text);
            min-height: 100vh;
            line-height: 1.6;
            -webkit-font-smoothing: antialiased;
            -webkit-tap-highlight-color: transparent;
        }

        ::-webkit-scrollbar {
            width: 5px;
        }
        ::-webkit-scrollbar-track {
            background: var(--bg);
        }
        ::-webkit-scrollbar-thumb {
            background: #3a3a58;
            border-radius: 3px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #555;
        }

        /* ========== HEADER ========== */
        header {
            background: rgba(19, 19, 42, 0.88);
            border-bottom: 1px solid var(--border);
            position: sticky;
            top: 0;
            z-index: 100;
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
        }
        .header-inner {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            height: 60px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 10px;
        }
        .logo-group {
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
            flex-shrink: 0;
            text-decoration: none;
        }
        .logo-icon-box {
            width: 38px;
            height: 38px;
            background: linear-gradient(135deg, #8b5cf6, #6d28d9);
            border-radius: 9px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 19px;
            flex-shrink: 0;
            box-shadow: 0 2px 14px var(--accent-glow);
        }
        .logo-text {
            font-weight: 800;
            font-size: 19px;
            color: var(--text);
            letter-spacing: -0.5px;
        }
        .owner-tag {
            font-size: 10px;
            background: var(--surface2);
            padding: 3px 8px;
            border-radius: 12px;
            color: var(--text2);
            border: 1px solid var(--border);
            white-space: nowrap;
        }
        .owner-tag span {
            color: var(--accent);
            font-weight: 700;
        }

        nav {
            display: flex;
            align-items: center;
            gap: 4px;
            flex-wrap: wrap;
        }
        nav a {
            color: var(--text2);
            text-decoration: none;
            font-size: 13px;
            font-weight: 600;
            padding: 7px 13px;
            border-radius: 18px;
            cursor: pointer;
            transition: all 0.2s;
            white-space: nowrap;
            letter-spacing: 0.2px;
        }
        nav a:hover {
            color: #fff;
            background: var(--surface2);
        }
        nav a.active-tab {
            color: #fff;
            background: var(--accent);
            box-shadow: 0 2px 10px var(--accent-glow);
        }
        .btn-outline {
            border: 1px solid var(--border);
            background: transparent;
            color: var(--text2);
            font-family: var(--font);
            font-size: 12px;
            font-weight: 600;
            padding: 7px 13px;
            border-radius: 18px;
            cursor: pointer;
            transition: all 0.2s;
            white-space: nowrap;
            letter-spacing: 0.2px;
        }
        .btn-outline:hover {
            border-color: var(--accent);
            color: #fff;
            background: rgba(139, 92, 246, 0.08);
        }
        .user-info {
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .user-avatar-sm {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 12px;
            color: #fff;
            flex-shrink: 0;
        }
        .user-name-sm {
            font-weight: 600;
            font-size: 13px;
            color: var(--text);
        }

        /* ========== HERO + ПОИСК ========== */
        .hero {
            text-align: center;
            padding: 44px 20px 28px;
            max-width: 650px;
            margin: 0 auto;
        }
        .hero h1 {
            font-size: 32px;
            font-weight: 800;
            letter-spacing: -1px;
            line-height: 1.2;
            margin-bottom: 8px;
        }
        .hero h1 span {
            background: linear-gradient(135deg, #a78bfa, #8b5cf6);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        .hero p {
            color: var(--text2);
            font-size: 15px;
            margin-bottom: 20px;
        }
        .search-box {
            display: flex;
            gap: 6px;
            max-width: 500px;
            margin: 0 auto;
            background: var(--surface2);
            border-radius: 28px;
            padding: 4px;
            border: 1px solid var(--border);
            transition: border-color 0.3s, box-shadow 0.3s;
        }
        .search-box:focus-within {
            border-color: var(--accent);
            box-shadow: 0 0 20px var(--accent-glow);
        }
        .search-box input {
            flex: 1;
            padding: 11px 16px;
            border: none;
            background: transparent;
            color: var(--text);
            font-size: 14px;
            outline: none;
            font-family: var(--font);
        }
        .search-box input::placeholder {
            color: #555;
        }
        .search-box button {
            padding: 11px 20px;
            border-radius: 24px;
            border: none;
            background: var(--accent);
            color: #fff;
            font-weight: 700;
            font-size: 13px;
            cursor: pointer;
            font-family: var(--font);
            white-space: nowrap;
            transition: background 0.2s, box-shadow 0.2s;
            box-shadow: 0 2px 10px var(--accent-glow);
        }
        .search-box button:hover {
            background: var(--accent2);
            box-shadow: 0 4px 18px var(--accent-glow);
        }
        .search-hints {
            display: flex;
            gap: 6px;
            justify-content: center;
            flex-wrap: wrap;
            margin-top: 10px;
            font-size: 11px;
            color: #555;
        }
        .search-hints span {
            cursor: pointer;
            padding: 4px 10px;
            border-radius: 10px;
            background: var(--surface2);
            border: 1px solid var(--border);
            transition: all 0.2s;
            white-space: nowrap;
        }
        .search-hints span:hover {
            border-color: var(--accent);
            color: var(--accent2);
        }

        /* ========== STATS ========== */
        .stats-row {
            display: flex;
            gap: 10px;
            justify-content: center;
            flex-wrap: wrap;
            padding: 0 20px 18px;
            max-width: 1200px;
            margin: 0 auto;
        }
        .stat-card {
            background: var(--surface);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 14px 18px;
            text-align: center;
            min-width: 90px;
            flex: 1;
            max-width: 160px;
            transition: transform 0.2s, border-color 0.2s, box-shadow 0.2s;
        }
        .stat-card:hover {
            transform: translateY(-2px);
            border-color: var(--border-accent);
            box-shadow: 0 4px 16px rgba(139, 92, 246, 0.1);
        }
        .stat-card .num {
            font-size: 24px;
            font-weight: 800;
            color: var(--accent);
        }
        .stat-card .lbl {
            font-size: 10px;
            color: var(--text2);
            text-transform: uppercase;
            letter-spacing: 0.5px;
            margin-top: 2px;
        }

        /* ========== MAIN ========== */
        .main-wrap {
            max-width: 1100px;
            margin: 0 auto;
            padding: 0 20px 50px;
        }
        .section-head {
            font-size: 18px;
            font-weight: 700;
            margin-bottom: 14px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .section-head::before {
            content: '';
            width: 4px;
            height: 20px;
            background: var(--accent);
            border-radius: 2px;
            box-shadow: 0 0 8px var(--accent-glow);
        }
        .alert {
            background: rgba(139, 92, 246, 0.05);
            border: 1px solid rgba(139, 92, 246, 0.15);
            border-radius: var(--radius);
            padding: 12px 16px;
            margin-bottom: 20px;
            font-size: 12px;
            color: #aaa;
            display: flex;
            gap: 8px;
            align-items: flex-start;
        }

        /* ========== CARDS ========== */
        .grid-2 {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(310px, 1fr));
            gap: 12px;
            margin-bottom: 28px;
        }
        .card {
            background: var(--surface);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 18px;
            transition: border 0.2s, transform 0.2s, box-shadow 0.2s;
            position: relative;
            overflow: hidden;
        }
        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--accent), transparent);
            opacity: 0;
            transition: opacity 0.3s;
        }
        .card:hover::before {
            opacity: 0.6;
        }
        .card:hover {
            border-color: #444;
            transform: translateY(-2px);
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.5);
        }
        .card-top {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 8px;
            gap: 8px;
        }
        .card-avatar {
            width: 42px;
            height: 42px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            font-size: 16px;
            color: #fff;
            flex-shrink: 0;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.4);
        }
        .pill {
            padding: 3px 9px;
            border-radius: 10px;
            font-size: 9px;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.3px;
        }
        .pill-red {
            background: rgba(239, 68, 68, 0.2);
            color: var(--red);
        }
        .pill-yellow {
            background: rgba(245, 158, 11, 0.15);
            color: var(--yellow);
        }
        .pill-purple {
            background: rgba(139, 92, 246, 0.2);
            color: var(--accent2);
        }
        .card-title {
            font-weight: 700;
            font-size: 15px;
            margin-bottom: 2px;
        }
        .card-sub {
            font-size: 11px;
            color: var(--text2);
            margin-bottom: 8px;
        }
        .card-info {
            font-size: 11px;
            color: var(--text2);
            display: flex;
            flex-direction: column;
            gap: 4px;
            margin-bottom: 10px;
        }
        .card-info .row {
            display: flex;
            gap: 5px;
            align-items: center;
        }
        .card-info .lbl {
            color: #666;
            min-width: 60px;
            flex-shrink: 0;
            font-size: 10px;
        }
        .card-info .val {
            color: var(--text);
            font-family: 'SF Mono', 'Cascadia Code', monospace;
            font-size: 10px;
            word-break: break-all;
        }
        .card-bottom {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 10px;
            color: #555;
            flex-wrap: wrap;
            gap: 4px;
            padding-top: 8px;
            border-top: 1px solid var(--border);
        }
        .btn-xs {
            padding: 4px 10px;
            border-radius: 12px;
            font-size: 10px;
            font-weight: 700;
            cursor: pointer;
            border: none;
            font-family: var(--font);
            transition: opacity 0.2s;
        }
        .btn-xs.del {
            background: rgba(239, 68, 68, 0.2);
            color: var(--red);
        }
        .btn-xs.del:hover {
            background: rgba(239, 68, 68, 0.35);
        }
        .btn-xs.approve {
            background: rgba(34, 197, 94, 0.2);
            color: var(--green);
        }
        .btn-xs.edit {
            background: rgba(139, 92, 246, 0.2);
            color: var(--accent2);
        }

        /* ========== BLOG ========== */
        .blog-card {
            background: var(--surface);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 20px;
            margin-bottom: 12px;
            transition: border 0.2s;
        }
        .blog-card:hover {
            border-color: #444;
        }
        .blog-card h3 {
            font-size: 16px;
            margin-bottom: 4px;
        }
        .blog-meta {
            font-size: 11px;
            color: #555;
            margin-bottom: 8px;
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
            align-items: center;
        }
        .blog-body {
            font-size: 13px;
            color: #bbb;
            line-height: 1.7;
            white-space: pre-wrap;
        }
        .blog-actions {
            margin-top: 10px;
            padding-top: 8px;
            border-top: 1px solid var(--border);
            display: flex;
            gap: 5px;
        }

        /* ========== FORMS ========== */
        .form-card {
            background: var(--surface);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 22px;
            max-width: 600px;
        }
        .field {
            margin-bottom: 14px;
        }
        .field label {
            display: block;
            font-size: 10px;
            font-weight: 700;
            color: var(--text2);
            text-transform: uppercase;
            letter-spacing: 0.5px;
            margin-bottom: 4px;
        }
        .field input,
        .field textarea,
        .field select {
            width: 100%;
            padding: 10px 14px;
            border-radius: var(--radius-sm);
            border: 1px solid var(--border);
            background: var(--surface2);
            color: var(--text);
            font-size: 13px;
            font-family: var(--font);
            outline: none;
            resize: vertical;
            transition: border 0.2s, box-shadow 0.2s;
        }
        .field input:focus,
        .field textarea:focus,
        .field select:focus {
            border-color: var(--accent);
            box-shadow: 0 0 0 3px rgba(139, 92, 246, 0.08);
        }
        .field textarea {
            min-height: 80px;
        }
        .row-2 {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
        }
        .btn-full {
            width: 100%;
            padding: 12px;
            border-radius: 24px;
            border: none;
            font-weight: 700;
            font-size: 14px;
            cursor: pointer;
            font-family: var(--font);
            transition: all 0.2s;
            letter-spacing: 0.3px;
        }
        .btn-purple {
            background: var(--accent);
            color: #fff;
            box-shadow: 0 2px 10px var(--accent-glow);
        }
        .btn-purple:hover {
            background: var(--accent2);
            box-shadow: 0 4px 18px var(--accent-glow);
        }
        .btn-green {
            background: var(--green);
            color: #000;
        }
        .btn-blue {
            background: var(--blue);
            color: #fff;
        }
        .btn-red {
            background: var(--red);
            color: #fff;
            box-shadow: 0 2px 10px var(--red-glow);
        }

        /* ========== MODAL ========== */
        .modal-bg {
            display: none;
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, 0.85);
            z-index: 200;
            align-items: center;
            justify-content: center;
            padding: 16px;
            backdrop-filter: blur(4px);
            -webkit-backdrop-filter: blur(4px);
        }
        .modal-bg.open {
            display: flex;
        }
        .modal-box {
            background: var(--surface);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 24px 20px;
            max-width: 400px;
            width: 100%;
            position: relative;
            animation: modalIn 0.3s ease;
            box-shadow: 0 0 40px rgba(139, 92, 246, 0.1);
        }
        @keyframes modalIn {
            from {
                opacity: 0;
                transform: translateY(-20px) scale(0.95);
            }
            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }
        .modal-box h2 {
            font-size: 20px;
            margin-bottom: 16px;
            text-align: center;
        }
        .modal-close {
            position: absolute;
            top: 10px;
            right: 14px;
            background: none;
            border: none;
            color: #777;
            font-size: 20px;
            cursor: pointer;
            font-family: var(--font);
            transition: color 0.2s;
        }
        .modal-close:hover {
            
