<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Electro İs Pro V18.8 - All Custom Images Edition</title>
    <style>
        * { box-sizing: border-box; user-select: none; }
        body { font-family: Arial, sans-serif; margin: 0; background: radial-gradient(circle at center, #1a2a3a 0%, #0d131a 100%); color: #333; height: 100vh; overflow: hidden; display: flex; flex-direction: column; }

        /* 🎬 ELECTRO İS ÖZEL AÇILIŞ EKRANI */
        #splash-screen { 
            position: fixed; 
            top: 0; 
            left: 0; 
            width: 100vw; 
            height: 100vh; 
            background-color: #050505; 
            z-index: 9999; 
            display: flex; 
            flex-direction: column; 
            justify-content: center; 
            align-items: center; 
            transition: opacity 0.8s ease-out; 
        }

        .animation-container {
            position: relative;
            width: 200px;
            height: 200px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .glow-orb {
            position: absolute;
            width: 25px;
            height: 25px;
            border-radius: 50%;
            filter: blur(4px);
            opacity: 0;
            animation: orbMerge 2.8s cubic-bezier(0.25, 1, 0.5, 1) forwards;
        }

        .orb-red { background: #00a4ef; box-shadow: 0 0 20px #00a4ef; transform: translate(-100px, -100px); animation-delay: 0.1s; }
        .orb-green { background: #00a4ef; box-shadow: 0 0 20px #00a4ef; transform: translate(100px, -100px); animation-delay: 0.3s; }
        .orb-blue { background: #00a4ef; box-shadow: 0 0 20px #00a4ef; transform: translate(-100px, 100px); animation-delay: 0.2s; }
        .orb-yellow { background: #00a4ef; box-shadow: 0 0 20px #00a4ef; transform: translate(100px, 100px); animation-delay: 0.4s; }

        @keyframes orbMerge {
            0% { opacity: 0; filter: blur(10px); }
            30% { opacity: 0.9; filter: blur(4px); }
            65% { transform: translate(0, 0); opacity: 1; filter: blur(2px); }
            80% { transform: translate(0, 0); opacity: 0.3; filter: blur(15px); }
            100% { transform: translate(0, 0); opacity: 0; filter: blur(30px); }
        }

        /* 🟦 ELECTRO İS GRID YAPISI */
        .brand-wrapper {
            position: absolute;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            opacity: 0;
            scale: 0.7;
            animation: logoAppear 1.2s cubic-bezier(0.15, 0.85, 0.35, 1) 2.0s forwards;
        }

        .brand-cube-grid { 
            display: grid; 
            grid-template-columns: 1fr 1fr; 
            gap: 10px; 
            width: 180px; 
            height: 180px; 
            transform: perspective(500px) rotateY(-38deg) rotateX(8deg);
        }
        
        .brand-cube { 
            border-radius: 4px;
            box-shadow: 0 0 25px rgba(0, 120, 215, 0.6);
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            border: 2px solid rgba(255,255,255,0.25);
            background-color: rgba(0, 120, 215, 0.2);
        }

        .brand-cube img, .element-img-wrap img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .brand-text-bottom {
            margin-top: 25px;
            color: #ffffff;
            font-family: 'Segoe UI', Arial, sans-serif;
            font-weight: bold;
            font-size: 24px;
            letter-spacing: 3px;
            text-align: center;
            text-shadow: 0 0 15px rgba(0, 120, 215, 0.8);
        }

        @keyframes logoAppear {
            0% { opacity: 0; scale: 0.7; filter: drop-shadow(0 0 0px rgba(0, 120, 215, 0)); }
            50% { filter: drop-shadow(0 0 45px rgba(0, 120, 215, 0.95)) drop-shadow(0 0 15px #fff); }
            100% { opacity: 1; scale: 1; filter: drop-shadow(0 0 30px rgba(0, 120, 215, 0.85)); }
        }

        /* 🏛️ ÜST BAR */
        header { background: rgba(255, 255, 255, 0.85); backdrop-filter: blur(10px); padding: 10px; text-align: center; border-bottom: 3px solid #0078d7; box-shadow: 0 2px 10px rgba(0,0,0,0.1); z-index: 60; }
        header h1 { font-size: 14px; margin: 0; color: #111; }
        #status-bar { color: #ff3366; font-weight: bold; font-size: 12px; margin-top: 5px; min-height: 18px; }
        
        /* 🏙️ ANA KONTEYNER */
        #main-container { flex: 1; display: flex; position: relative; height: 80vh; }

        /* 🎛️ SOL YAN MENÜ */
        .menu-sidebar { width: 125px; background: rgba(255, 255, 255, 0.45); backdrop-filter: blur(15px); border-right: 2px solid rgba(255,255,255,0.3); display: flex; flex-direction: column; gap: 4px; padding: 6px; z-index: 50; overflow-y: auto; }
        button { width: 100%; padding: 8px 2px; border-radius: 6px; border: 1px solid #0078d7; background: rgba(255, 253, 243, 0.8); color: #0078d7; font-weight: bold; font-size: 10px; text-align: center; cursor: pointer; }
        button:active { background: #0078d7; color: #000; }
        .btn-reset { background: #ff3366; color: #fff; border-color: #ff3366; margin-top: auto; padding: 10px 2px; }

        /* ⬜ BEYAZ TAHTA */
        #workspace { flex: 1; position: relative; overflow: hidden; background: rgba(255, 255, 255, 0.15); backdrop-filter: blur(20px); background-image: radial-gradient(rgba(255, 255, 255, 0.08) 1px, transparent 1px); background-size: 24px 24px; }
        
        .workspace-background-logo {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            pointer-events: none;
            z-index: 1;
            opacity: 0.35;
            filter: drop-shadow(0 0 25px rgba(0, 120, 215, 0.7));
        }

        .element { position: absolute; background: #ffffff; border: 2px solid #555; border-radius: 8px; padding: 4px; width: 95px; height: 95px; display: flex; flex-direction: column; align-items: center; justify-content: space-between; font-size: 9px; font-weight: bold; cursor: move; box-shadow: 4px 8px 16px rgba(0,0,0,0.4); z-index: 10; overflow: hidden; }
        
        .element-img-wrap {
            width: 32px;
            height: 32px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            border-radius: 4px;
        }
        
        .el-icon { font-size: 22px; }
        .el-time { font-size: 8.5px; color: #ff3366; font-weight: bold; text-align: center; width: 100%; white-space: nowrap; overflow: hidden; }
        .el-name { text-align: center; width: 100%; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
        
        .ismail-kuru { background: linear-gradient(to bottom, #ff8c00 35%, #111 35%) !important; color: white !important; border-color: #000 !important; }
        .ismail-lityum { background: #eeeeee !important; color: #111 !important; border: 3px solid #999 !important; border-radius: 4px !important; }
        .gold-bar { background: linear-gradient(135deg, #ffe066, #f5b041) !important; color: #784212 !important; border-color: #b7950b !important; }
        .silver-bar { background: linear-gradient(135deg, #ffffff, #bdc3c7) !important; color: #2c3e50 !important; border-color: #7f8c8d !important; }
        .copper-bar { background: linear-gradient(135deg, #f5b041, #dc7633) !important; color: #6e2c00 !important; border-color: #a04000 !important; }
        
        .res-stripes { width: 100%; height: 5px; display: flex; border-radius: 2px; overflow: hidden; margin-top: 1px; }
        .r-low { background: #58d68d; } .r-mid { background: #f5b041; } .r-high { background: #ec7063; }

        .burnt { background: #222222 !important; color: #ff4444 !important; border-color: #ff0000 !important; }

        /* 🔌 PİNLER */
        .node { position: absolute; bottom: 4px; width: 16px; height: 16px; border-radius: 50%; border: 2px solid #fff; z-index: 20; cursor: pointer; }
        .node-left { left: 8px; background: #ff3366; } 
        .node-right { right: 8px; background: #333945; } 
        .node.selected { background: #00a4ef !important; box-shadow: 0 0 12px #00a4ef; }

        /* 〰️ KABLOLAR */
        svg { position: absolute; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; z-index: 5; }
        .wire { stroke: #0078d7; stroke-width: 5px; fill: none; stroke-linecap: round; }
        .wire-burnt { stroke: #444444 !important; stroke-dasharray: 4; animation: melt 0.4s forwards; }
        @keyframes melt { 100% { opacity: 0; stroke-width: 0; } }

        .electron { fill: #fff300; r: 3.5; }
        .glow { filter: drop-shadow(0 0 15px #ffeb3b); color: #fbc02d !important; }
        .glow-dim { filter: drop-shadow(0 0 6px #ffb300); color: #f57c00 !important; }
    </style>
</head>
<body>

<div id="splash-screen">
    <div class="animation-container">
        <div class="glow-orb orb-red"></div>
        <div class="glow-orb orb-green"></div>
        <div class="glow-orb orb-blue"></div>
        <div class="glow-orb orb-yellow"></div>
    </div>
    
    <div class="brand-wrapper">
        <div class="brand-cube-grid">
            <div class="brand-cube"><img src="resim1.png" alt="" onerror="this.style.display='none';"></div>
            <div class="brand-cube"><img src="resim2.png" alt="" onerror="this.style.display='none';"></div>
            <div class="brand-cube"><img src="resim3.png" alt="" onerror="this.style.display='none';"></div>
            <div class="brand-cube"><img src="resim4.png" alt="" onerror="this.style.display='none';"></div>
        </div>
        <div class="brand-text-bottom">İSMAİL BARUĞ</div>
    </div>
</div>

<header>
    <h1>⚡ ELECTRO İS LAB - FULL RESİMLİ PARÇALAR V18.8 ⚡</h1>
    <div id="status-bar">Maddeleri ve pilleri bağla, kabloların içindeki akan elektronları izle!</div>
</header>

<div id="main-container">
    <div class="menu-sidebar">
        <button onclick="spawn('ismail_kuru')" style="background:#ffe5cc;">🔋 İsmail Kuru Pil</button>
        <button onclick="spawn('ismail_lityum')" style="background:#f2f2f2;">⚡ İsmail Lityum Pil</button>
        <button onclick="spawn('ampul')">💡 Flamanlı Ampul</button>
        <button onclick="spawn('sigorta')" style="background:#e6f2ff;">🧬 Cam Sigorta</button>
        <button onclick="spawn('switch')">🎛️ Çıtçıt Anahtar</button>
        <button onclick="spawn('r_low')">🔵 Düşük Direnç</button>
        <button onclick="spawn('r_mid')">🟡 Orta Direnç</button>
        <button onclick="spawn('r_high')">🔴 Yüksek Direnç</button>
        <button onclick="spawn('gold')">🪙 Altın Külçe</button>
        <button onclick="silver_bar_spawn('silver')">🥈 Gümüş Külçe</button>
        <button onclick="copper_bar_spawn('copper')">🟫 Bakır Külçe</button>
        <button onclick="reset()" class="btn-reset">🗑️ Sıfırla</button>
    </div>

    <div id="workspace">
        <div class="workspace-background-logo">
            <div class="brand-cube-grid">
                <div class="brand-cube"><img src="resim1.png" alt="" onerror="this.style.display='none';"></div>
                <div class="brand-cube"><img src="resim2.png" alt="" onerror="this.style.display='none';"></div>
                <div class="brand-cube"><img src="resim3.png" alt="" onerror="this.style.display='none';"></div>
                <div class="brand-cube"><img src="resim4.png" alt="" onerror="this.style.display='none';"></div>
            </div>
            <div class="brand-text-bottom" style="font-size:26px;">İSMAİL BARUĞ</div>
        </div>
        
        <svg id="wires"></svg>
    </div>
</div>

<script>
    setTimeout(() => document.getElementById('splash-screen').style.display = 'none', 3500);
    
    let elements = []; let connections = []; let selectedNode = null;
    let shortCircuitTimer = null; let animationFrameId = null;
    let countdown = 5; let isSystemBurnt = false; let electronOffset = 0;

    function spawn(type) {
        let id = 'el_' + Date.now();
        let el = document.createElement('div');
        el.className = 'element'; el.id = id;
        
        let icon = "🔋"; let name = "İSMAİL KURU"; let extra = "1.5V (10s)";
        let imgName = "pil.png"; 

        if(type === 'ismail_kuru') { el.classList.add('ismail-kuru'); imgName = "pil_kuru.png"; }
        if(type === 'ismail_lityum') { icon = "⚡"; name = "İSMAİL LİTYUM"; extra = "3.6V (20s)"; el.classList.add('ismail-lityum'); imgName = "pil_lityum.png"; }
        if(type === 'ampul') { icon = "💡"; name = "AMPUL"; extra = ""; imgName = "ampul.png"; }
        if(type === 'sigorta') { icon = "🧬"; name = "CAM SİGORTA"; extra = "Tel Sağlam"; imgName = "sigorta.png"; }
        if(type === 'switch') { icon = "🎛️"; name = "ANAHTAR"; extra = "KAPALI (O)"; el.setAttribute('onclick', `toggleSwitch('${id}')`); imgName = "anahtar.png"; }
        if(type === 'r_low') { icon = "🧬"; name = "DÜŞÜK DİRENÇ"; extra = "10 Ohm"; imgName = "direnc_low.png"; }
        if(type === 'r_mid') { icon = "🧬"; name = "ORTA DİRENÇ"; extra = "50 Ohm"; imgName = "direnc_mid.png"; }
        if(type === 'r_high') { icon = "🧬"; name = "YÜKSEK DİRENÇ"; extra = "200 Ohm"; imgName = "direnc_high.png"; }
        if(type === 'gold') { icon = "🪙"; name = "ALTIN KÜLÇE"; extra = "Süper İletken"; el.classList.add('gold-bar'); imgName = "altin.png"; }
        if(type === 'silver') { icon = "🥈"; name = "GÜMÜŞ KÜLÇE"; extra = "Çok İletken"; el.classList.add('silver-bar'); imgName = "gumus.png"; }
        if(type === 'copper') { icon = "🟫"; name = "BAKIR KÜLÇE"; extra = "İletken"; el.classList.add('copper-bar'); imgName = "bakir.png"; }

        el.innerHTML = `
            <div class="element-img-wrap">
                <img src="${imgName}" alt="" onerror="this.style.display='none';">
                <div class="el-icon" id="icon_${id}">${icon}</div>
            </div>
            <div class="el-name" id="name_${id}">${name}</div>
            <div id="extra_${id}" class="el-time">${extra}</div>
            <div class="node node-left" onclick="event.stopPropagation(); select(this, '${id}', 'left')"></div>
            <div class="node node-right" onclick="event.stopPropagation(); select(this, '${id}', 'right')"></div>
        `;
        
        if(type.startsWith('r_')) {
            let stripeDiv = document.createElement('div');
            stripeDiv.className = `res-stripes ${type}`;
            el.appendChild(stripeDiv);
        }

        el.style.left = '70px'; el.style.top = '70px';
        document.getElementById('workspace').appendChild(el);
        
        elements.push({ id, type, burnt: false, state: false, time: (type === 'ismail_kuru' ? 10 : (type === 'ismail_lityum' ? 20 : 0)) });

        el.ontouchmove = (e) => {
            let ws = document.getElementById('workspace').getBoundingClientRect();
            el.style.left = (e.touches[0].clientX - ws.left - 45) + 'px';
            el.style.top = (e.touches[0].clientY - ws.top - 45) + 'px';
            draw();
        };
    }

    function select(node, id, side) {
        if (isSystemBurnt) return;
        if (!selectedNode) {
            selectedNode = { node, id, side };
            node.classList.add('selected');
        } else {
            if(selectedNode.id !== id) {
                connections.push([selectedNode, { node, id, side }]);
                selectedNode.node.classList.remove('selected');
                selectedNode = null;
                draw();
                checkCircuit();
            } else {
                selectedNode.node.classList.remove('selected');
                selectedNode = null;
            }
        }
    }

    function toggleSwitch(id) {
        let sw = elements.find(e => e.id === id);
        if(!sw || sw.burnt) return;
        sw.state = !sw.state;
        document.getElementById('extra_' + id).innerText = sw.state ? "AÇIK (I)" : "KAPALI (O)";
        checkCircuit();
    }

    function draw() {
        let svg = document.getElementById('wires');
        svg.innerHTML = '';
        connections.forEach(c => {
            let p1 = c[0].node.getBoundingClientRect();
            let p2 = c[1].node.getBoundingClientRect();
            let ws = document.getElementById('workspace').getBoundingClientRect();
            
            let x1 = p1.left - ws.left + 8; let y1 = p1.top - ws.top + 8;
            let x2 = p2.left - ws.left + 8; let y2 = p2.top - ws.top + 8;

            let line = document.createElementNS('http://www.w3.org/2000/svg', 'line');
            line.setAttribute('x1', x1); line.setAttribute('y1', y1);
            line.setAttribute('x2', x2); line.setAttribute('y2', y2);
            line.setAttribute('class', 'wire' + (isSystemBurnt ? ' wire-burnt' : ''));
            svg.appendChild(line);
        });
    }

    function animateElectrons() {
        if (isSystemBurnt) return;
        let svg = document.getElementById('wires');
        document.querySelectorAll('.electron').forEach(e => e.remove());

        let hasAmpulGlow = elements.some(e => e.type === 'ampul' && document.getElementById('icon_' + e.id).classList.contains('glow'));
        let isShort = shortCircuitTimer !== null;

        if (hasAmpulGlow || isShort) {
            electronOffset += isShort ? 1.5 : 0.4;
            connections.forEach(c => {
                let p1 = c[0].node.getBoundingClientRect();
                let p2 = c[1].node.getBoundingClientRect();
                let ws = document.getElementById('workspace').getBoundingClientRect();
                let x1 = p1.left - ws.left + 8; let y1 = p1.top - ws.top + 8;
                let x2 = p2.left - ws.left + 8; let y2 = p2.top - ws.top + 8;

                let len = Math.hypot(x2 - x1, y2 - y1);
                let dots = Math.floor(len / 25);
                for (let i = 0; i < dots; i++) {
                    let t = ((i * 25 + electronOffset) % len) / len;
                    let cx = x1 + (x2 - x1) * t;
                    let cy = y1 + (y2 - y1) * t;

                    let circle = document.createElementNS('http://www.w3.org/2000/svg', 'circle');
                    circle.setAttribute('cx', cx); circle.setAttribute('cy', cy);
                    circle.setAttribute('class', 'electron');
                    svg.appendChild(circle);
                }
            });
        }
        animationFrameId = requestAnimationFrame(animateElectrons);
    }

    function checkCircuit() {
        if (connections.length < 2) { setAmpulState('off'); stopTimer(); return; }

        let activePils = elements.filter(e => (e.type === 'ismail_kuru' || e.type === 'ismail_lityum') && !e.burnt);
        let hasAmpul = elements.some(e => e.type === 'ampul' && !e.burnt);
        let fuse = elements.find(e => e.type === 'sigorta');
        let switches = elements.filter(e => e.type === 'switch');
        
        if(switches.length > 0 && switches.some(s => !s.state)) {
            setAmpulState('off'); document.getElementById('status-bar').innerText = "🎛️ Anahtar kapalı, elektron akışı durduruldu.";
            stopTimer(); return;
        }

        if (activePils.length === 0) return;

        let hasHighRes = elements.some(e => e.type === 'r_high');
        let hasMidRes = elements.some(e => e.type === 'r_mid');
        let isShortCircuit = !hasAmpul && !hasHighRes && !hasMidRes;

        if (hasAmpul) {
            if (hasHighRes) {
                document.getElementById('status-bar').innerText = "🔴 Yüksek direnç bağlandı. Elektronlar yavaş, ampul loş yanyor.";
                setAmpulState('dim'); stopTimer();
            } else {
                document.getElementById('status-bar').innerText = "🟢 Devre tamamlandı! Elektronlar akıyor, flamanlı ampul ışık saçıyor!";
                setAmpulState('full'); stopTimer();
            }
            if(!animationFrameId) animateElectrons();
        } else if (isShortCircuit) {
            setAmpulState('off');
            if (fuse && !fuse.burnt) triggerFuseBlow(); else triggerShortCircuit();
        }
    }

    function triggerShortCircuit() {
        if (shortCircuitTimer) return;
        if(!animationFrameId) animateElectrons();
        countdown = 5;
        shortCircuitTimer = setInterval(() => {
            countdown--;
            if (countdown > 0) {
                document.getElementById('status-bar').innerText = `🔥 KISA DEVRE! Elektronlar çıldırdı! Piller ${countdown}s içinde PATLAYACAK!`;
            } else {
                clearInterval(shortCircuitTimer);
                explodeSystem();
            }
        }, 1000);
    }

    function triggerFuseBlow() {
        let fuse = elements.find(e => e.type === 'sigorta');
        if(!fuse) return;
        fuse.burnt = true;
        isSystemBurnt = true;
        stopTimer();
        document.getElementById('status-bar').innerText = "💥 ÇAAAT!!! Cam sigortanın içindeki ince tel koptu ve simsiyah oldu! Piller kurtarıldı!";
        document.getElementById(fuse.id).classList.add('burnt');
        document.getElementById('icon_' + fuse.id).innerText = "✖️";
        document.getElementById('extra_' + fuse.id).innerText = "TEL KOPTU (BURNT)";
        burnWires();
    }

    function explodeSystem() {
        isSystemBurnt = true;
        document.getElementById('status-bar').innerText = "💥 GÜÜÜM!!! Sigorta olmadığı için piller ve tüm devre infilak etti!";
        elements.forEach(e => {
            if (e.type === 'ismail_kuru' || e.type === 'ismail_lityum') {
                e.burnt = true;
                document.getElementById(e.id).classList.add('burnt');
                document.getElementById('icon_' + e.id).innerText = "💥";
                document.getElementById('extra_' + e.id).innerText = "PATLADI";
            }
        });
        burnWires();
    }

    function burnWires() {
        cancelAnimationFrame(animationFrameId); animationFrameId = null;
        document.querySelectorAll('.wire').forEach(w => w.classList.add('wire-burnt'));
        setTimeout(() => { connections = []; draw(); }, 400);
    }

    function setAmpulState(state) {
        elements.forEach(e => {
            if (e.type === 'ampul') {
                let icon = document.getElementById('icon_' + e.id);
                if (state === 'full') icon.className = "el-icon glow";
                else if (state === 'dim') icon.className = "el-icon glow-dim";
                else icon.className = "el-icon";
            }
        });
    }

    function stopTimer() { if (shortCircuitTimer) { clearInterval(shortCircuitTimer); shortCircuitTimer = null; } }
    function reset() { location.reload(); }
    function copper_bar_spawn(t) { spawn(t); }
    function silver_bar_spawn(t) { spawn(t); }
</script>
</body>
</html>
