# ESO-learning-1
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>English ESO Learning Platform</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            height: 100vh;
            overflow: hidden;
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: #333;
        }

        #login-page {
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .login-container {
            background: white;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            width: 400px;
            max-width: 90%;
            padding: 40px;
            text-align: center;
        }

        .login-container h1 {
            color: #1e3c72;
            margin-bottom: 10px;
            font-size: 28px;
        }

        .login-container p {
            color: #666;
            margin-bottom: 30px;
        }

        .input-group {
            margin-bottom: 20px;
            text-align: left;
        }

        .input-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: #444;
        }

        .input-group input {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 16px;
            transition: border-color 0.3s;
        }

        .input-group input:focus {
            border-color: #2a5298;
            outline: none;
        }

        .login-btn {
            background: #1e3c72;
            color: white;
            border: none;
            padding: 14px 20px;
            width: 100%;
            border-radius: 6px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.3s;
        }

        .login-btn:hover {
            background: #2a5298;
        }

        .login-options {
            margin-top: 25px;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .social-login {
            display: flex;
            justify-content: center;
            gap: 15px;
        }

        .social-btn {
            padding: 12px;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            border: 1px solid #ddd;
            background: white;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .social-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        #main-app {
            height: 100vh;
            display: none;
            flex-direction: column;
        }

        .app-header {
            background: white;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            padding: 15px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .app-header h1 {
            color: #1e3c72;
            font-size: 24px;
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .user-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: #1e3c72;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
        }

        .logout-btn {
            background: #f0f4f8;
            border: none;
            padding: 8px 15px;
            border-radius: 6px;
            cursor: pointer;
            color: #666;
            transition: background 0.3s;
        }

        .logout-btn:hover {
            background: #e0e7f1;
        }

        .app-content {
            display: flex;
            flex: 1;
            overflow: hidden;
        }

        .sidebar {
            width: 250px;
            background: #2a5298;
            color: white;
            padding: 30px 0;
        }

        .nav-item {
            padding: 15px 30px;
            cursor: pointer;
            transition: background 0.3s;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .nav-item:hover {
            background: #3a63b0;
        }

        .nav-item.active {
            background: #1e3c72;
            border-left: 4px solid white;
        }

        .content-area {
            flex: 1;
            padding: 30px;
            overflow-y: auto;
            background: #f0f4f8;
        }

        .section {
            display: none;
        }

        .section.active {
            display: block;
            animation: fadeIn 0.5s;
        }

        .section h2 {
            color: #1e3c72;
            margin-bottom: 20px;
            font-size: 28px;
        }

        .section p {
            color: #555;
            line-height: 1.6;
            margin-bottom: 20px;
        }

        .exercise-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .exercise-card {
            background: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.08);
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .exercise-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.12);
        }

        .exercise-card h3 {
            color: #1e3c72;
            margin-bottom: 10px;
        }

        .exercise-card p {
            color: #666;
            margin-bottom: 15px;
        }

        .start-btn {
            background: #1e3c72;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 14px;
            transition: background 0.3s;
        }

        .start-btn:hover {
            background: #2a5298;
        }

        .progress-container {
            background: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.08);
            margin-bottom: 25px;
        }

        .progress-bar {
            height: 10px;
            background: #e0e7f1;
            border-radius: 5px;
            margin: 15px 0;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background: #1e3c72;
            border-radius: 5px;
            width: 0%;
            transition: width 1s ease-in-out;
        }

        .resource-list {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .resource-item {
            background: white;
            border-radius: 8px;
            padding: 15px;
            display: flex;
            align-items: center;
            gap: 15px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
            transition: transform 0.3s;
        }

        .resource-item:hover {
            transform: translateX(5px);
        }

        .resource-icon {
            width: 40px;
            height: 40px;
            background: #1e3c72;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 20px;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @media (max-width: 768px) {
            .app-content {
                flex-direction: column;
            }
            
            .sidebar {
                width: 100%;
                padding: 15px 0;
            }
            
            .nav-item {
                padding: 12px 20px;
            }
            
            .exercise-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Página de inicio de sesión -->
    <div id="login-page">
        <div class="login-container">
            <h1>English ESO Learning</h1>
            <p>Inicia sesión para acceder a los recursos de aprendizaje</p>
            
            <div class="input-group">
                <label for="email">Correo electrónico</label>
                <input type="email" id="email" placeholder="tu@email.com">
            </div>
            
            <div class="input-group">
                <label for="password">Contraseña</label>
                <input type="password" id="password" placeholder="Tu contraseña">
            </div>
            
            <button class="login-btn" onclick="login()">Iniciar Sesión</button>
            
            <div class="login-options">
                <p>o inicia sesión con</p>
                <div class="social-login">
                    <div class="social-btn">G</div>
                    <div class="social-btn">F</div>
                    <div class="social-btn">M</div>
                </div>
            </div>
        </div>
    </div>

    <!-- Aplicación principal (oculta inicialmente) -->
    <div id="main-app">
        <header class="app-header">
            <h1>English ESO Learning</h1>
            <div class="user-info">
                <div class="user-avatar">A</div>
                <span id="username">Usuario</span>
                <button class="logout-btn" onclick="logout()">Cerrar Sesión</button>
            </div>
        </header>
        
        <div class="app-content">
            <nav class="sidebar">
                <div class="nav-item active" data-section="lessons">
                    <span>📚</span> Lecciones
                </div>
                <div class="nav-item" data-section="exercises">
                    <span>✏️</span> Ejercicios
                </div>
                <div class="nav-item" data-section="progress">
                    <span>📊</span> Progreso
                </div>
                <div class="nav-item" data-section="resources">
                    <span>🔗</span> Recursos
                </div>
            </nav>
            
            <main class="content-area">
                <!-- Sección de Lecciones -->
                <section id="lessons" class="section active">
                    <h2>Lecciones de Inglés</h2>
                    <p>Explora nuestras lecciones organizadas por nivel de dificultad y temas gramaticales.</p>
                    
                    <div class="exercise-grid">
                        <div class="exercise-card">
                            <h3>Present Simple</h3>
                            <p>Aprende a usar el presente simple en contextos cotidianos.</p>
                            <button class="start-btn">Comenzar Lección</button>
                        </div>
                        
                        <div class="exercise-card">
                            <h3>Past Continuous</h3>
                            <p>Domina el uso del pasado continuo con ejemplos prácticos.</p>
                            <button class="start-btn">Comenzar Lección</button>
                        </div>
                        
                        <div class="exercise-card">
                            <h3>Future Tenses</h3>
                            <p>Aprende a diferenciar entre will, going to y present continuous.</p>
                            <button class="start-btn">Comenzar Lección</button>
                        </div>
                        
                        <div class="exercise-card">
                            <h3>Conditionals</h3>
                            <p>Domina los condicionales de tipo 0, 1, 2 y 3.</p>
                            <button class="start-btn">Comenzar Lección</button>
                        </div>
                    </div>
                </section>
                
                <!-- Sección de Ejercicios -->
                <section id="exercises" class="section">
                    <h2>Ejercicios de Práctica</h2>
                    <p>Practica lo aprendido con nuestros ejercicios interactivos.</p>
                    
                    <div class="exercise-grid">
                        <div class="exercise-card">
                            <h3>Present Simple Exercise</h3>
                            <p>Completa las oraciones con la forma correcta del verbo.</p>
                            <button class="start-btn">Comenzar Ejercicio</button>
                        </div>
                        
                        <div class="exercise-card">
                            <h3>Vocabulary Quiz</h3>
                            <p>Pon a prueba tu vocabulario con este cuestionario.</p>
                            <button class="start-btn">Comenzar Ejercicio</button>
                        </div>
                        
                        <div class="exercise-card">
                            <h3>Listening Comprehension</h3>
                            <p>Escucha el audio y responde a las preguntas.</p>
                            <button class="start-btn">Comenzar Ejercicio</button>
                        </div>
                        
                        <div class="exercise-card">
                            <h3>Reading Exercise</h3>
                            <p>Lee el texto y responde a las preguntas de comprensión.</p>
                            <button class="start-btn">Comenzar Ejercicio</button>
                        </div>
                    </div>
                </section>
                
                <!-- Sección de Progreso -->
                <section id="progress" class="section">
                    <h2>Tu Progreso</h2>
                    <p>Revisa tu avance en el aprendizaje del inglés.</p>
                    
                    <div class="progress-container">
                        <h3>Progreso General</h3>
                        <div class="progress-bar">
                            <div class="progress-fill" id="overall-progress"></div>
                        </div>
                        <p>Has completado el <span id="progress-percent">0</span>% del curso</p>
                    </div>
                    
                    <div class="progress-container">
                        <h3>Lecciones Completadas</h3>
                        <p>✅ Present Simple - Completado</p>
                        <p>✅ Vocabulary Basics - Completado</p>
                        <p>🔄 Past Continuous - En progreso</p>
                        <p>❌ Future Tenses - No iniciado</p>
                    </div>
                </section>
                
                <!-- Sección de Recursos -->
                <section id="resources" class="section">
                    <h2>Recursos Adicionales</h2>
                    <p>Enlaces y materiales adicionales para complementar tu aprendizaje.</p>
                    
                    <div class="resource-list">
                        <div class="resource-item">
                            <div class="resource-icon">📖</div>
                            <div>
                                <h3>Gramática Avanzada</h3>
                                <p>Guía completa de gramática inglesa</p>
                            </div>
                        </div>
                        
                        <div class="resource-item">
                            <div class="resource-icon">🎧</div>
                            <div>
                                <h3>Podcasts en Inglés</h3>
                                <p>Mejora tu listening con estos podcasts</p>
                            </div>
                        </div>
                        
                        <div class="resource-item">
                            <div class="resource-icon">📺</div>
                            <div>
                                <h3>Canales de YouTube</h3>
                                <p>Canales recomendados para aprender inglés</p>
                            </div>
                        </div>
                        
                        <div class="resource-item">
                            <div class="resource-icon">📝</div>
                            <div>
                                <h3>Plantillas de Ejercicios</h3>
                                <p>Descarga ejercicios adicionales en PDF</p>
                            </div>
                        </div>
                    </div>
                </section>
            </main>
        </div>
    </div>

    <script>
        // Función para iniciar sesión
        function login() {
            const email = document.getElementById('email').value;
            const password = document.getElementById('password').value;
            
            if (!email || !password) {
                alert('Por favor, completa todos los campos');
                return;
            }
            
            // Simular inicio de sesión exitoso
            document.getElementById('login-page').style.display = 'none';
            document.getElementById('main-app').style.display = 'flex';
            document.getElementById('username').textContent = email.split('@')[0];
            
            // Simular progreso
            simulateProgress();
        }
        
        // Función para cerrar sesión
        function logout() {
            document.getElementById('main-app').style.display = 'none';
            document.getElementById('login-page').style.display = 'flex';
            document.getElementById('email').value = '';
            document.getElementById('password').value = '';
        }
        
        // Navegación entre secciones
        document.querySelectorAll('.nav-item').forEach(item => {
            item.addEventListener('click', function() {
                // Remover clase active de todos los items
                document.querySelectorAll('.nav-item').forEach(i => {
                    i.classList.remove('active');
                });
                
                // Añadir clase active al item clickeado
                this.classList.add('active');
                
                // Ocultar todas las secciones
                document.querySelectorAll('.section').forEach(section => {
                    section.classList.remove('active');
                });
                
                // Mostrar la sección correspondiente
                const sectionId = this.getAttribute('data-section');
                document.getElementById(sectionId).classList.add('active');
            });
        });
        
        // Simular barra de progreso
        function simulateProgress() {
            const progressBar = document.getElementById('overall-progress');
            const progressPercent = document.getElementById('progress-percent');
            
            let progress = 0;
            const interval = setInterval(() => {
                progress += Math.random() * 5;
                if (progress >= 65) {
                    progress = 65;
                    clearInterval(interval);
                }
                
                progressBar.style.width = progress + '%';
                progressPercent.textContent = Math.round(progress);
            }, 100);
        }
        
        // Botones de comenzar lección/ejercicio
        document.querySelectorAll('.start-btn').forEach(btn => {
            btn.addEventListener('click', function() {
                alert('¡Función de ejercicio activada! En una aplicación real, esto abriría el ejercicio seleccionado.');
            });
        });
    </script>
</body>
</html>
