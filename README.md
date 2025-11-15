# ChatiAV (ChatBull) - Sistema de Chat en Vivo Profesional

## 📋 Descripción

Sistema completo de chat en vivo (Live Chat) para sitios web desarrollado con CodeIgniter 3 y AngularJS. Permite comunicación en tiempo real entre visitantes y agentes de soporte con panel de administración, gestión multi-sitio, mensajes enlatados, etiquetado de usuarios y notificaciones push para Android/iOS.

**Producto Comercial:** ChatBull by G-Axon (v5.1.8)

## 🚀 Tipo de Proyecto

**Aplicación Web SaaS** - Plataforma de Live Chat Multi-Site

## 🛠️ Stack Tecnológico

**Backend:**
- PHP 5.6+ (5.3.7 minimum)
- CodeIgniter 3.x (MVC Framework)
- MySQL/MySQLi (utf8mb4)
- Autenticación basada en sesiones + MD5

**Frontend:**
- AngularJS 1.x
- Angular UI Bootstrap 2.5.0
- jQuery
- Bootstrap + Font Awesome
- Bower (gestor de paquetes)

**Características Avanzadas:**
- Google Cloud Messaging (GCM)
- Google Maps API
- Service Worker para notificaciones
- TinyMCE WYSIWYG Editor

## 🏗️ Arquitectura

**Patrón MVC con Controladores Base Extendidos:**

```
CI_Controller
└── CP_Controller (Base)
    ├── CP_AdminController (Admin/Agent pages con auth)
    ├── CP_AgentController (Agentes)
    ├── CP_VisitorController (Visitantes)
    └── CP_AppController (Aplicación)

CP_Model (Base Model)
└── Modelos de negocio (Chat_message, User, etc.)

CP_Config (Base Config)
└── Configuración extendida
```

## 📁 Estructura del Proyecto

```
application/
├── controllers/          → 28 controladores (5 carpetas)
│   ├── Admin/           → Gestión general
│   ├── agents/          → Dashboard de agentes
│   ├── api/             → RESTful API
│   ├── desktop/         → Interfaz desktop
│   └── visitors/        → Widget visitantes
├── models/              → 18 modelos
├── views/               → 78 vistas PHP
│   ├── agents/          → Panel agentes
│   ├── canned-messages/ → Mensajes rápidos
│   └── cmodule/         → Módulo chat principal
├── core/                → Controladores base (CP_*)
├── libraries/           → Authentication, Media, Curl
├── helpers/             → common, notifications, URL
├── migrations/          → 36 migraciones
└── config/              → Configuración

assets/
├── cmodule/             → Módulo chat principal
├── cmodule-chat/        → Componente chat avanzado
└── angular-*/           → Componentes AngularJS
```

## ✨ Características Principales

### 💬 Chat en Tiempo Real
- Widget embebible (iframe/script)
- Múltiples conversaciones simultáneas
- Chat anónimo soportado
- Historial completo de conversaciones
- Estados online/offline/away
- Typing indicators

### 🎯 Panel de Agentes
- Dashboard con métricas (Flot charts)
- Gestión de solicitudes entrantes
- Mensajes enlatados (respuestas rápidas)
- Forwarding (reenvío de chats)
- Cambio de disponibilidad
- Estadísticas de rendimiento

### 👨‍💼 Administración
- Gestión de usuarios (admin/agentes)
- Sistema de permisos y roles
- Tags para categorización
- Configuración multi-idioma
- Personalización (colores, logos)
- Feedback de usuarios
- Solicitudes offline
- Analytics con Google Maps

### 📱 Visitantes
- Formulario de inicio chat
- Interface responsive
- Emojis/smilies
- Subida de archivos
- Notificaciones push (GCM)
- Pre-chat surveys

### 🌐 Multi-Sitio
- Gestión de múltiples sitios
- Asignación de usuarios por sitio
- Configuración independiente
- Analytics por sitio

### 🔌 API REST
- Integración externa
- Endpoints documentados
- Tokens de acceso
- AJAX para tiempo real

## 🗄️ Base de Datos

**25 Tablas** (prefijo: `chatbull_`):

| Tabla | Descripción |
|-------|-------------|
| users | Cuentas de admin/agentes |
| chat_sessions | Conversaciones |
| chat_users | Participantes en sesiones |
| chat_messages | Mensajes individuales |
| chat_requests | Sistema de solicitudes |
| canned_messages | Respuestas pre-escritas |
| tags, user_tags | Sistema de etiquetado |
| offline_requests | Solicitudes fuera de horario |
| feedback | Reviews de usuarios |
| notifications | Sistema de notificaciones |
| temp_visitors | Tracking temporal |
| anonymous_messages | Chats anónimos |
| daily_pageviews | Analytics - pageviews |
| daily_visitors | Analytics - visitantes |
| gcm_users | Tokens dispositivos móviles |
| sites, users_to_sites | Multi-sitio |

