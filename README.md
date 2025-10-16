<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fashion MNIST Banner</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'SF Pro Display', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: #0a0a0a;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        .banner-container {
            width: 100%;
            max-width: 1200px;
            height: 400px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
            border-radius: 20px;
            position: relative;
            overflow: hidden;
            box-shadow: 0 20px 60px rgba(102, 126, 234, 0.4);
        }

        .grid-background {
            position: absolute;
            width: 100%;
            height: 100%;
            opacity: 0.1;
            background-image: 
                linear-gradient(rgba(255,255,255,0.1) 1px, transparent 1px),
                linear-gradient(90deg, rgba(255,255,255,0.1) 1px, transparent 1px);
            background-size: 50px 50px;
        }

        .content {
            position: relative;
            z-index: 2;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            padding: 0 60px;
        }

        .icon {
            font-size: 64px;
            margin-bottom: 20px;
            animation: float 3s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }

        h1 {
            font-size: 72px;
            font-weight: 800;
            color: white;
            margin-bottom: 10px;
            letter-spacing: -2px;
            text-shadow: 0 4px 20px rgba(0,0,0,0.3);
        }

        .subtitle {
            font-size: 28px;
            color: rgba(255, 255, 255, 0.9);
            font-weight: 300;
            margin-bottom: 30px;
            letter-spacing: 0.5px;
        }

        .tech-stack {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
        }

        .tech-badge {
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(10px);
            padding: 8px 20px;
            border-radius: 20px;
            color: white;
            font-size: 14px;
            font-weight: 600;
            border: 1px solid rgba(255, 255, 255, 0.3);
            transition: all 0.3s ease;
        }

        .tech-badge:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-2px);
        }

        .decorative-elements {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
        }

        .circle {
            position: absolute;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.1);
            animation: pulse 4s ease-in-out infinite;
        }

        .circle-1 {
            width: 300px;
            height: 300px;
            top: -100px;
            right: -50px;
            animation-delay: 0s;
        }

        .circle-2 {
            width: 200px;
            height: 200px;
            bottom: -50px;
            left: -30px;
            animation-delay: 1s;
        }

        .circle-3 {
            width: 150px;
            height: 150px;
            top: 50%;
            right: 10%;
            animation-delay: 2s;
        }

        @keyframes pulse {
            0%, 100% {
                transform: scale(1);
                opacity: 0.1;
            }
            50% {
                transform: scale(1.1);
                opacity: 0.2;
            }
        }

        .neural-network {
            position: absolute;
            right: 80px;
            top: 50%;
            transform: translateY(-50%);
            opacity: 0.15;
        }

        .nn-layer {
            display: flex;
            gap: 20px;
            margin-bottom: 30px;
            justify-content: center;
        }

        .nn-node {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: white;
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.5);
            animation: glow 2s ease-in-out infinite;
        }

        .nn-node:nth-child(1) { animation-delay: 0s; }
        .nn-node:nth-child(2) { animation-delay: 0.2s; }
        .nn-node:nth-child(3) { animation-delay: 0.4s; }
        .nn-node:nth-child(4) { animation-delay: 0.6s; }

        @keyframes glow {
            0%, 100% {
                opacity: 0.3;
                transform: scale(1);
            }
            50% {
                opacity: 1;
                transform: scale(1.2);
            }
        }

        .stats {
            position: absolute;
            bottom: 30px;
            right: 60px;
            display: flex;
            gap: 40px;
        }

        .stat-item {
            text-align: center;
        }

        .stat-value {
            font-size: 32px;
            font-weight: 800;
            color: white;
            text-shadow: 0 2px 10px rgba(0,0,0,0.3);
        }

        .stat-label {
            font-size: 12px;
            color: rgba(255, 255, 255, 0.8);
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-top: 5px;
        }

        .download-btn {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(10px);
            color: white;
            padding: 12px 24px;
            border-radius: 12px;
            border: 1px solid rgba(255, 255, 255, 0.3);
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            z-index: 10;
        }

        .download-btn:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-2px);
        }

        @media (max-width: 768px) {
            .banner-container {
                height: 500px;
            }

            h1 {
                font-size: 48px;
            }

            .subtitle {
                font-size: 20px;
            }

            .content {
                padding: 0 30px;
            }

            .neural-network {
                display: none;
            }

            .stats {
                position: relative;
                bottom: auto;
                right: auto;
                margin-top: 30px;
                justify-content: flex-start;
            }
        }
    </style>
</head>
<body>
    <div class="banner-container">
        <button class="download-btn" onclick="downloadBanner()">📥 Download Banner</button>
        
        <div class="grid-background"></div>
        
        <div class="decorative-elements">
            <div class="circle circle-1"></div>
            <div class="circle circle-2"></div>
            <div class="circle circle-3"></div>
        </div>

        <div class="neural-network">
            <div class="nn-layer">
                <div class="nn-node"></div>
                <div class="nn-node"></div>
                <div class="nn-node"></div>
                <div class="nn-node"></div>
            </div>
            <div class="nn-layer">
                <div class="nn-node"></div>
                <div class="nn-node"></div>
                <div class="nn-node"></div>
            </div>
            <div class="nn-layer">
                <div class="nn-node"></div>
                <div class="nn-node"></div>
            </div>
        </div>

        <div class="content">
            <div class="icon">👔</div>
            <h1>Fashion MNIST</h1>
            <div class="subtitle">CNN-based Image Classification</div>
            
            <div class="tech-stack">
                <div class="tech-badge">🔥 PyTorch</div>
                <div class="tech-badge">🧠 Deep Learning</div>
                <div class="tech-badge">👁️ Computer Vision</div>
                <div class="tech-badge">📊 CNN</div>
            </div>
        </div>

        <div class="stats">
            <div class="stat-item">
                <div class="stat-value">86%</div>
                <div class="stat-label">Accuracy</div>
            </div>
            <div class="stat-item">
                <div class="stat-value">10</div>
                <div class="stat-label">Classes</div>
            </div>
            <div class="stat-item">
                <div class="stat-value">70K</div>
                <div class="stat-label">Images</div>
            </div>
        </div>
    </div>

    <script>
        function downloadBanner() {
            // Simula download - em produção, você usaria html2canvas ou similar
            alert('💡 Dica: Use a ferramenta de screenshot do seu sistema ou html2canvas para capturar o banner!\n\nPara usar no GitHub:\n1. Capture o banner\n2. Salve como "banner.png"\n3. Adicione ao README: ![Banner](./assets/banner.png)');
        }
    </script>
</body>
</html>
