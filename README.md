# Microservicio DevOps CI/CD

## Descripción
Este proyecto implementa un microservicio basado en Flask utilizando prácticas DevOps para automatizar el ciclo de vida del software mediante Git, GitHub, Docker, Docker Compose y GitHub Actions.
El objetivo es demostrar la integración continua (CI), la entrega continua (CD), la seguridad automatizada y la orquestación de contenedores en un entorno simulado.

# Modelos de Ramificación

## GitFlow
GitFlow es una estrategia de ramificación que utiliza ramas separadas para producción, desarrollo, nuevas funcionalidades y correcciones urgentes.

### Ventajas
- Separación clara entre desarrollo y producción.
- Facilita el trabajo colaborativo.
- Reduce riesgos al integrar cambios.
- Permite un mejor control de versiones.

### Uso recomendado
Proyectos colaborativos con múltiples desarrolladores y ciclos de desarrollo estructurados.

## GitHub Flow
GitHub Flow utiliza una única rama principal y ramas temporales para desarrollar cambios específicos.

### Ventajas
- Flujo simple y rápido.
- Fácil implementación.
- Integración continua de cambios.

### Uso recomendado
Proyectos pequeños o equipos con despliegues frecuentes.

## Trunk-Based Development
Consiste en integrar cambios continuamente sobre una rama principal compartida.

### Ventajas
- Favorece la integración continua.
- Reduce conflictos de integración.
- Permite ciclos de desarrollo rápidos.

### Uso recomendado
Equipos DevOps maduros con alta automatización.

# Comparación de Modelos

| Modelo | Ventajas | Uso recomendado |
|----------|----------|----------|
| GitFlow | Mayor control y organización | Proyectos colaborativos |
| GitHub Flow | Simplicidad y rapidez | Equipos pequeños |
| Trunk-Based | Integración continua constante | Equipos DevOps avanzados |

# Modelo Seleccionado
Para este proyecto se seleccionó GitFlow debido a que permite gestionar de forma organizada el trabajo colaborativo mediante ramas especializadas para desarrollo, funcionalidades y correcciones.
Además, facilita la trazabilidad de cambios, el control de versiones y la integración progresiva del código.

# Estrategia de Ramificación
Se implementó la siguiente estructura:
- `main`: Producción
- `develop`: Desarrollo
- `feature/login`
- `feature/register`
- `hotfix/error-login`

# Flujo de Trabajo DevOps
1. Crear rama feature desde develop.
2. Implementar funcionalidad.
3. Realizar commits siguiendo convenciones.
4. Crear Pull Request.
5. Ejecutar validaciones automáticas.
6. Aprobar cambios.
7. Realizar merge.
8. Ejecutar pipeline CI/CD.
9. Desplegar versión validada.

# Simulación Colaborativa
Durante el desarrollo se implementaron:
- Feature Login
- Feature Register
- Hotfix Error Login
Todas las integraciones fueron realizadas mediante Pull Requests.

# Pipeline CI/CD
El proyecto implementa un pipeline CI/CD automatizado utilizando GitHub Actions.

## Objetivos
- Automatizar validaciones.
- Garantizar calidad del código.
- Detectar vulnerabilidades.
- Automatizar despliegues.
- Mantener trazabilidad completa.

# Etapas del Pipeline

## 1. Construcción (Build)
Se valida que la aplicación pueda construirse correctamente.

## 2. Pruebas Automatizadas
Se ejecutan pruebas unitarias utilizando PyTest.

## 3. Análisis de Dependencias (SCA)
Se utiliza Dependabot para detectar dependencias vulnerables.

## 4. Análisis Estático de Seguridad (SAST)
Se utiliza CodeQL para analizar el código fuente y detectar posibles vulnerabilidades.

## 5. Construcción de Imagen Docker
Se genera automáticamente una imagen Docker del microservicio.

## 6. Despliegue Simulado
El pipeline ejecuta una etapa de despliegue automatizado simulando un entorno productivo.

# GitHub Actions
El pipeline se ejecuta automáticamente cuando:
- Se realiza un Push a la rama main.
- Se crea un Pull Request hacia main.

Archivo utilizado:
```text
.github/workflows/ci.yml
```

# Contenedorización con Docker
La aplicación se ejecuta dentro de un contenedor Docker.

## Beneficios
- Portabilidad.
- Consistencia entre ambientes.
- Facilidad de despliegue.
- Escalabilidad.

Archivo utilizado:
```text
Dockerfile
```

# Orquestación con Docker Compose
Para la simulación del entorno se utiliza Docker Compose.

Archivo utilizado:
```text
docker-compose.yml
```

## Servicios Implementados
### App
Microservicio principal desarrollado en Flask.

### Redis
Servicio auxiliar utilizado como caché.

## Características de Docker Compose

### Definición de Servicios
Se definen múltiples contenedores para representar el entorno completo.

