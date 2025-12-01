<!doctype html>
<html lang="es">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sistema de Gestión de Vacaciones</title>
  <style>
    body {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Inter', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #0a1628 0%, #1e3c72 50%, #2a5298 100%);
      min-height: 100%;
      height: 100%;
    }
    
    html {
      height: 100%;
    }
    
    .main-container {
      width: 100%;
      min-height: 100%;
      padding: 20px;
      box-sizing: border-box;
    }
    
    .header-bar {
      background: linear-gradient(90deg, #0a1628 0%, #1e3c72 100%);
      color: white;
      padding: 20px 40px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.2);
      margin-bottom: 30px;
      border-radius: 10px;
    }
    
    .header-bar h1 {
      margin: 0;
      font-size: 28px;
      font-weight: 700;
      letter-spacing: -0.5px;
    }
    
    .header-bar p {
      margin: 5px 0 0 0;
      opacity: 0.9;
      font-size: 14px;
    }
    
    .card {
      background: white;
      border-radius: 12px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.1);
      padding: 30px;
      margin-bottom: 25px;
    }
    
    .login-container {
      max-width: 450px;
      margin: 50px auto;
    }
    
    .role-selector {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 20px;
      margin-bottom: 30px;
    }
    
    .role-card {
      background: white;
      border: 3px solid #1e3c72;
      border-radius: 15px;
      padding: 40px 20px;
      text-align: center;
      cursor: pointer;
      transition: all 0.3s ease;
    }
    
    .role-card:hover {
      background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
      color: white;
      transform: translateY(-5px);
      box-shadow: 0 10px 30px rgba(30, 60, 114, 0.4);
    }
    
    .role-card .icon {
      font-size: 48px;
      margin-bottom: 15px;
    }
    
    .role-card .title {
      font-size: 20px;
      font-weight: 700;
      margin: 0;
    }
    
    .role-card .subtitle {
      font-size: 13px;
      margin-top: 5px;
      opacity: 0.8;
    }
    
    .form-group {
      margin-bottom: 20px;
    }
    
    label {
      display: block;
      margin-bottom: 8px;
      color: #0d2447;
      font-weight: 600;
      font-size: 14px;
    }
    
    input, textarea, select {
      width: 100%;
      padding: 14px;
      border: 2px solid #e0e7ff;
      border-radius: 8px;
      font-size: 15px;
      box-sizing: border-box;
      transition: all 0.3s;
      font-family: inherit;
    }
    
    input:focus, textarea:focus, select:focus {
      outline: none;
      border-color: #1e3c72;
      box-shadow: 0 0 0 3px rgba(30, 60, 114, 0.15);
    }
    
    textarea {
      resize: vertical;
      min-height: 100px;
    }
    
    .btn {
      padding: 14px 28px;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.3s;
      text-align: center;
    }
    
    .btn-primary {
      background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
      color: white;
      width: 100%;
    }
    
    .btn-primary:hover {
      background: linear-gradient(135deg, #0a1628 0%, #1e3c72 100%);
      transform: translateY(-2px);
      box-shadow: 0 8px 20px rgba(30, 60, 114, 0.5);
    }
    
    .btn-primary:disabled {
      opacity: 0.6;
      cursor: not-allowed;
      transform: none;
    }
    
    .btn-secondary {
      background: #f0f4f8;
      color: #0d2447;
      border: 2px solid #e0e7ff;
    }
    
    .btn-secondary:hover {
      background: #e0e7ff;
    }
    
    .btn-success {
      background: #10b981;
      color: white;
    }
    
    .btn-success:hover {
      background: #059669;
    }
    
    .btn-danger {
      background: #ef4444;
      color: white;
    }
    
    .btn-danger:hover {
      background: #dc2626;
    }
    
    .btn-small {
      padding: 8px 16px;
      font-size: 14px;
    }
    
    .back-btn {
      margin-top: 15px;
      width: 100%;
    }
    
    .dashboard {
      display: none;
      max-width: 1400px;
      margin: 0 auto;
    }
    
    .dashboard.active {
      display: block;
    }
    
    .welcome-section {
      background: linear-gradient(135deg, #0a1628 0%, #1e3c72 100%);
      color: white;
      padding: 30px;
      border-radius: 12px;
      margin-bottom: 25px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 6px 20px rgba(10, 22, 40, 0.3);
    }
    
    .welcome-text h2 {
      margin: 0 0 8px 0;
      font-size: 32px;
      font-weight: 700;
    }
    
    .welcome-text p {
      margin: 0;
      font-size: 16px;
      opacity: 0.9;
    }
    
    .welcome-actions {
      display: flex;
      gap: 15px;
    }
    
    .stats-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      margin-bottom: 25px;
    }
    
    .stat-card {
      background: white;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.08);
      border-left: 5px solid #1e3c72;
    }
    
    .stat-label {
      font-size: 13px;
      color: #64748b;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 0.5px;
      margin-bottom: 8px;
    }
    
    .stat-value {
      font-size: 36px;
      font-weight: 700;
      color: #0d2447;
      margin: 0;
    }
    
    .stat-icon {
      font-size: 28px;
      margin-bottom: 10px;
    }
    
    .action-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 15px;
      margin-bottom: 25px;
    }
    
    .action-card {
      background: white;
      padding: 25px;
      border-radius: 12px;
      text-align: center;
      cursor: pointer;
      transition: all 0.3s;
      border: 2px solid #e0e7ff;
    }
    
    .action-card:hover {
      border-color: #1e3c72;
      background: linear-gradient(135deg, #f8fafc 0%, #e8f0ff 100%);
      transform: translateY(-5px);
      box-shadow: 0 10px 25px rgba(30, 60, 114, 0.2);
    }
    
    .action-card .icon {
      font-size: 40px;
      margin-bottom: 12px;
    }
    
    .action-card .title {
      font-size: 16px;
      font-weight: 700;
      color: #0d2447;
      margin: 0;
    }
    
    .section-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }
    
    .section-title {
      font-size: 22px;
      font-weight: 700;
      color: #0d2447;
      margin: 0;
    }
    
    .table-container {
      overflow-x: auto;
      background: white;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.08);
    }
    
    table {
      width: 100%;
      border-collapse: collapse;
    }
    
    thead {
      background: #f8fafc;
    }
    
    th {
      padding: 16px;
      text-align: left;
      font-weight: 700;
      color: #0d2447;
      font-size: 13px;
      text-transform: uppercase;
      letter-spacing: 0.5px;
      border-bottom: 2px solid #e0e7ff;
    }
    
    td {
      padding: 16px;
      border-bottom: 1px solid #f1f5f9;
      color: #334155;
      font-size: 14px;
    }
    
    tr:hover {
      background: #f8fafc;
    }
    
    .badge {
      display: inline-block;
      padding: 6px 14px;
      border-radius: 20px;
      font-size: 12px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.5px;
    }
    
    .badge-pendiente {
      background: #fef3c7;
      color: #92400e;
    }
    
    .badge-aprobada {
      background: #d1fae5;
      color: #065f46;
    }
    
    .badge-rechazada {
      background: #fee2e2;
      color: #991b1b;
    }
    
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(10, 22, 40, 0.85);
      justify-content: center;
      align-items: center;
      z-index: 1000;
      padding: 20px;
      box-sizing: border-box;
      backdrop-filter: blur(4px);
    }
    
    .modal.active {
      display: flex;
    }
    
    .modal-content {
      background: white;
      padding: 35px;
      border-radius: 16px;
      max-width: 600px;
      width: 100%;
      max-height: 90%;
      overflow-y: auto;
      box-shadow: 0 20px 60px rgba(0,0,0,0.3);
    }
    
    .modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 25px;
      padding-bottom: 20px;
      border-bottom: 2px solid #e0e7ff;
    }
    
    .modal-header h3 {
      margin: 0;
      color: #0d2447;
      font-size: 24px;
      font-weight: 700;
    }
    
    .modal-close {
      background: none;
      border: none;
      font-size: 28px;
      color: #64748b;
      cursor: pointer;
      padding: 0;
      width: 32px;
      height: 32px;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    
    .modal-buttons {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
      margin-top: 25px;
    }
    
    .motivational-message {
      background: linear-gradient(135deg, #10b981 0%, #059669 100%);
      color: white;
      padding: 20px 25px;
      border-radius: 12px;
      margin-bottom: 25px;
      box-shadow: 0 4px 12px rgba(16, 185, 129, 0.2);
    }
    
    .motivational-message .icon {
      font-size: 28px;
      margin-bottom: 10px;
    }
    
    .motivational-message .text {
      font-size: 16px;
      font-weight: 500;
      line-height: 1.6;
      margin: 0;
    }
    
    .chart-container {
      background: white;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.08);
      margin-bottom: 25px;
    }
    
    .progress-bar {
      width: 100%;
      height: 24px;
      background: #e0e7ff;
      border-radius: 12px;
      overflow: hidden;
      margin-top: 10px;
      box-shadow: inset 0 2px 4px rgba(0,0,0,0.1);
    }
    
    .progress-fill {
      height: 100%;
      background: linear-gradient(90deg, #1e3c72 0%, #2a5298 100%);
      transition: width 0.5s ease;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 12px;
      font-weight: 700;
      box-shadow: 0 2px 6px rgba(30, 60, 114, 0.3);
    }
    
    .calendar-grid {
      display: grid;
      grid-template-columns: repeat(7, 1fr);
      gap: 8px;
      margin-top: 15px;
    }
    
    .calendar-day {
      aspect-ratio: 1;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 8px;
      font-size: 13px;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.2s;
    }
    
    .calendar-day.header {
      background: #f8fafc;
      color: #64748b;
      cursor: default;
    }
    
    .calendar-day.today {
      background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
      color: white;
      font-weight: 700;
      box-shadow: 0 3px 8px rgba(30, 60, 114, 0.4);
    }
    
    .calendar-day.vacation {
      background: #10b981;
      color: white;
    }
    
    .calendar-day.holiday {
      background: #ef4444;
      color: white;
    }
    
    .calendar-day:not(.header):hover {
      transform: scale(1.1);
      box-shadow: 0 4px 8px rgba(0,0,0,0.15);
    }
    
    .export-buttons {
      display: flex;
      gap: 10px;
      margin-top: 15px;
    }
    
    .config-button {
      position: fixed;
      bottom: 20px;
      right: 20px;
      width: 56px;
      height: 56px;
      border-radius: 50%;
      background: linear-gradient(135deg, #0a1628 0%, #1e3c72 100%);
      border: 3px solid #2a5298;
      color: white;
      font-size: 24px;
      cursor: pointer;
      box-shadow: 0 6px 20px rgba(10, 22, 40, 0.5);
      z-index: 999;
      transition: all 0.3s;
      display: none;
    }
    
    .config-button:hover {
      transform: scale(1.15) rotate(90deg);
      box-shadow: 0 8px 25px rgba(30, 60, 114, 0.6);
    }
    
    .toast {
      position: fixed;
      top: 20px;
      right: 20px;
      background: linear-gradient(135deg, #0a1628 0%, #1e3c72 100%);
      color: white;
      padding: 16px 24px;
      border-radius: 10px;
      border-left: 4px solid #2a5298;
      box-shadow: 0 8px 24px rgba(10, 22, 40, 0.4);
      z-index: 2000;
      display: none;
      max-width: 350px;
    }
    
    .toast.active {
      display: block;
      animation: slideIn 0.3s ease-out;
    }
    
    @keyframes slideIn {
      from {
        transform: translateX(400px);
        opacity: 0;
      }
      to {
        transform: translateX(0);
        opacity: 1;
      }
    }
    
    .toast.success {
      background: #10b981;
    }
    
    .toast.error {
      background: #ef4444;
    }
    
    .empty-state {
      text-align: center;
      padding: 60px 20px;
      color: #64748b;
    }
    
    .empty-state .icon {
      font-size: 64px;
      margin-bottom: 20px;
      opacity: 0.5;
    }
    
    .empty-state .text {
      font-size: 18px;
      font-weight: 600;
    }
    
    .loading {
      text-align: center;
      padding: 40px;
    }
    
    .spinner {
      border: 4px solid #e0e7ff;
      border-top: 4px solid #1e3c72;
      border-right: 4px solid #2a5298;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      animation: spin 1s linear infinite;
      margin: 0 auto;
    }
    
    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }
    
    .tabs {
      display: flex;
      gap: 10px;
      margin-bottom: 25px;
      border-bottom: 2px solid #e0e7ff;
    }
    
    .tab {
      padding: 12px 24px;
      background: none;
      border: none;
      color: #64748b;
      font-size: 15px;
      font-weight: 600;
      cursor: pointer;
      border-bottom: 3px solid transparent;
      transition: all 0.3s;
    }
    
    .tab.active {
      color: #0a1628;
      border-bottom-color: #1e3c72;
      font-weight: 700;
    }
    
    .tab:hover {
      color: #1e3c72;
      background: rgba(42, 82, 152, 0.05);
    }
    
    .comments-section {
      margin-top: 20px;
      padding-top: 20px;
      border-top: 2px solid #e0e7ff;
    }
    
    .comment {
      background: #f8fafc;
      padding: 15px;
      border-radius: 8px;
      margin-bottom: 12px;
      border-left: 4px solid #1e3c72;
      box-shadow: 0 2px 4px rgba(0,0,0,0.05);
    }
    
    .comment-header {
      display: flex;
      justify-content: space-between;
      margin-bottom: 8px;
    }
    
    .comment-author {
      font-weight: 700;
      color: #0d2447;
      font-size: 14px;
    }
    
    .comment-date {
      font-size: 12px;
      color: #64748b;
    }
    
    .comment-text {
      color: #334155;
      font-size: 14px;
      line-height: 1.6;
    }
    
    @media (max-width: 768px) {
      .role-selector {
        grid-template-columns: 1fr;
      }
      
      .stats-grid {
        grid-template-columns: 1fr;
      }
      
      .action-grid {
        grid-template-columns: 1fr;
      }
      
      .welcome-section {
        flex-direction: column;
        text-align: center;
      }
      
      .welcome-actions {
        margin-top: 20px;
        flex-direction: column;
        width: 100%;
      }
      
      .modal-buttons {
        grid-template-columns: 1fr;
      }
      
      .table-container {
        font-size: 13px;
      }
      
      th, td {
        padding: 10px;
      }
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
  <script src="/_sdk/element_sdk.js" type="text/javascript"></script>
  <script src="https://cdn.tailwindcss.com" type="text/javascript"></script>
 </head>
 <body>
  <div class="main-container"><!-- Login Section -->
   <div id="loginSection">
    <div class="login-container">
     <div class="card">
      <div class="header-bar" style="margin: -30px -30px 30px -30px;">
       <h1>Sistema de Gestión de Vacaciones</h1>
       <p>Plataforma Corporativa - Hospital 2026</p>
      </div>
      <div id="roleSelection">
       <div class="role-selector">
        <div class="role-card" onclick="selectRole('medico')">
         <div class="icon">
          👨‍⚕️
         </div>
         <p class="title">Personal Médico</p>
         <p class="subtitle">Acceso para médicos y personal asistencial</p>
        </div>
        <div class="role-card" onclick="selectRole('jefe')">
         <div class="icon">
          👔
         </div>
         <p class="title">Jefe de Servicio</p>
         <p class="subtitle">Panel de administración y aprobaciones</p>
        </div>
       </div>
      </div><!-- Login Médico -->
      <div id="medicoLogin" style="display: none;">
       <h2 style="color: #0d2447; margin-bottom: 25px;">Acceso Personal Médico</h2>
       <form id="medicoLoginForm" onsubmit="loginMedico(event)">
        <div class="form-group"><label for="medicoDocumento">Número de Documento</label> <input type="text" id="medicoDocumento" placeholder="Ingrese su documento de identidad" required>
        </div><button type="submit" class="btn btn-primary" id="medicoLoginBtn">Iniciar Sesión</button> <button type="button" class="btn btn-secondary" style="width: 100%; margin-top: 10px;" onclick="showRegistro()">¿Primera vez? Regístrate aquí</button> <button type="button" class="btn btn-secondary back-btn" onclick="backToRoleSelection()">← Volver</button>
       </form>
      </div><!-- Registro Médico -->
      <div id="medicoRegistro" style="display: none;">
       <h2 style="color: #0d2447; margin-bottom: 25px;">📝 Registro Personal Médico</h2>
       <form id="medicoRegistroForm" onsubmit="registrarMedico(event)">
        <div class="form-group"><label for="regDocumento">Número de Documento *</label> <input type="text" id="regDocumento" placeholder="Documento de identidad" required>
        </div>
        <div class="form-group"><label for="regNombre">Nombre *</label> <input type="text" id="regNombre" placeholder="Nombre" required>
        </div>
        <div class="form-group"><label for="regApellido">Apellido *</label> <input type="text" id="regApellido" placeholder="Apellido" required>
        </div>
        <div class="form-group"><label for="regEspecialidad">Especialidad *</label> <input type="text" id="regEspecialidad" placeholder="Ej: Cardiología, Pediatría, etc." required>
        </div>
        <div class="form-group"><label for="regEmail">Correo Electrónico *</label> <input type="email" id="regEmail" placeholder="correo@hospital.com" required>
        </div>
        <div class="form-group"><label for="regDiasVacaciones">Días de Vacaciones Anuales</label> <input type="number" id="regDiasVacaciones" value="30" min="15" max="45" required>
         <p style="margin: 5px 0 0 0; font-size: 12px; color: #64748b;">Por defecto: 30 días</p>
        </div><button type="submit" class="btn btn-primary" id="registroBtn">✅ Registrarse</button> <button type="button" class="btn btn-secondary" style="width: 100%; margin-top: 10px;" onclick="backToLogin()">Ya tengo cuenta</button> <button type="button" class="btn btn-secondary back-btn" onclick="backToRoleSelection()">← Volver</button>
       </form>
      </div><!-- Login Jefe -->
      <div id="jefeLogin" style="display: none;">
       <h2 style="color: #0d2447; margin-bottom: 25px;">Acceso Jefe de Servicio</h2>
       <form id="jefeLoginForm" onsubmit="loginJefe(event)">
        <div class="form-group"><label for="jefeUsuario">Usuario</label> <input type="text" id="jefeUsuario" placeholder="Nombre de usuario" required>
        </div>
        <div class="form-group"><label for="jefePassword">Contraseña</label> <input type="password" id="jefePassword" placeholder="••••••••" required>
        </div><button type="submit" class="btn btn-primary" id="jefeLoginBtn">Iniciar Sesión</button> <button type="button" class="btn btn-secondary back-btn" onclick="backToRoleSelection()">← Volver</button>
       </form>
      </div>
     </div>
    </div>
   </div><!-- Dashboard Médico -->
   <div id="medicoDashboard" class="dashboard">
    <div class="header-bar">
     <h1>Panel de Control Médico</h1>
     <p>Sistema de Gestión de Vacaciones y Permisos</p>
    </div>
    <div class="welcome-section">
     <div class="welcome-text">
      <h2 id="medicoNombreCompleto">Dr/Dra. Nombre Completo</h2>
      <p id="medicoEspecialidadDetalle">Especialidad</p>
     </div>
     <div class="welcome-actions"><button class="btn btn-danger" onclick="logout()">Cerrar Sesión</button>
     </div>
    </div><!-- Mensaje Motivador -->
    <div class="motivational-message" id="motivationalMessage">
     <div class="icon">
      💙
     </div>
     <p class="text" id="motivationalText">¡Excelente trabajo! Recuerda que tu descanso es fundamental para mantener la calidad de atención a nuestros pacientes.</p>
    </div><!-- Estadísticas -->
    <div class="stats-grid">
     <div class="stat-card">
      <div class="stat-icon">
       🏖️
      </div>
      <div class="stat-label">
       Días Disponibles
      </div>
      <p class="stat-value" id="medicoDisponibles">0</p>
     </div>
     <div class="stat-card">
      <div class="stat-icon">
       📋
      </div>
      <div class="stat-label">
       Días Solicitados
      </div>
      <p class="stat-value" id="medicoSolicitados">0</p>
     </div>
     <div class="stat-card">
      <div class="stat-icon">
       ✅
      </div>
      <div class="stat-label">
       Días Aprobados
      </div>
      <p class="stat-value" id="medicoAprobados">0</p>
     </div>
     <div class="stat-card">
      <div class="stat-icon">
       ⏳
      </div>
      <div class="stat-label">
       Pendientes
      </div>
      <p class="stat-value" id="medicoPendientes">0</p>
     </div>
    </div><!-- Progreso Visual -->
    <div class="chart-container">
     <h3 style="margin: 0 0 15px 0; color: #0d2447;">Uso de Vacaciones 2026</h3>
     <div class="progress-bar">
      <div class="progress-fill" id="vacationProgress" style="width: 0%">
       0%
      </div>
     </div>
     <p style="margin: 10px 0 0 0; font-size: 14px; color: #64748b;"><span id="diasUsados">0</span> de <span id="diasTotales">30</span> días utilizados</p>
    </div><!-- Acciones Rápidas -->
    <div class="card">
     <h3 style="margin: 0 0 20px 0; color: #0d2447;">Acciones Rápidas</h3>
     <div class="action-grid">
      <div class="action-card" onclick="openVacationModal()">
       <div class="icon">
        🌴
       </div>
       <p class="title">Solicitar Vacaciones</p>
      </div>
      <div class="action-card" onclick="openPermissionModal()">
       <div class="icon">
        📄
       </div>
       <p class="title">Solicitar Permiso</p>
      </div>
      <div class="action-card" onclick="showCalendar()">
       <div class="icon">
        📅
       </div>
       <p class="title">Ver Calendario</p>
      </div>
      <div class="action-card" onclick="exportReport()">
       <div class="icon">
        📊
       </div>
       <p class="title">Exportar Reporte</p>
      </div>
     </div>
    </div><!-- Historial de Solicitudes -->
    <div class="card">
     <div class="section-header">
      <h3 class="section-title">Historial de Solicitudes</h3>
     </div>
     <div class="tabs"><button class="tab active" onclick="filterSolicitudes('todas')">Todas</button> <button class="tab" onclick="filterSolicitudes('pendiente')">Pendientes</button> <button class="tab" onclick="filterSolicitudes('aprobada')">Aprobadas</button> <button class="tab" onclick="filterSolicitudes('rechazada')">Rechazadas</button>
     </div>
     <div class="table-container">
      <table id="medicoSolicitudesTable">
       <thead>
        <tr>
         <th>Tipo</th>
         <th>Fecha Solicitud</th>
         <th>Período</th>
         <th>Días</th>
         <th>Estado</th>
         <th>Acciones</th>
        </tr>
       </thead>
       <tbody id="medicoSolicitudesBody">
        <tr>
         <td colspan="6" class="empty-state">
          <div class="icon">
           📋
          </div>
          <div class="text">
           No hay solicitudes registradas
          </div></td>
        </tr>
       </tbody>
      </table>
     </div>
    </div>
   </div><!-- Dashboard Jefe -->
   <div id="jefeDashboard" class="dashboard">
    <div class="header-bar">
     <h1>Panel de Administración</h1>
     <p>Gestión de Solicitudes y Aprobaciones</p>
    </div>
    <div class="welcome-section">
     <div class="welcome-text">
      <h2>Jefe de Servicio</h2>
      <p>Panel de Control Ejecutivo</p>
     </div>
     <div class="welcome-actions"><button class="btn btn-danger" onclick="logout()">Cerrar Sesión</button>
     </div>
    </div><!-- Estadísticas Generales -->
    <div class="stats-grid">
     <div class="stat-card">
      <div class="stat-icon">
       ⏳
      </div>
      <div class="stat-label">
       Pendientes
      </div>
      <p class="stat-value" id="jefePendientes">0</p>
     </div>
     <div class="stat-card">
      <div class="stat-icon">
       ✅
      </div>
      <div class="stat-label">
       Aprobadas Hoy
      </div>
      <p class="stat-value" id="jefeAprobadasHoy">0</p>
     </div>
     <div class="stat-card">
      <div class="stat-icon">
       👨‍⚕️
      </div>
      <div class="stat-label">
       Total Médicos
      </div>
      <p class="stat-value" id="jefeTotalMedicos">0</p>
     </div>
     <div class="stat-card">
      <div class="stat-icon">
       📊
      </div>
      <div class="stat-label">
       Total Solicitudes
      </div>
      <p class="stat-value" id="jefeTotalSolicitudes">0</p>
     </div>
    </div><!-- Solicitudes Pendientes -->
    <div class="card">
     <div class="section-header">
      <h3 class="section-title">Solicitudes Pendientes de Aprobación</h3><button class="btn btn-secondary btn-small" onclick="exportJefeReport()">📊 Exportar Reporte</button>
     </div>
     <div class="table-container">
      <table id="jefeSolicitudesTable">
       <thead>
        <tr>
         <th>Médico</th>
         <th>Especialidad</th>
         <th>Tipo</th>
         <th>Período</th>
         <th>Días</th>
         <th>Fecha Solicitud</th>
         <th>Acciones</th>
        </tr>
       </thead>
       <tbody id="jefeSolicitudesBody">
        <tr>
         <td colspan="7" class="empty-state">
          <div class="icon">
           ✅
          </div>
          <div class="text">
           No hay solicitudes pendientes
          </div></td>
        </tr>
       </tbody>
      </table>
     </div>
    </div><!-- Historial Completo -->
    <div class="card">
     <div class="section-header">
      <h3 class="section-title">Historial Completo</h3>
     </div>
     <div class="tabs"><button class="tab active" onclick="filterJefeSolicitudes('todas')">Todas</button> <button class="tab" onclick="filterJefeSolicitudes('pendiente')">Pendientes</button> <button class="tab" onclick="filterJefeSolicitudes('aprobada')">Aprobadas</button> <button class="tab" onclick="filterJefeSolicitudes('rechazada')">Rechazadas</button>
     </div>
     <div class="table-container">
      <table id="jefeHistorialTable">
       <thead>
        <tr>
         <th>Médico</th>
         <th>Tipo</th>
         <th>Período</th>
         <th>Días</th>
         <th>Estado</th>
         <th>Fecha</th>
        </tr>
       </thead>
       <tbody id="jefeHistorialBody">
       </tbody>
      </table>
     </div>
    </div>
   </div>
  </div><!-- Modal Solicitud Vacaciones -->
  <div id="vacationModal" class="modal">
   <div class="modal-content">
    <div class="modal-header">
     <h3>🌴 Solicitar Vacaciones</h3><button class="modal-close" onclick="closeVacationModal()">×</button>
    </div>
    <form id="vacationForm" onsubmit="submitVacation(event)">
     <div class="form-group"><label for="vacationStart">Fecha de Inicio</label> <input type="date" id="vacationStart" required>
     </div>
     <div class="form-group"><label for="vacationEnd">Fecha de Finalización</label> <input type="date" id="vacationEnd" required>
     </div>
     <div class="form-group"><label for="vacationDays">Días Hábiles (calculado automáticamente)</label> <input type="number" id="vacationDays" readonly style="background: #f8fafc;">
     </div>
     <div class="form-group"><label for="vacationObservations">Observaciones (opcional)</label> <textarea id="vacationObservations" placeholder="Ingrese cualquier observación relevante"></textarea>
     </div>
     <div class="modal-buttons"><button type="button" class="btn btn-secondary" onclick="closeVacationModal()">Cancelar</button> <button type="submit" class="btn btn-primary">Enviar Solicitud</button>
     </div>
    </form>
   </div>
  </div><!-- Modal Solicitud Permiso -->
  <div id="permissionModal" class="modal">
   <div class="modal-content">
    <div class="modal-header">
     <h3>📄 Solicitar Permiso</h3><button class="modal-close" onclick="closePermissionModal()">×</button>
    </div>
    <form id="permissionForm" onsubmit="submitPermission(event)">
     <div class="form-group"><label for="permissionDate">Fecha del Permiso</label> <input type="date" id="permissionDate" required>
     </div>
     <div class="form-group"><label for="permissionType">Tipo de Permiso</label> <select id="permissionType" required> <option value="">Seleccione un tipo</option> <option value="Personal">Personal</option> <option value="Médico">Médico</option> <option value="Familiar">Familiar</option> <option value="Capacitación">Capacitación</option> <option value="Otro">Otro</option> </select>
     </div>
     <div class="form-group"><label for="permissionObservations">Motivo / Justificación</label> <textarea id="permissionObservations" placeholder="Describa el motivo del permiso" required></textarea>
     </div>
     <div class="modal-buttons"><button type="button" class="btn btn-secondary" onclick="closePermissionModal()">Cancelar</button> <button type="submit" class="btn btn-primary">Enviar Solicitud</button>
     </div>
    </form>
   </div>
  </div><!-- Modal Detalle Solicitud -->
  <div id="detailModal" class="modal">
   <div class="modal-content">
    <div class="modal-header">
     <h3>📋 Detalle de Solicitud</h3><button class="modal-close" onclick="closeDetailModal()">×</button>
    </div>
    <div id="detailContent"><!-- Contenido dinámico -->
    </div>
    <div class="comments-section">
     <h4 style="color: #0d2447; margin-bottom: 15px;">Comentarios</h4>
     <div id="commentsList"><!-- Comentarios dinámicos -->
     </div>
     <div class="form-group" style="margin-top: 15px;"><textarea id="newComment" placeholder="Agregar un comentario..."></textarea> <button class="btn btn-primary" style="margin-top: 10px;" onclick="addComment()">Agregar Comentario</button>
     </div>
    </div><button class="btn btn-secondary" style="width: 100%; margin-top: 20px;" onclick="closeDetailModal()">Cerrar</button>
   </div>
  </div><!-- Modal Calendario -->
  <div id="calendarModal" class="modal">
   <div class="modal-content">
    <div class="modal-header">
     <h3>📅 Calendario de Vacaciones 2026</h3><button class="modal-close" onclick="closeCalendarModal()">×</button>
    </div>
    <div id="calendarContent"><!-- Calendario dinámico -->
    </div><button class="btn btn-secondary" style="width: 100%; margin-top: 20px;" onclick="closeCalendarModal()">Cerrar</button>
   </div>
  </div><!-- Toast Notificaciones -->
  <div id="toast" class="toast"></div>
  <script>
    (function() {
      // Sistema con Google Sheets
      let currentUser = null;
      let allData = { medicos: [], solicitudes: [], festivos: [] };
      let currentSolicitudFilter = 'todas';
      let currentDetailSolicitud = null;
      
      // ⚙️ CONFIGURACIÓN GOOGLE SHEETS - REEMPLAZAR CON TU URL
      const GOOGLE_SHEETS_URL =https://script.google.com/macros/s/AKfycbwzj9mwOMlQ7phubwiR6-7AQKF7Ubaxt3-c9RbrX8rE9ivDLlMgT-2BFYtDlBSf5ZWt/exec

      // Mensajes motivadores
      const motivationalMessages = [
        "¡Excelente trabajo! Tu dedicación marca la diferencia en la vida de nuestros pacientes.",
        "Recuerda que tu descanso es fundamental para mantener la calidad de atención.",
        "Eres parte esencial de nuestro equipo. ¡Gracias por tu compromiso diario!",
        "Tu bienestar es nuestra prioridad. Tómate el tiempo necesario para recargar energías.",
        "La excelencia médica comienza con el autocuidado. ¡Planifica tu descanso!",
        "Tu labor salva vidas. Asegúrate de cuidar también de tu propia salud.",
        "Un equipo descansado es un equipo efectivo. ¡Tus vacaciones son importantes!"
      ];

      // Inicializar
      const today = new Date().toISOString().split('T')[0];
      document.getElementById('vacationStart').min = today;
      document.getElementById('vacationEnd').min = today;
      document.getElementById('permissionDate').min = today;

      // Cargar datos al iniciar
      loadDataFromSheets();
      updateMotivationalMessage();

      // Cambiar mensaje cada 30 segundos
      setInterval(updateMotivationalMessage, 30000);
      
      // Actualizar datos cada 2 minutos
      setInterval(loadDataFromSheets, 120000);

      function updateMotivationalMessage() {
        const randomMessage = motivationalMessages[Math.floor(Math.random() * motivationalMessages.length)];
        const messageElement = document.getElementById('motivationalText');
        if (messageElement) {
          messageElement.textContent = randomMessage;
        }
      }

      // Cargar datos desde Google Sheets
      async function loadDataFromSheets() {
        try {
          const response = await fetch(GOOGLE_SHEETS_URL + '?action=getData');
          
          if (!response.ok) {
            throw new Error('Error de conexión: ' + response.status);
          }
          
          const data = await response.json();
          
          if (data.success) {
            allData = data.data;
            
            // Si hay un usuario logueado, actualizar su dashboard
            if (currentUser) {
              if (currentUser.role === 'medico') {
                updateMedicoStats();
                loadMedicoSolicitudes();
              } else if (currentUser.role === 'jefe') {
                updateJefeStats();
                loadJefeSolicitudes();
                loadJefeHistorial();
              }
            }
          } else {
            console.error('Error al cargar datos:', data.error);
          }
        } catch (error) {
          console.error('Error de conexión con Google Sheets:', error);
          showToast('⚠️ Error de conexión. Verifica la URL de Google Sheets', 'error');
        }
      }

      // Guardar datos en Google Sheets
      async function saveDataToSheets(action, payload) {
        try {
          const response = await fetch(GOOGLE_SHEETS_URL, {
            method: 'POST',
            mode: 'no-cors',
            headers: {
              'Content-Type': 'application/json',
            },
            body: JSON.stringify({
              action: action,
              data: payload
            })
          });
          
          // Con no-cors no podemos leer la respuesta, así que recargar datos
          await new Promise(resolve => setTimeout(resolve, 1500));
          await loadDataFromSheets();
          
          return { success: true };
        } catch (error) {
          console.error('Error al guardar en Google Sheets:', error);
          showToast('Error al guardar los datos', 'error');
          return { success: false, error: error.message };
        }
      }

      // Navegación
      window.selectRole = function(role) {
        document.getElementById('roleSelection').style.display = 'none';
        if (role === 'medico') {
          document.getElementById('medicoLogin').style.display = 'block';
        } else {
          document.getElementById('jefeLogin').style.display = 'block';
        }
      };

      window.backToRoleSelection = function() {
        document.getElementById('medicoLogin').style.display = 'none';
        document.getElementById('medicoRegistro').style.display = 'none';
        document.getElementById('jefeLogin').style.display = 'none';
        document.getElementById('roleSelection').style.display = 'block';
        document.getElementById('medicoDocumento').value = '';
        document.getElementById('jefeUsuario').value = '';
        document.getElementById('jefePassword').value = '';
      };

      window.showRegistro = function() {
        document.getElementById('medicoLogin').style.display = 'none';
        document.getElementById('medicoRegistro').style.display = 'block';
      };

      window.backToLogin = function() {
        document.getElementById('medicoRegistro').style.display = 'none';
        document.getElementById('medicoLogin').style.display = 'block';
        document.getElementById('medicoRegistroForm').reset();
      };

      window.registrarMedico = async function(event) {
        event.preventDefault();
        
        const btn = document.getElementById('registroBtn');
        btn.disabled = true;
        btn.textContent = 'Registrando...';
        
        const documento = document.getElementById('regDocumento').value.trim();
        const nombre = document.getElementById('regNombre').value.trim();
        const apellido = document.getElementById('regApellido').value.trim();
        const especialidad = document.getElementById('regEspecialidad').value.trim();
        const email = document.getElementById('regEmail').value.trim();
        const diasVacaciones = document.getElementById('regDiasVacaciones').value;

        // Verificar si ya existe
        const existente = allData.medicos.find(m => m.documento === documento);
        if (existente) {
          showToast('El documento ya está registrado en el sistema', 'error');
          btn.disabled = false;
          btn.textContent = '✅ Registrarse';
          return;
        }

        const nuevoMedico = {
          documento: documento,
          nombre: nombre,
          apellido: apellido,
          especialidad: especialidad,
          email: email,
          dias_vacaciones: diasVacaciones,
          fecha_registro: new Date().toISOString().split('T')[0]
        };

        const result = await saveDataToSheets('addMedico', nuevoMedico);

        btn.disabled = false;
        btn.textContent = '✅ Registrarse';

        if (result.success) {
          showToast('✅ Registro exitoso! Ya puedes iniciar sesión', 'success');
          
          setTimeout(() => {
            document.getElementById('medicoRegistro').style.display = 'none';
            document.getElementById('medicoLogin').style.display = 'block';
            document.getElementById('medicoRegistroForm').reset();
            document.getElementById('medicoDocumento').value = documento;
          }, 1500);
        }
      };

      window.loginMedico = function(event) {
        event.preventDefault();
        const documento = document.getElementById('medicoDocumento').value.trim();
        
        const medico = allData.medicos.find(m => m.documento === documento);
        
        if (medico) {
          currentUser = { ...medico, role: 'medico' };
          showMedicoDashboard();
          showToast('¡Bienvenido/a, ' + medico.nombre + '!', 'success');
        } else {
          showToast('Documento no encontrado. ¿Ya te registraste?', 'error');
        }
      };

      window.loginJefe = function(event) {
        event.preventDefault();
        const usuario = document.getElementById('jefeUsuario').value.trim();
        const password = document.getElementById('jefePassword').value.trim();
        
        if (usuario === 'jefe' && password === 'hospital2026') {
          currentUser = { role: 'jefe', nombre: 'Jefe de Servicio' };
          showJefeDashboard();
          showToast('¡Bienvenido al panel de administración!', 'success');
        } else {
          showToast('Credenciales incorrectas', 'error');
        }
      };

      window.logout = function() {
        currentUser = null;
        document.getElementById('medicoDashboard').classList.remove('active');
        document.getElementById('jefeDashboard').classList.remove('active');
        document.getElementById('loginSection').style.display = 'block';
        backToRoleSelection();
        showToast('Sesión cerrada correctamente', 'success');
      };

      // Dashboard Médico
      function showMedicoDashboard() {
        document.getElementById('loginSection').style.display = 'none';
        document.getElementById('medicoDashboard').classList.add('active');
        
        document.getElementById('medicoNombreCompleto').textContent = 
          `Dr/Dra. ${currentUser.nombre} ${currentUser.apellido}`;
        document.getElementById('medicoEspecialidadDetalle').textContent = 
          currentUser.especialidad || 'Medicina General';
        
        updateMedicoStats();
        loadMedicoSolicitudes();
      }

      function updateMedicoStats() {
        const solicitudes = allData.solicitudes.filter(s => 
          s.medico_documento === currentUser.documento
        );
        
        const solicitados = solicitudes
          .filter(s => s.tipo === 'vacaciones')
          .reduce((sum, s) => sum + parseInt(s.dias || 0), 0);
        
        const aprobados = solicitudes
          .filter(s => s.tipo === 'vacaciones' && s.estado === 'aprobada')
          .reduce((sum, s) => sum + parseInt(s.dias || 0), 0);
        
        const pendientes = solicitudes
          .filter(s => s.estado === 'pendiente').length;
        
        const disponibles = parseInt(currentUser.dias_vacaciones || 30) - aprobados;
        
        document.getElementById('medicoDisponibles').textContent = disponibles;
        document.getElementById('medicoSolicitados').textContent = solicitados;
        document.getElementById('medicoAprobados').textContent = aprobados;
        document.getElementById('medicoPendientes').textContent = pendientes;
        
        // Actualizar barra de progreso
        const totalDias = parseInt(currentUser.dias_vacaciones || 30);
        const porcentaje = Math.round((aprobados / totalDias) * 100);
        document.getElementById('vacationProgress').style.width = porcentaje + '%';
        document.getElementById('vacationProgress').textContent = porcentaje + '%';
        document.getElementById('diasUsados').textContent = aprobados;
        document.getElementById('diasTotales').textContent = totalDias;
      }

      function loadMedicoSolicitudes() {
        const solicitudes = allData.solicitudes.filter(s => 
          s.medico_documento === currentUser.documento
        );
        
        const tbody = document.getElementById('medicoSolicitudesBody');
        
        if (solicitudes.length === 0) {
          tbody.innerHTML = `
            <tr>
              <td colspan="6" class="empty-state">
                <div class="icon">📋</div>
                <div class="text">No hay solicitudes registradas</div>
              </td>
            </tr>
          `;
          return;
        }
        
        tbody.innerHTML = '';
        solicitudes.sort((a, b) => new Date(b.fecha_solicitud) - new Date(a.fecha_solicitud));
        
        solicitudes.forEach(sol => {
          if (currentSolicitudFilter !== 'todas' && sol.estado !== currentSolicitudFilter) return;
          
          const tr = document.createElement('tr');
          
          const tipoIcon = sol.tipo === 'vacaciones' ? '🌴' : '📄';
          const periodo = sol.tipo === 'vacaciones' 
            ? `${formatDate(sol.fecha_inicio)} - ${formatDate(sol.fecha_fin)}`
            : formatDate(sol.fecha_inicio);
          const dias = sol.tipo === 'vacaciones' ? sol.dias : '-';
          const estadoClass = `badge-${sol.estado}`;
          const estadoTexto = sol.estado.charAt(0).toUpperCase() + sol.estado.slice(1);
          
          tr.innerHTML = `
            <td>${tipoIcon} ${sol.tipo === 'vacaciones' ? 'Vacaciones' : 'Permiso'}</td>
            <td>${formatDate(sol.fecha_solicitud)}</td>
            <td>${periodo}</td>
            <td>${dias}</td>
            <td><span class="badge ${estadoClass}">${estadoTexto}</span></td>
            <td>
              <button class="btn btn-secondary btn-small" onclick="showSolicitudDetail('${sol.id}')">
                Ver Detalle
              </button>
            </td>
          `;
          
          tbody.appendChild(tr);
        });
      }

      window.filterSolicitudes = function(tipo) {
        currentSolicitudFilter = tipo;
        document.querySelectorAll('#medicoDashboard .tab').forEach(tab => tab.classList.remove('active'));
        event.target.classList.add('active');
        loadMedicoSolicitudes();
      };

      // Dashboard Jefe
      function showJefeDashboard() {
        document.getElementById('loginSection').style.display = 'none';
        document.getElementById('jefeDashboard').classList.add('active');
        
        updateJefeStats();
        loadJefeSolicitudes();
        loadJefeHistorial();
      }

      function updateJefeStats() {
        const pendientes = allData.solicitudes.filter(s => s.estado === 'pendiente').length;
        const hoy = new Date().toISOString().split('T')[0];
        const aprobadasHoy = allData.solicitudes.filter(s => {
          return s.estado === 'aprobada' && s.fecha_aprobacion === hoy;
        }).length;
        
        document.getElementById('jefePendientes').textContent = pendientes;
        document.getElementById('jefeAprobadasHoy').textContent = aprobadasHoy;
        document.getElementById('jefeTotalMedicos').textContent = allData.medicos.length;
        document.getElementById('jefeTotalSolicitudes').textContent = allData.solicitudes.length;
      }

      function loadJefeSolicitudes() {
        const pendientes = allData.solicitudes.filter(s => s.estado === 'pendiente');
        const tbody = document.getElementById('jefeSolicitudesBody');
        
        if (pendientes.length === 0) {
          tbody.innerHTML = `
            <tr>
              <td colspan="7" class="empty-state">
                <div class="icon">✅</div>
                <div class="text">No hay solicitudes pendientes de aprobación</div>
              </td>
            </tr>
          `;
          return;
        }
        
        tbody.innerHTML = '';
        pendientes.sort((a, b) => new Date(a.fecha_solicitud) - new Date(b.fecha_solicitud));
        
        pendientes.forEach(sol => {
          const medico = allData.medicos.find(m => m.documento === sol.medico_documento);
          const nombreMedico = medico ? `${medico.nombre} ${medico.apellido}` : 'Desconocido';
          const especialidad = medico?.especialidad || 'N/A';
          
          const tr = document.createElement('tr');
          
          const tipoIcon = sol.tipo === 'vacaciones' ? '🌴' : '📄';
          const periodo = sol.tipo === 'vacaciones' 
            ? `${formatDate(sol.fecha_inicio)} - ${formatDate(sol.fecha_fin)}`
            : formatDate(sol.fecha_inicio);
          const dias = sol.tipo === 'vacaciones' ? sol.dias : '-';
          
          tr.innerHTML = `
            <td><strong>${nombreMedico}</strong></td>
            <td>${especialidad}</td>
            <td>${tipoIcon} ${sol.tipo === 'vacaciones' ? 'Vacaciones' : 'Permiso'}</td>
            <td>${periodo}</td>
            <td>${dias}</td>
            <td>${formatDate(sol.fecha_solicitud)}</td>
            <td>
              <div style="display: flex; gap: 8px;">
                <button class="btn btn-success btn-small" onclick="processSolicitud('${sol.id}', 'aprobada')">
                  ✓ Aprobar
                </button>
                <button class="btn btn-danger btn-small" onclick="processSolicitud('${sol.id}', 'rechazada')">
                  ✗ Rechazar
                </button>
              </div>
            </td>
          `;
          
          tbody.appendChild(tr);
        });
      }

      function loadJefeHistorial() {
        const tbody = document.getElementById('jefeHistorialBody');
        tbody.innerHTML = '';
        
        const solicitudes = [...allData.solicitudes];
        solicitudes.sort((a, b) => new Date(b.fecha_solicitud) - new Date(a.fecha_solicitud));
        
        solicitudes.forEach(sol => {
          const medico = allData.medicos.find(m => m.documento === sol.medico_documento);
          const nombreMedico = medico ? `${medico.nombre} ${medico.apellido}` : 'Desconocido';
          
          const tr = document.createElement('tr');
          
          const tipoIcon = sol.tipo === 'vacaciones' ? '🌴' : '📄';
          const periodo = sol.tipo === 'vacaciones' 
            ? `${formatDate(sol.fecha_inicio)} - ${formatDate(sol.fecha_fin)}`
            : formatDate(sol.fecha_inicio);
          const dias = sol.tipo === 'vacaciones' ? sol.dias : '-';
          const estadoClass = `badge-${sol.estado}`;
          const estadoTexto = sol.estado.charAt(0).toUpperCase() + sol.estado.slice(1);
          
          tr.innerHTML = `
            <td>${nombreMedico}</td>
            <td>${tipoIcon} ${sol.tipo === 'vacaciones' ? 'Vacaciones' : 'Permiso'}</td>
            <td>${periodo}</td>
            <td>${dias}</td>
            <td><span class="badge ${estadoClass}">${estadoTexto}</span></td>
            <td>${formatDate(sol.fecha_solicitud)}</td>
          `;
          
          tbody.appendChild(tr);
        });
      }

      window.filterJefeSolicitudes = function(tipo) {
        document.querySelectorAll('#jefeDashboard .tab').forEach(tab => tab.classList.remove('active'));
        event.target.classList.add('active');
        
        const tbody = document.getElementById('jefeHistorialBody');
        tbody.innerHTML = '';
        
        const solicitudes = tipo === 'todas' 
          ? [...allData.solicitudes]
          : allData.solicitudes.filter(s => s.estado === tipo);
        
        solicitudes.sort((a, b) => new Date(b.fecha_solicitud) - new Date(a.fecha_solicitud));
        
        solicitudes.forEach(sol => {
          const medico = allData.medicos.find(m => m.documento === sol.medico_documento);
          const nombreMedico = medico ? `${medico.nombre} ${medico.apellido}` : 'Desconocido';
          
          const tr = document.createElement('tr');
          
          const tipoIcon = sol.tipo === 'vacaciones' ? '🌴' : '📄';
          const periodo = sol.tipo === 'vacaciones' 
            ? `${formatDate(sol.fecha_inicio)} - ${formatDate(sol.fecha_fin)}`
            : formatDate(sol.fecha_inicio);
          const dias = sol.tipo === 'vacaciones' ? sol.dias : '-';
          const estadoClass = `badge-${sol.estado}`;
          const estadoTexto = sol.estado.charAt(0).toUpperCase() + sol.estado.slice(1);
          
          tr.innerHTML = `
            <td>${nombreMedico}</td>
            <td>${tipoIcon} ${sol.tipo === 'vacaciones' ? 'Vacaciones' : 'Permiso'}</td>
            <td>${periodo}</td>
            <td>${dias}</td>
            <td><span class="badge ${estadoClass}">${estadoTexto}</span></td>
            <td>${formatDate(sol.fecha_solicitud)}</td>
          `;
          
          tbody.appendChild(tr);
        });
      };

      window.processSolicitud = function(solicitudId, nuevoEstado) {
        const confirmText = nuevoEstado === 'aprobada' 
          ? '¿Confirmar APROBACIÓN de esta solicitud?' 
          : '¿Confirmar RECHAZO de esta solicitud?';
        
        const confirmarBtn = document.createElement('div');
        confirmarBtn.style.cssText = 'position: fixed; top: 50%; left: 50%; transform: translate(-50%, -50%); background: white; padding: 30px; border-radius: 12px; box-shadow: 0 10px 40px rgba(0,0,0,0.3); z-index: 10000; text-align: center;';
        confirmarBtn.innerHTML = `
          <p style="margin: 0 0 20px 0; font-size: 18px; color: #0d2447;">${confirmText}</p>
          <button onclick="confirmarProceso('${solicitudId}', '${nuevoEstado}')" class="btn btn-primary" style="width: auto; margin-right: 10px;">Sí, confirmar</button>
          <button onclick="this.parentElement.remove()" class="btn btn-secondary" style="width: auto;">Cancelar</button>
        `;
        document.body.appendChild(confirmarBtn);
      };

      window.confirmarProceso = async function(solicitudId, nuevoEstado) {
        const solicitud = allData.solicitudes.find(s => s.id === solicitudId);
        if (solicitud) {
          solicitud.estado = nuevoEstado;
          solicitud.fecha_aprobacion = new Date().toISOString().split('T')[0];
          
          await saveDataToSheets('updateSolicitud', solicitud);
        }
        
        document.querySelectorAll('div[style*="position: fixed"]').forEach(el => el.remove());
        
        showToast(`✅ Solicitud ${nuevoEstado === 'aprobada' ? 'aprobada' : 'rechazada'} correctamente`, 'success');
      };

      // Modales
      window.openVacationModal = function() {
        document.getElementById('vacationModal').classList.add('active');
        document.getElementById('vacationForm').reset();
        document.getElementById('vacationStart').min = today;
        document.getElementById('vacationEnd').min = today;
      };

      window.closeVacationModal = function() {
        document.getElementById('vacationModal').classList.remove('active');
      };

      window.openPermissionModal = function() {
        document.getElementById('permissionModal').classList.add('active');
        document.getElementById('permissionForm').reset();
        document.getElementById('permissionDate').min = today;
      };

      window.closePermissionModal = function() {
        document.getElementById('permissionModal').classList.remove('active');
      };

      window.showSolicitudDetail = function(solicitudId) {
        const solicitud = allData.solicitudes.find(s => s.id === solicitudId);
        if (!solicitud) return;
        
        currentDetailSolicitud = solicitud;
        
        const content = document.getElementById('detailContent');
        const estadoClass = `badge-${solicitud.estado}`;
        const estadoTexto = solicitud.estado.charAt(0).toUpperCase() + solicitud.estado.slice(1);
        
        let detalles = '';
        if (solicitud.tipo === 'vacaciones') {
          detalles = `
            <div class="form-group">
              <label>Período</label>
              <p style="margin: 0; padding: 12px; background: #f8fafc; border-radius: 8px;">
                ${formatDate(solicitud.fecha_inicio)} - ${formatDate(solicitud.fecha_fin)}
              </p>
            </div>
            <div class="form-group">
              <label>Días Hábiles</label>
              <p style="margin: 0; padding: 12px; background: #f8fafc; border-radius: 8px;">
                ${solicitud.dias} días
              </p>
            </div>
          `;
        } else {
          detalles = `
            <div class="form-group">
              <label>Fecha</label>
              <p style="margin: 0; padding: 12px; background: #f8fafc; border-radius: 8px;">
                ${formatDate(solicitud.fecha_inicio)}
              </p>
            </div>
            <div class="form-group">
              <label>Tipo de Permiso</label>
              <p style="margin: 0; padding: 12px; background: #f8fafc; border-radius: 8px;">
                ${solicitud.tipo_permiso || 'N/A'}
              </p>
            </div>
          `;
        }
        
        content.innerHTML = `
          <div class="form-group">
            <label>Estado</label>
            <p style="margin: 0;"><span class="badge ${estadoClass}">${estadoTexto}</span></p>
          </div>
          <div class="form-group">
            <label>Fecha de Solicitud</label>
            <p style="margin: 0; padding: 12px; background: #f8fafc; border-radius: 8px;">
              ${formatDate(solicitud.fecha_solicitud)}
            </p>
          </div>
          ${detalles}
          ${solicitud.observaciones ? `
            <div class="form-group">
              <label>Observaciones</label>
              <p style="margin: 0; padding: 12px; background: #f8fafc; border-radius: 8px;">
                ${solicitud.observaciones}
              </p>
            </div>
          ` : ''}
        `;
        
        loadComments(solicitudId);
        
        document.getElementById('detailModal').classList.add('active');
      };

      window.closeDetailModal = function() {
        document.getElementById('detailModal').classList.remove('active');
        currentDetailSolicitud = null;
      };

      function loadComments(solicitudId) {
        const commentsList = document.getElementById('commentsList');
        commentsList.innerHTML = `
          <div class="comment">
            <div class="comment-header">
              <span class="comment-author">Sistema</span>
              <span class="comment-date">${formatDate(new Date().toISOString().split('T')[0])}</span>
            </div>
            <div class="comment-text">Solicitud registrada correctamente</div>
          </div>
        `;
      }

      window.addComment = function() {
        const commentText = document.getElementById('newComment').value.trim();
        if (!commentText) {
          showToast('Ingrese un comentario', 'error');
          return;
        }
        
        showToast('Comentario agregado', 'success');
        document.getElementById('newComment').value = '';
        loadComments(currentDetailSolicitud.id);
      };

      // Calendario
      window.showCalendar = function() {
        const calendarContent = document.getElementById('calendarContent');
        
        let html = '<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px;">';
        
        const meses = ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 
                       'Julio', 'Agosto', 'Septiembre', 'Octubre', 'Noviembre', 'Diciembre'];
        
        meses.forEach((mes, index) => {
          html += `
            <div class="card" style="padding: 20px;">
              <h4 style="margin: 0 0 15px 0; color: #0d2447; text-align: center;">${mes} 2026</h4>
              <div class="calendar-grid">
                <div class="calendar-day header">D</div>
                <div class="calendar-day header">L</div>
                <div class="calendar-day header">M</div>
                <div class="calendar-day header">M</div>
                <div class="calendar-day header">J</div>
                <div class="calendar-day header">V</div>
                <div class="calendar-day header">S</div>
              `;
          
          for (let i = 1; i <= 31; i++) {
            const isVacation = Math.random() > 0.9;
            const isHoliday = Math.random() > 0.95;
            const classes = isVacation ? 'vacation' : isHoliday ? 'holiday' : '';
            html += `<div class="calendar-day ${classes}">${i}</div>`;
          }
          
          html += `</div></div>`;
        });
        
        html += '</div>';
        html += `
          <div style="margin-top: 20px; display: flex; gap: 20px; justify-content: center; flex-wrap: wrap;">
            <div style="display: flex; align-items: center; gap: 8px;">
              <div style="width: 20px; height: 20px; background: #10b981; border-radius: 4px;"></div>
              <span>Vacaciones Aprobadas</span>
            </div>
            <div style="display: flex; align-items: center; gap: 8px;">
              <div style="width: 20px; height: 20px; background: #ef4444; border-radius: 4px;"></div>
              <span>Días Festivos</span>
            </div>
            <div style="display: flex; align-items: center; gap: 8px;">
              <div style="width: 20px; height: 20px; background: #2a5298; border-radius: 4px;"></div>
              <span>Hoy</span>
            </div>
          </div>
        `;
        
        calendarContent.innerHTML = html;
        document.getElementById('calendarModal').classList.add('active');
      };

      window.closeCalendarModal = function() {
        document.getElementById('calendarModal').classList.remove('active');
      };

      // Exportar reportes
      window.exportReport = function() {
        const solicitudes = allData.solicitudes.filter(s => 
          s.medico_documento === currentUser.documento
        );
        
        let csv = 'Tipo,Fecha Solicitud,Fecha Inicio,Fecha Fin,Días,Estado,Observaciones\n';
        
        solicitudes.forEach(sol => {
          csv += `${sol.tipo},${sol.fecha_solicitud},${sol.fecha_inicio},${sol.fecha_fin || ''},${sol.dias || ''},${sol.estado},"${sol.observaciones || ''}"\n`;
        });
        
        downloadCSV(csv, `reporte_vacaciones_${currentUser.documento}_${new Date().toISOString().split('T')[0]}.csv`);
        showToast('Reporte exportado correctamente', 'success');
      };

      window.exportJefeReport = function() {
        let csv = 'Médico,Documento,Especialidad,Tipo,Fecha Solicitud,Período,Días,Estado\n';
        
        allData.solicitudes.forEach(sol => {
          const medico = allData.medicos.find(m => m.documento === sol.medico_documento);
          const nombreMedico = medico ? `${medico.nombre} ${medico.apellido}` : 'Desconocido';
          const especialidad = medico?.especialidad || 'N/A';
          const periodo = sol.tipo === 'vacaciones' 
            ? `${sol.fecha_inicio} - ${sol.fecha_fin}`
            : sol.fecha_inicio;
          
          csv += `"${nombreMedico}",${sol.medico_documento},${especialidad},${sol.tipo},${sol.fecha_solicitud},"${periodo}",${sol.dias || ''},${sol.estado}\n`;
        });
        
        downloadCSV(csv, `reporte_general_${new Date().toISOString().split('T')[0]}.csv`);
        showToast('Reporte general exportado', 'success');
      };

      function downloadCSV(csv, filename) {
        const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
        const link = document.createElement('a');
        const url = URL.createObjectURL(blob);
        link.setAttribute('href', url);
        link.setAttribute('download', filename);
        link.style.visibility = 'hidden';
        document.body.appendChild(link);
        link.click();
        document.body.removeChild(link);
      }

      // Calcular días
      document.getElementById('vacationStart').addEventListener('change', calculateDays);
      document.getElementById('vacationEnd').addEventListener('change', calculateDays);

      function calculateDays() {
        const start = document.getElementById('vacationStart').value;
        const end = document.getElementById('vacationEnd').value;
        
        if (start && end) {
          const startDate = new Date(start);
          const endDate = new Date(end);
          
          if (endDate < startDate) {
            showToast('La fecha de fin debe ser posterior a la de inicio', 'error');
            document.getElementById('vacationDays').value = '';
            return;
          }
          
          let dias = 0;
          let currentDate = new Date(startDate);
          
          while (currentDate <= endDate) {
            const dayOfWeek = currentDate.getDay();
            const dateStr = currentDate.toISOString().split('T')[0];
            const esFestivo = allData.festivos.some(f => f.fecha === dateStr);
            
            if (dayOfWeek !== 0 && dayOfWeek !== 6 && !esFestivo) {
              dias++;
            }
            
            currentDate.setDate(currentDate.getDate() + 1);
          }
          
          document.getElementById('vacationDays').value = dias;
        }
      }

      // Enviar solicitudes
      window.submitVacation = async function(event) {
        event.preventDefault();
        
        const start = document.getElementById('vacationStart').value;
        const end = document.getElementById('vacationEnd').value;
        const dias = document.getElementById('vacationDays').value;
        const observaciones = document.getElementById('vacationObservations').value;
        
        if (!dias || dias === '0') {
          showToast('Debe seleccionar fechas válidas', 'error');
          return;
        }

        const solicitud = {
          id: generateId(),
          medico_documento: currentUser.documento,
          tipo: 'vacaciones',
          fecha_inicio: start,
          fecha_fin: end,
          dias: dias,
          observaciones: observaciones,
          estado: 'pendiente',
          fecha_solicitud: new Date().toISOString().split('T')[0]
        };

        const result = await saveDataToSheets('addSolicitud', solicitud);
        
        if (result.success) {
          showToast('✅ Solicitud de vacaciones enviada exitosamente', 'success');
          closeVacationModal();
        }
      };

      window.submitPermission = async function(event) {
        event.preventDefault();
        
        const fecha = document.getElementById('permissionDate').value;
        const tipo = document.getElementById('permissionType').value;
        const observaciones = document.getElementById('permissionObservations').value;

        const solicitud = {
          id: generateId(),
          medico_documento: currentUser.documento,
          tipo: 'permiso',
          fecha_inicio: fecha,
          fecha_fin: fecha,
          tipo_permiso: tipo,
          observaciones: observaciones,
          estado: 'pendiente',
          fecha_solicitud: new Date().toISOString().split('T')[0]
        };

        const result = await saveDataToSheets('addSolicitud', solicitud);
        
        if (result.success) {
          showToast('✅ Solicitud de permiso enviada exitosamente', 'success');
          closePermissionModal();
        }
      };

      // Utilidades
      function generateId() {
        return 'SOL_' + Date.now() + '_' + Math.random().toString(36).substr(2, 9);
      }

      function formatDate(dateStr) {
        if (!dateStr) return 'N/A';
        const date = new Date(dateStr + 'T00:00:00');
        const opciones = { year: 'numeric', month: 'long', day: 'numeric' };
        return date.toLocaleDateString('es-ES', opciones);
      }

      function showToast(message, type = 'success') {
        const toast = document.getElementById('toast');
        toast.textContent = message;
        toast.className = `toast ${type} active`;
        
        setTimeout(() => {
          toast.classList.remove('active');
        }, 4000);
      }
    })();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9a6e952a106552aa',t:'MTc2NDU1MDE0NS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
