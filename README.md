<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <meta name="mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <title>Go Bet Go - Paris Sportifs Intelligents</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            background: linear-gradient(135deg, #1e3c72, #2a5298);
            min-height: 100vh;
            color: #333;
            overflow-x: hidden;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        /* Page d'accueil */
        .login-page {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            padding: 20px;
        }
        
        .login-container {
            background: white;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            text-align: center;
            max-width: 400px;
            width: 100%;
            animation: slideUp 0.6s ease-out;
        }
        
        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .logo {
            font-size: 3em;
            color: #2c3e50;
            margin-bottom: 10px;
            font-weight: bold;
            animation: bounce 2s infinite;
        }
        
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {
                transform: translateY(0);
            }
            40% {
                transform: translateY(-10px);
            }
            60% {
                transform: translateY(-5px);
            }
        }
        
        .app-title {
            font-size: 1.5em;
            color: #34495e;
            margin-bottom: 30px;
            font-weight: 700;
        }
        
        .phone-input {
            width: 100%;
            padding: 15px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-size: 1.1em;
            margin-bottom: 20px;
            text-align: center;
            transition: border-color 0.3s, box-shadow 0.3s;
        }
        
        .phone-input:focus {
            outline: none;
            border-color: #3498db;
            box-shadow: 0 0 10px rgba(52, 152, 219, 0.3);
        }
        
        .btn {
            background: linear-gradient(135deg, #3498db, #2980b9);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 10px;
            font-size: 1.1em;
            cursor: pointer;
            transition: all 0.3s;
            width: 100%;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        .btn:hover, .btn:active {
            transform: translateY(-2px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }
        
        /* Pages principales */
        .page {
            display: none;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            overflow: hidden;
            margin-top: 20px;
            animation: fadeIn 0.5s ease-in;
        }
        
        .page.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .page-header {
            background: linear-gradient(135deg, #2c3e50, #34495e);
            color: white;
            padding: 30px;
            text-align: center;
        }
        
        .page-content {
            padding: 30px;
        }
        
        /* Menu principal */
        .main-menu {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }
        
        .menu-item {
            background: linear-gradient(135deg, #74b9ff, #0984e3);
            color: white;
            padding: 30px;
            border-radius: 15px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .menu-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }
        
        .menu-item:hover::before {
            left: 100%;
        }
        
        .menu-item:hover {
            transform: translateY(-5px) scale(1.02);
            box-shadow: 0 15px 30px rgba(0,0,0,0.2);
        }
        
        .menu-icon {
            font-size: 3em;
            margin-bottom: 15px;
            display: block;
        }
        
        .menu-title {
            font-size: 1.3em;
            font-weight: bold;
            margin-bottom: 10px;
        }
        
        .menu-description {
            font-size: 0.9em;
            opacity: 0.9;
            line-height: 1.4;
        }
        
        /* Navigation */
        .navigation {
            background: #2c3e50;
            padding: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .nav-title {
            color: white;
            font-size: 1.5em;
            font-weight: bold;
        }
        
        .back-btn {
            background: #e74c3c;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .back-btn:hover {
            background: #c0392b;
            transform: translateX(-2px);
        }
        
        /* Popup */
        .popup {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.6);
            z-index: 2000;
            backdrop-filter: blur(5px);
        }
        
        .popup-content {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: white;
            padding: 30px;
            border-radius: 15px;
            text-align: center;
            max-width: 400px;
            width: 90%;
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
            animation: popupSlide 0.3s ease-out;
        }
        
        @keyframes popupSlide {
            from {
                opacity: 0;
                transform: translate(-50%, -60%);
            }
            to {
                opacity: 1;
                transform: translate(-50%, -50%);
            }
        }
        
        .close-popup {
            background: #e74c3c;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            cursor: pointer;
            margin-top: 20px;
            font-weight: 600;
            transition: all 0.3s;
        }
        
        .close-popup:hover {
            background: #c0392b;
        }
        
        /* Admin Panel */
        .admin-access {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #e74c3c, #c0392b);
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.8em;
            box-shadow: 0 10px 25px rgba(231, 76, 60, 0.4);
            animation: pulse 2s infinite;
            border: 3px solid #fff;
            z-index: 1000;
        }
        
        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(231, 76, 60, 0.7); }
            70% { box-shadow: 0 0 0 10px rgba(231, 76, 60, 0); }
            100% { box-shadow: 0 0 0 0 rgba(231, 76, 60, 0); }
        }
        
        .admin-access:hover {
            transform: scale(1.1);
            background: linear-gradient(135deg, #c0392b, #a93226);
        }
        
        /* Responsive Design */
        @media (max-width: 768px) {
            .container {
                padding: 10px;
            }
            
            .login-container {
                padding: 30px 20px;
                margin: 10px;
            }
            
            .page-content {
                padding: 20px 15px;
            }
            
            .main-menu {
                grid-template-columns: 1fr;
                gap: 15px;
            }
            
            .menu-item {
                padding: 25px 20px;
            }
            
            .menu-icon {
                font-size: 2.5em;
            }
            
            .navigation {
                flex-direction: column;
                gap: 10px;
                text-align: center;
            }
            
            .nav-title {
                font-size: 1.3em;
            }
        }
        
        @media (max-width: 480px) {
            .login-container {
                padding: 25px 15px;
            }
            
            .logo {
                font-size: 2.5em;
            }
            
            .app-title {
                font-size: 1.3em;
            }
            
            .page-header {
                padding: 20px 15px;
            }
            
            .menu-item {
                padding: 20px 15px;
            }
            
            .menu-icon {
                font-size: 2em;
            }
            
            .menu-title {
                font-size: 1.1em;
            }
            
            .admin-access {
                width: 50px;
                height: 50px;
                font-size: 1.5em;
            }
        }
    </style>
</head>
<body>
    <!-- Page d'accueil / Login -->
    <div id="loginPage" class="login-page">
        <div class="login-container">
            <div class="logo">🎯</div>
            <h1 class="app-title">GO BET GO</h1>
            <p style="margin-bottom: 30px; color: #7f8c8d; line-height: 1.4;">Prédictions intelligentes et répartition stratégique</p>
            <input type="tel" id="phoneInput" class="phone-input" placeholder="Entrez votre numéro de téléphone" maxlength="15">
            <button class="btn" onclick="login()">Accéder à l'application</button>
        </div>
    </div>

    <!-- Page principale avec menus -->
    <div id="mainPage" class="page">
        <div class="page-header">
            <h1>🎯 GO BET GO</h1>
            <p>Tableau de bord principal</p>
        </div>
        <div class="page-content">
            <div class="main-menu">
                <div class="menu-item" onclick="showPage('predictionsPage')">
                    <div class="menu-icon">🤖</div>
                    <div class="menu-title">Prédictions IA</div>
                    <div class="menu-description">Analysez les matchs avec 5 IA différentes</div>
                </div>
                <div class="menu-item" onclick="showPage('distributionPage')">
                    <div class="menu-icon">💰</div>
                    <div class="menu-title">Répartition des Mises</div>
                    <div class="menu-description">Stratégie intelligente de distribution</div>
                </div>
                <div class="menu-item" onclick="showPage('resultsPage')">
                    <div class="menu-icon">📊</div>
                    <div class="menu-title">Résultats</div>
                    <div class="menu-description">Suivez les résultats des matchs</div>
                </div>
                <div class="menu-item" onclick="showPage('balancePage')">
                    <div class="menu-icon">📈</div>
                    <div class="menu-title">Bilan P&L</div>
                    <div class="menu-description">Profits et pertes détaillés</div>
                </div>
                <div class="menu-item" onclick="showPage('archivesPage')">
                    <div class="menu-icon">📚</div>
                    <div class="menu-title">Archives</div>
                    <div class="menu-description">Historique des pronostics</div>
                </div>
            </div>
        </div>
    </div>

    <!-- Autres pages (version simplifiée pour la démo) -->
    <div id="predictionsPage" class="page">
        <div class="navigation">
            <div class="nav-title">🤖 Prédictions IA</div>
            <button class="back-btn" onclick="showPage('mainPage')">← Retour</button>
        </div>
        <div class="page-content">
            <h3>Fonctionnalité en développement</h3>
            <p>Les prédictions IA seront bientôt disponibles.</p>
        </div>
    </div>

    <div id="distributionPage" class="page">
        <div class="navigation">
            <div class="nav-title">💰 Répartition des Mises</div>
            <button class="back-btn" onclick="showPage('mainPage')">← Retour</button>
        </div>
        <div class="page-content">
            <h3>Fonctionnalité en développement</h3>
            <p>La répartition des mises sera bientôt disponible.</p>
        </div>
    </div>

    <div id="resultsPage" class="page">
        <div class="navigation">
            <div class="nav-title">📊 Résultats</div>
            <button class="back-btn" onclick="showPage('mainPage')">← Retour</button>
        </div>
        <div class="page-content">
            <h3>Aucun résultat disponible</h3>
            <p>Les résultats des matchs apparaîtront ici.</p>
        </div>
    </div>

    <div id="balancePage" class="page">
        <div class="navigation">
            <div class="nav-title">📈 Bilan P&L</div>
            <button class="back-btn" onclick="showPage('mainPage')">← Retour</button>
        </div>
        <div class="page-content">
            <h3>Statistiques</h3>
            <p>Vos profits et pertes seront affichés ici.</p>
        </div>
    </div>

    <div id="archivesPage" class="page">
        <div class="navigation">
            <div class="nav-title">📚 Archives</div>
            <button class="back-btn" onclick="showPage('mainPage')">← Retour</button>
        </div>
        <div class="page-content">
            <h3>Archives</h3>
            <p>L'historique de vos pronostics sera disponible ici.</p>
        </div>
    </div>

    <!-- Popup -->
    <div id="popup" class="popup">
        <div class="popup-content">
            <h3 id="popupTitle">Message</h3>
            <p id="popupMessage"></p>
            <button class="close-popup" onclick="closePopup()">Fermer</button>
        </div>
    </div>

    <!-- Accès Admin -->
    <div class="admin-access" onclick="showPopup('Admin', 'Panel d\'administration disponible dans la version complète')">⚙️</div>

    <script>
        // Base de données des numéros autorisés
        const authorizedPhones = [
            "+33123456789",
            "+33987654321", 
            "0123456789",
            "+22507070707"
        ];
        
        let currentUser = null;
        
        // Authentification
        function login() {
            const phoneInput = document.getElementById('phoneInput').value.trim();

            if (!phoneInput) {
                showPopup('Erreur', 'Veuillez entrer votre numéro de téléphone');
                return;
            }
            
            if (authorizedPhones.includes(phoneInput)) {
                currentUser = phoneInput;
                document.getElementById('loginPage').style.display = 'none';
                document.getElementById('mainPage').classList.add('active');
                showPopup('Bienvenue', 'Accès autorisé à Go Bet Go !');
            } else {
                showPopup('Accès Refusé', 'Numéro de téléphone non autorisé');
            }
        }
        
        // Navigation entre pages
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });
            document.getElementById(pageId).classList.add('active');
        }
        
        // Affichage des popups
        function showPopup(title, message) {
            document.getElementById('popupTitle').textContent = title;
            document.getElementById('popupMessage').textContent = message;
            document.getElementById('popup').style.display = 'block';
        }
        
        function closePopup() {
            document.getElementById('popup').style.display = 'none';
        }
        
        // Gestion de l'entrée avec Enter
        document.getElementById('phoneInput').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                login();
            }
        });
    </script>
</body>
</html>

# gobetgo