### Redes Personalizadas
Los servicios se comunican mediante una red interna.

### Variables de Entorno
Se utilizan variables para facilitar la configuración.

### Exposición de Puertos
Se publica el servicio para acceso externo.

### Reinicio Automático
Los contenedores se reinician automáticamente en caso de fallos.

# Seguridad
La seguridad forma parte del pipeline CI/CD.

## Dependabot
Permite:
- Detectar dependencias vulnerables.
- Recomendar actualizaciones.
- Mantener paquetes actualizados.

Archivo:
```text
.github/dependabot.yml
```

## CodeQL
Realiza análisis estático del código.

Permite detectar:
- Vulnerabilidades potenciales.
- Problemas de calidad.
- Errores de seguridad.

Archivo:
```text
.github/workflows/codeql.yml
```
# Trazabilidad
La trazabilidad se garantiza mediante:
- Git.
- GitHub.
- Historial de commits.
- Pull Requests.
- GitHub Actions.
- Control de versiones.
- Registros de ejecución del pipeline.
Cada cambio queda documentado y asociado a una rama, commit y ejecución del pipeline.

# Guía de Buenas Prácticas DevOps

## Naming de Ramas
### Producción
```text
main
```

### Desarrollo
```text
develop
```

### Funcionalidades
```text
feature/nombre-funcionalidad
```
Ejemplo:
```text
feature/login
feature/register
```

### Correcciones
```text
hotfix/nombre-error
```

Ejemplo:
```text
hotfix/error-login
```
## Convenciones de Commits
### feat
Nueva funcionalidad.

Ejemplo:
```text
feat: agregar login de usuario
```

### fix
Corrección de errores.

Ejemplo:
```text
fix: corregir error de autenticación
```

### docs
Documentación.

Ejemplo:
```text
docs: actualizar README
```

### test
Pruebas.

Ejemplo:
```text
test: agregar pruebas unitarias
```

### ci
Integración continua.

Ejemplo:
```text
ci: agregar pipeline github actions
```

### security
Seguridad.

Ejemplo:
```text
security: agregar dependabot
```
## Estrategia de Merge
Todos los cambios deben integrarse mediante Pull Requests.
Antes de realizar un merge:
- Revisar código.
- Ejecutar pipeline.
- Validar pruebas.
- Verificar seguridad.

## Control de Versiones
Git permite:
- Mantener historial completo.
- Recuperar versiones anteriores.
- Auditar cambios.
- Facilitar trabajo colaborativo.

## Estructura del Proyecto
```text
microservicio-devops-ci-cd/
│
├── app.py
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── README.md
│
├── tests/
│   └── test_app.py
│
└── .github/
    ├── dependabot.yml
    │
    └── workflows/
        ├── ci.yml
        └── codeql.yml
```

# Tecnologías Utilizadas
- Git
- GitHub
- GitHub Actions
- Docker
- Docker Compose
- Python
- Flask
- PyTest
- Dependabot
- CodeQL

# Conclusión
Durante el desarrollo de esta evaluación pude comprender de mejor manera cómo funcionan las prácticas DevOps aplicadas a un proyecto real. Aprendí a utilizar GitFlow para organizar el trabajo mediante ramas de desarrollo, funcionalidades y correcciones, lo que permitió mantener un mejor control de los cambios realizados en el repositorio.

Además, adquirí experiencia en la creación de contenedores utilizando Docker y en la orquestación de servicios mediante Docker Compose. Esto me permitió entender cómo una aplicación puede ejecutarse de manera consistente en distintos entornos, facilitando su despliegue y mantenimiento.

Otro aprendizaje importante fue la implementación de un pipeline CI/CD con GitHub Actions. Gracias a esto comprendí la importancia de automatizar procesos como la ejecución de pruebas, el análisis de seguridad y la construcción de imágenes Docker, reduciendo errores manuales y mejorando la calidad del software.

También pude conocer herramientas de seguridad como Dependabot y CodeQL, las cuales ayudan a identificar vulnerabilidades y mantener un código más seguro y confiable. Estas herramientas demuestran cómo la seguridad puede integrarse desde las primeras etapas del desarrollo.

En mi caso, participé activamente en la configuración del repositorio, la documentación del proyecto, la implementación del pipeline CI/CD y la integración de los distintos componentes necesarios para cumplir los requisitos de la evaluación. Esta experiencia me permitió fortalecer mis conocimientos sobre automatización, control de versiones y trabajo colaborativo en un entorno DevOps.

Finalmente, considero que este proyecto fue una experiencia muy útil para comprender cómo se integran herramientas modernas de desarrollo, automatización y despliegue continuo, competencias que serán fundamentales para futuros proyectos profesionales en el área de informática y desarrollo de software.

(Esta sección debe ser redactada por los integrantes del equipo con sus propias palabras, describiendo los aprendizajes obtenidos durante el desarrollo del proyecto y su contribución individual.)