## 🔧 Instalación

```bash
# 1. Clonar repositorio
git clone https://github.com/dannyggg3/chatiav.git
cd chatiav

# 2. Configurar base de datos
# Editar application/config/database.php
$db['default'] = array(
    'hostname' => 'localhost',
    'username' => 'root',
    'password' => '',
    'database' => 'chatbull_db'
);

# 3. Importar base de datos
# Ejecutar migraciones o script SQL (25 tablas)

# 4. Configurar aplicación
# Editar application/config/config.php
$config['base_url'] = 'https://tudominio.com/';

# 5. Permisos
chmod -R 755 assets/
chmod -R 777 uploads/

# 6. Servidor web
# DocumentRoot: /ruta/chatiav
# Habilitar mod_rewrite (Apache)
```

## 💻 Uso

### Widget Embebido

```html
<!-- En tu sitio web -->
<script src="https://tudominio.com/assets/cmodule-chat/js/chatbox.js"></script>
<script>
  ChatBull.init({
    domain: 'https://tudominio.com',
    token: 'TU_TOKEN_API',
    position: 'bottom-right'
  });
</script>
```

### Acceso al Panel

- **Admin:** `/admin` (credenciales por defecto en instalación)
- **Agentes:** `/agents/login`
- **API:** `/api/v1/...`

### Notificaciones Push (GCM)

```php
// Keys configuradas:
Android: AIzaSyA9zbei2gZAXvJ8fAYw4u_s6thfIl4pwMg
iOS: AIzaSyB9thCSXGZCpAe8eRa1CH9yha5Ll1zoczI
```

## 📊 Estadísticas del Proyecto

| Métrica | Valor |
|---------|-------|
| Controllers | 28 |
| Models | 18 |
| Views | 78 |
| Migrations | 36 |
| Tablas BD | 25 |
| Líneas código | ~15k+ |
| Framework | CodeIgniter 3 |
| Frontend | AngularJS 1.x |

## 🔒 Seguridad

**Implementado:**
- ✅ Tokens de autenticación
- ✅ Validación de datos (CodeIgniter)
- ✅ Sistema de permisos por rol
- ✅ Sesiones seguras
- ✅ CSRF protection
- ✅ Remember token (20 caracteres)

**Recomendaciones:**
- [ ] Actualizar hashing MD5 a bcrypt/Argon2
- [ ] Implementar HTTPS obligatorio
- [ ] Actualizar a PHP 7.4+
- [ ] Rate limiting en API
- [ ] Sanitización de archivos subidos

## 🚀 Características Técnicas

- AJAX para actualización en tiempo real
- Service Worker para notificaciones offline
- Google Cloud Messaging (Android/iOS)
- AngularJS para interfaz dinámica
- 25 colores predefinidos para perfiles
- Sistema de instalación wizard
- Migraciones de base de datos
- Custom routing con CodeIgniter
- Media library con thumbnails

## 🎨 Personalización

El sistema permite personalizar:
- Colores del widget
- Logo y branding
- Idiomas (multi-language)
- Mensajes de bienvenida
- Campos de formulario pre-chat
- Email templates
- Configuración de horarios

## 🧪 Testing

```bash
# No incluye tests automatizados
# Se recomienda implementar PHPUnit
```

## 📈 Mejoras Futuras

- Migrar a CodeIgniter 4
- Implementar WebSockets real (Socket.IO)
- Actualizar AngularJS a Vue.js/React
- Sistema de reportes avanzado
- Integración con CRM
- Video/Audio chat
- Chatbots con IA

## 🛠️ Troubleshooting

| Problema | Solución |
|----------|----------|
| Chat no conecta | Verificar base_url en config.php |
| Notificaciones no llegan | Validar GCM keys y permisos |
| Error 404 en rutas | Habilitar mod_rewrite en Apache |
| Widget no carga | Verificar CORS y base_url |

## 📚 Referencias

- [CodeIgniter 3 Documentation](https://codeigniter.com/userguide3/)
- [AngularJS Guide](https://docs.angularjs.org/guide)
- [Google Cloud Messaging](https://firebase.google.com/docs/cloud-messaging)

## 📄 Licencia

Producto comercial - ChatBull by G-Axon. Repositorio parte del portafolio de dannyggg3.

## 👤 Autor

**dannyggg3** - [@dannyggg3](https://github.com/dannyggg3)

---

⭐ Sistema profesional de soporte al cliente en tiempo real con capacidades multi-sitio y multi-idioma
