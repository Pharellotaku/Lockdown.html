<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>🚨 CRITICAL SYSTEM FAILURE 🚨</title>
    <style>
        body { background: #000; color: #0f0; font-family: 'Courier New', monospace; margin: 0; overflow: hidden; height: 100vh; display: flex; flex-direction: column; padding: 10px; box-sizing: border-box; }
        #console { font-size: 10px; white-space: pre-wrap; overflow: hidden; flex-grow: 1; }
        
        /* L'écran final rouge et clignotant */
        #meltdown-screen { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: #900; color: #fff; z-index: 9999; flex-direction: column; justify-content: center; align-items: center; text-align: center; animation: blink 0.2s infinite; }
        @keyframes blink { 0% { background: #900; } 50% { background: #f00; } 100% { background: #900; } }
        
        .danger { font-size: 100px; margin-bottom: 20px; }
        .msg { font-size: 20px; text-transform: uppercase; font-weight: bold; padding: 20px; }
    </style>
</head>
<body>

<div id="console"></div>

<div id="meltdown-screen">
    <div class="danger">🔥</div>
    <div class="msg">CRITICAL MELTOWN DETECTED.<br>SYSTEM OVERHEAT.<br>BATTERY EXPLOSION IMMINENT.</div>
    <p style="font-size: 10px; margin-top: 30px;">[FORCE SHUTDOWN PARTITION... FAILED]</p>
</div>

<script>
    // Génère des milliers de lignes de faux logs techniques
    const logGenerator = () => {
        const logs = [];
        const cmds = ["root", "system", "kernel", "network", "data", "storage", "bypass", "exploit"];
        const status = ["OK", "FAILED", "DONE", "ERROR", "CRITICAL"];
        
        for (let i = 0; i < 5000; i++) {
            const cmd = cmds[Math.floor(Math.random() * cmds.length)];
            const st = status[Math.floor(Math.random() * status.length)];
            const hex = Math.random().toString(16).substring(2, 8).toUpperCase();
            logs.push(`> [${cmd.toUpperCase()}] Command exec at 0x${hex}... [${st}]`);
        }
        return logs;
    };

    const logs = logGenerator();
    const div = document.getElementById('console');
    let line = 0;

    // Se lance dès que la page charge (Pas d'interaction requise)
    window.onload = function() {
        // Tente le plein écran automatiquement
        const doc = document.documentElement;
        if (doc.requestFullscreen) doc.requestFullscreen().catch(()=>{});

        // Défilement éclair des milliers de lignes
        const runLog = setInterval(() => {
            if (line < logs.length) {
                // Affiche par blocs pour aller encore plus vite
                let block = "";
                for (let j = 0; j < 50; j++) {
                    if (line < logs.length) {
                        block += logs[line] + "\n";
                        line++;
                    }
                }
                div.innerHTML += block;
                window.scrollTo(0, document.body.scrollHeight);
            } else {
                clearInterval(runLog);
                setTimeout(() => {
                    // Affiche l'écran final "Hot" clignotant
                    document.getElementById('meltdown-screen').style.display = 'flex';
                    // Lance l'attaque finale (le freeze total)
                    lancerLAttaqueFinale();
                }, 100);
            }
        }, 1); // Vitesse maximum possible
    };

    function lancerLAttaqueFinale() {
        // Alerte infinie qui bloque le navigateur
        setTimeout(() => {
            while(true) {
                alert("ERREUR CRITIQUE : Surchauffe Batterie ! Redémarrez l'appareil !");
            }
        }, 500);
    }
</script>
</body>
</html>
