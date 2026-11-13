# Reflexión — Clase 2: SQL Connect

### 1. ¿Qué es IDOR y cómo lo evita auth.uid?
IDOR es una vulnerabilidad que permite acceder a datos de otros usuarios modificando un identificador. `auth.uid` lo evita utilizando la identidad del usuario autenticado, sin confiar en un ID enviado por el cliente.

### 2. ¿Por qué ListCursos es PUBLIC y ListAlumnos NO_ACCESS?
Porque los cursos son información pública, mientras que los alumnos tienen datos personales. Un panel de administración necesitaría operaciones específicas con permisos de administrador.

### 3. ¿Qué ventaja tiene una clave primaria compuesta?
Impide que un alumno se inscriba dos veces al mismo curso. La restricción se aplica directamente en la base de datos.

### 4. ¿Por qué la configuración de Firebase es pública?
Porque conocer la configuración no otorga permisos para acceder a los datos. La seguridad depende de la autenticación y autorización. App Check agrega protección contra clientes no autorizados.

### 5. ¿Qué ventajas y desventajas tiene SQL Connect frente a REST?
SQL Connect genera una API y permite definir autorizaciones sin desarrollar un backend propio. Como desventaja, ofrece menos flexibilidad para implementar lógica personalizada.

### 6. ¿Por qué modificamos la CSP?
Porque la aplicación necesita comunicarse con los servicios de Firebase. Agregamos dominios específicos en `connect-src` para permitir esas conexiones sin habilitar cualquier origen.

### Auditoría de seguridad

Se ejecutó `npm run atacar` utilizando los emuladores locales.

**Resultado final:**
- Catálogo público accesible.
- Datos personales protegidos.
- Inscripciones anónimas rechazadas.
- Inscripciones duplicadas evitadas.
- Aislamiento entre usuarios verificado.
- Baja de inscripciones ajenas bloqueada.

