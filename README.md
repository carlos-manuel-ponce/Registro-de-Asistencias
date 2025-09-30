# 📋 Registro de Asistencias

Sistema web para el control y seguimiento de asistencia en tiempo real con **209 asientos** organizados en un plano interactivo.

## ✨ Características

- 🎯 **Plano interactivo** con 209 asientos organizados en filas A-U
- 🔍 **Búsqueda por DNI** para localizar asistentes rápidamente
- ✅ **Registro de asistencia** con actualización en tiempo real
- 📱 **Diseño responsive** optimizado para móviles y tablets
- 🔄 **Sincronización en tiempo real** entre múltiples usuarios
- 💾 **Base de datos Supabase** para persistencia de datos

## 🚀 Tecnologías

- **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
- **Backend**: Supabase (PostgreSQL + Realtime)
- **Responsive**: CSS Grid + Flexbox
- **PWA Ready**: Optimizado para dispositivos móviles

## 📱 Características Móviles

- **Touch-friendly**: Botones de 44px mínimo
- **Diseño adaptativo**: 
  - Desktop: 10 asientos por fila
  - Tablet: 5 asientos por fila  
  - Móvil: 4 asientos por fila
- **Modal responsive** al 95% de la pantalla
- **Búsqueda optimizada** para dispositivos táctiles

## 🛠️ Configuración

### 1. Base de datos Supabase

Ejecuta este SQL en tu panel de Supabase:

```sql
CREATE TABLE asistencia (
    id SERIAL PRIMARY KEY,
    region VARCHAR(100) NOT NULL,
    establecimiento VARCHAR(200) NOT NULL,
    cargo VARCHAR(100) NOT NULL,
    aspirante VARCHAR(150) NOT NULL,
    dni VARCHAR(20) NOT NULL UNIQUE,
    asiento INTEGER NOT NULL UNIQUE CHECK (asiento >= 1 AND asiento <= 209),
    presente BOOLEAN DEFAULT FALSE,
    fecha_registro TIMESTAMP DEFAULT NOW(),
    fecha_asistencia TIMESTAMP NULL
);

CREATE INDEX idx_asistencia_dni ON asistencia(dni);
CREATE INDEX idx_asistencia_asiento ON asistencia(asiento);
CREATE INDEX idx_asistencia_presente ON asistencia(presente);
```

### 2. Configuración de la aplicación

1. Abre `index.html` en tu editor
2. Reemplaza las credenciales de Supabase:
   ```javascript
   const SUPABASE_URL = 'tu-url-de-supabase';
   const SUPABASE_KEY = 'tu-api-key-publica';
   ```

### 3. Datos de ejemplo

```sql
INSERT INTO asistencia (region, establecimiento, cargo, aspirante, dni, asiento) VALUES
('Buenos Aires', 'Escuela Primaria N°1', 'Maestro', 'Juan Pérez', '12345678', 15),
('Córdoba', 'Colegio San José', 'Profesor', 'María García', '87654321', 42),
('Santa Fe', 'Instituto Nacional', 'Director', 'Carlos López', '11111111', 78);
```

## 🎯 Uso

### Para Operadores:

1. **Buscar asistente**: Ingresa el DNI en el buscador
2. **Ver detalles**: Haz clic en cualquier asiento para ver información
3. **Marcar presente**: Usa el botón "Dar Asistencia" en el modal
4. **Visualización**: Los asientos presentes se marcan en verde

### Para Administradores:

- **Múltiples operadores** pueden usar la aplicación simultáneamente
- **Cambios en tiempo real** se reflejan en todas las pantallas
- **Datos persistentes** en base de datos Supabase

## 📊 Estructura del Plano

```
   1  2  3  4  5  6  7  8  9  10     101 102 103 104 105 106 107 108 109 110
A  •  •  •  •  •  •  •  •  •  •   K   •   •   •   •   •   •   •   •   •   •
B  •  •  •  •  •  •  •  •  •  •   L   •   •   •   •   •   •   •   •   •   •
C  •  •  •  •  •  •  •  •  •  •   M   •   •   •   •   •   •   •   •   •   •
...                               ...
J  •  •  •  •  •  •  •  •  •  •   U   •   •   •   •   •   •   •   •   • (209)
```

## 🔄 Tiempo Real

La aplicación utiliza **Supabase Realtime** para:

- ✅ Sincronizar cambios entre usuarios
- ✅ Actualizar estados de asistencia automáticamente  
- ✅ Mostrar indicadores de conexión
- ✅ Manejar errores de red graciosamente

## 📱 Compatibilidad

- ✅ Chrome/Edge 88+
- ✅ Firefox 85+
- ✅ Safari 14+
- ✅ Chrome Mobile
- ✅ Safari Mobile
- ✅ Samsung Internet

## 🚀 Despliegue

### Opción 1: Archivo estático
Sube `index.html` a cualquier hosting web (Netlify, Vercel, GitHub Pages)

### Opción 2: Servidor local
```bash
python -m http.server 8000
# Abre http://localhost:8000
```

## 🤝 Contribuir

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. Commit tus cambios (`git commit -m 'Agrega nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Abre un Pull Request

## 📄 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para detalles.

## 📞 Soporte

Para reportar bugs o solicitar features, abre un [issue](https://github.com/carlos-manuel-ponce/Registro-de-Asistencias/issues) en GitHub.

---

**Desarrollado con ❤️ para facilitar el control de asistencias**
