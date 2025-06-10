<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "2aa9dbc165e104764fa57e8a0d3f1c73",
  "translation_date": "2025-06-10T05:29:38+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab1/README.md",
  "language_code": "cs"
}
-->
# 🚀 Module 1: Fundamentos del AI Toolkit

[![Duration](https://img.shields.io/badge/Duration-15%20minutes-blue.svg)]()
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green.svg)]()
[![Prerequisites](https://img.shields.io/badge/Prerequisites-VS%20Code-orange.svg)]()

## 📋 Objetivos de Aprendizaje

Al finalizar este módulo, podrás:
- ✅ Instalar y configurar AI Toolkit para Visual Studio Code
- ✅ Navegar por el Catálogo de Modelos y entender las diferentes fuentes de modelos
- ✅ Usar el Playground para probar y experimentar con modelos
- ✅ Crear agentes AI personalizados usando Agent Builder
- ✅ Comparar el rendimiento de modelos entre distintos proveedores
- ✅ Aplicar las mejores prácticas en ingeniería de prompts

## 🧠 Introducción al AI Toolkit (AITK)

El **AI Toolkit para Visual Studio Code** es la extensión principal de Microsoft que transforma VS Code en un entorno completo para desarrollo de IA. Cierra la brecha entre la investigación en IA y el desarrollo práctico, haciendo que la IA generativa sea accesible para desarrolladores de todos los niveles.

### 🌟 Capacidades Clave

| Característica | Descripción | Caso de Uso |
|----------------|-------------|-------------|
| **🗂️ Catálogo de Modelos** | Acceso a más de 100 modelos de GitHub, ONNX, OpenAI, Anthropic, Google | Descubrimiento y selección de modelos |
| **🔌 Soporte BYOM** | Integra tus propios modelos (locales o remotos) | Despliegue de modelos personalizados |
| **🎮 Playground Interactivo** | Pruebas en tiempo real con interfaz de chat | Prototipado y pruebas rápidas |
| **📎 Soporte Multimodal** | Manejo de texto, imágenes y archivos adjuntos | Aplicaciones de IA complejas |
| **⚡ Procesamiento por Lotes** | Ejecuta múltiples prompts simultáneamente | Flujos de trabajo de prueba eficientes |
| **📊 Evaluación de Modelos** | Métricas integradas (F1, relevancia, similitud, coherencia) | Evaluación de desempeño |

### 🎯 Por qué AI Toolkit es Importante

- **🚀 Desarrollo Acelerado**: De la idea al prototipo en minutos
- **🔄 Flujo de Trabajo Unificado**: Una sola interfaz para múltiples proveedores de IA
- **🧪 Experimentación Sencilla**: Compara modelos sin configuraciones complejas
- **📈 Listo para Producción**: Transición fluida de prototipo a despliegue

## 🛠️ Requisitos Previos y Configuración

### 📦 Instalar la Extensión AI Toolkit

**Paso 1: Acceder al Marketplace de Extensiones**
1. Abre Visual Studio Code
2. Ve a la vista de Extensiones (`Ctrl+Shift+X` o `Cmd+Shift+X`)
3. Busca "AI Toolkit"

**Paso 2: Elige tu Versión**
- **🟢 Release**: Recomendado para uso en producción
- **🔶 Pre-release**: Acceso anticipado a funciones innovadoras

**Paso 3: Instalar y Activar**

![AI Toolkit Extension](../../../../translated_images/aitkext.d28945a03eed003c39fc39bc96ae655af9b64b9b922e78e88b07214420ed7985.cs.png)

### ✅ Lista de Verificación para Verificación
- [ ] El ícono de AI Toolkit aparece en la barra lateral de VS Code
- [ ] La extensión está habilitada y activada
- [ ] No hay errores de instalación en el panel de salida

## 🧪 Ejercicio Práctico 1: Explorando Modelos de GitHub

**🎯 Objetivo**: Dominar el Catálogo de Modelos y probar tu primer modelo AI

### 📊 Paso 1: Navegar el Catálogo de Modelos

El Catálogo de Modelos es tu puerta de entrada al ecosistema de IA. Reúne modelos de varios proveedores, facilitando su descubrimiento y comparación.

**🔍 Guía de Navegación:**

Haz clic en **MODELOS - Catálogo** en la barra lateral de AI Toolkit

![Model Catalog](../../../../translated_images/aimodel.263ed2be013d8fb0e2265c4f742cfe490f6f00eca5e132ec50438c8e826e34ed.cs.png)

**💡 Consejo**: Busca modelos con capacidades específicas que se ajusten a tu caso de uso (por ejemplo, generación de código, escritura creativa, análisis).

**⚠️ Nota**: Los modelos alojados en GitHub (GitHub Models) son gratuitos pero tienen límites en la cantidad de solicitudes y tokens. Para acceder a modelos externos (como los alojados en Azure AI u otros endpoints), deberás proporcionar la clave API o autenticación correspondiente.

### 🚀 Paso 2: Añadir y Configurar tu Primer Modelo

**Estrategia de Selección de Modelo:**
- **GPT-4.1**: Ideal para razonamiento complejo y análisis
- **Phi-4-mini**: Ligero y rápido para tareas sencillas

**🔧 Proceso de Configuración:**
1. Selecciona **OpenAI GPT-4.1** en el catálogo
2. Haz clic en **Agregar a Mis Modelos** para registrarlo
3. Elige **Probar en Playground** para abrir el entorno de pruebas
4. Espera la inicialización del modelo (la primera vez puede tardar un poco)

![Playground Setup](../../../../translated_images/playground.dd6f5141344878ca4d4f3de819775da7b113518941accf37c291117c602f85db.cs.png)

**⚙️ Parámetros del Modelo:**
- **Temperature**: Controla la creatividad (0 = determinista, 1 = creativo)
- **Max Tokens**: Longitud máxima de la respuesta
- **Top-p**: Muestreo de núcleo para diversidad en respuestas

### 🎯 Paso 3: Domina la Interfaz del Playground

El Playground es tu laboratorio de experimentación con IA. Así puedes sacarle el máximo provecho:

**🎨 Mejores Prácticas para Ingeniería de Prompts:**
1. **Sé Específico**: Instrucciones claras y detalladas producen mejores resultados
2. **Proporciona Contexto**: Incluye información relevante de fondo
3. **Usa Ejemplos**: Muestra al modelo lo que deseas con ejemplos
4. **Itera**: Ajusta los prompts según los resultados iniciales

**🧪 Escenarios de Prueba:**
```markdown
# Example 1: Code Generation
"Write a Python function that calculates the factorial of a number using recursion. Include error handling and docstrings."

# Example 2: Creative Writing
"Write a professional email to a client explaining a project delay, maintaining a positive tone while being transparent about challenges."

# Example 3: Data Analysis
"Analyze this sales data and provide insights: [paste your data]. Focus on trends, anomalies, and actionable recommendations."
```

![Testing Results](../../../../translated_images/result.1dfcf211fb359cf65902b09db191d3bfc65713ca15e279c1a30be213bb526949.cs.png)

### 🏆 Ejercicio Desafío: Comparación de Rendimiento de Modelos

**🎯 Meta**: Compara diferentes modelos usando los mismos prompts para entender sus fortalezas

**📋 Instrucciones:**
1. Añade **Phi-4-mini** a tu espacio de trabajo
2. Usa el mismo prompt para GPT-4.1 y Phi-4-mini

![set](../../../../translated_images/set.88132df189ecde2cbbda256c1841db5aac8e9bdeba1a4e343dfa031b9545d6c9.cs.png)

3. Compara calidad, velocidad y precisión de las respuestas
4. Documenta tus hallazgos en la sección de resultados

![Model Comparison](../../../../translated_images/compare.97746cd0f907495503c1fc217739f3890dc76ea5f6fd92379a6db0cc331feb58.cs.png)

**💡 Ideas Clave para Descubrir:**
- Cuándo usar LLM vs SLM
- Balance costo vs rendimiento
- Capacidades especializadas de cada modelo

## 🤖 Ejercicio Práctico 2: Creando Agentes Personalizados con Agent Builder

**🎯 Objetivo**: Crear agentes AI especializados para tareas y flujos de trabajo específicos

### 🏗️ Paso 1: Entendiendo Agent Builder

Agent Builder es donde AI Toolkit realmente destaca. Permite crear asistentes AI a medida que combinan el poder de grandes modelos de lenguaje con instrucciones personalizadas, parámetros específicos y conocimiento especializado.

**🧠 Componentes de la Arquitectura del Agente:**
- **Modelo Central**: El LLM base (GPT-4, Groks, Phi, etc.)
- **Prompt del Sistema**: Define la personalidad y comportamiento del agente
- **Parámetros**: Configuraciones finas para rendimiento óptimo
- **Integración de Herramientas**: Conexión con APIs externas y servicios MCP
- **Memoria**: Contexto de conversación y persistencia de sesión

![Agent Builder Interface](../../../../translated_images/agentbuilder.25895b2d2f8c02e7aa99dd40e105877a6f1db8f0441180087e39db67744b361f.cs.png)

### ⚙️ Paso 2: Profundizando en la Configuración del Agente

**🎨 Creación de Prompts de Sistema Efectivos:**
```markdown
# Template Structure:
## Role Definition
You are a [specific role] with expertise in [domain].

## Capabilities
- List specific abilities
- Define scope of knowledge
- Clarify limitations

## Behavior Guidelines
- Response style (formal, casual, technical)
- Output format preferences
- Error handling approach

## Examples
Provide 2-3 examples of ideal interactions
```

*Por supuesto, también puedes usar Generate System Prompt para que la IA te ayude a crear y optimizar prompts*

**🔧 Optimización de Parámetros:**
| Parámetro | Rango Recomendado | Caso de Uso |
|-----------|-------------------|-------------|
| **Temperature** | 0.1-0.3 | Respuestas técnicas/factuales |
| **Temperature** | 0.7-0.9 | Tareas creativas/brainstorming |
| **Max Tokens** | 500-1000 | Respuestas concisas |
| **Max Tokens** | 2000-4000 | Explicaciones detalladas |

### 🐍 Paso 3: Ejercicio Práctico - Agente de Programación en Python

**🎯 Misión**: Crear un asistente especializado en codificación Python

**📋 Pasos de Configuración:**

1. **Selección de Modelo**: Elige **Claude 3.5 Sonnet** (excelente para código)

2. **Diseño del Prompt del Sistema**:
```markdown
# Python Programming Expert Agent

## Role
You are a senior Python developer with 10+ years of experience. You excel at writing clean, efficient, and well-documented Python code.

## Capabilities
- Write production-ready Python code
- Debug complex issues
- Explain code concepts clearly
- Suggest best practices and optimizations
- Provide complete working examples

## Response Format
- Always include docstrings
- Add inline comments for complex logic
- Suggest testing approaches
- Mention relevant libraries when applicable

## Code Quality Standards
- Follow PEP 8 style guidelines
- Use type hints where appropriate
- Handle exceptions gracefully
- Write readable, maintainable code
```

3. **Configuración de Parámetros**:
   - Temperature: 0.2 (para código consistente y confiable)
   - Max Tokens: 2000 (explicaciones detalladas)
   - Top-p: 0.9 (creatividad balanceada)

![Python Agent Configuration](../../../../translated_images/pythonagent.5e51b406401c165fcabfd66f2d943c27f46b5fed0f9fb73abefc9e91ca3489d4.cs.png)

### 🧪 Paso 4: Prueba de tu Agente Python

**Escenarios de Prueba:**
1. **Función Básica**: "Crea una función para encontrar números primos"
2. **Algoritmo Complejo**: "Implementa un árbol binario de búsqueda con métodos insertar, eliminar y buscar"
3. **Problema Real**: "Construye un web scraper que maneje limitación de tasa y reintentos"
4. **Depuración**: "Corrige este código [pega código con errores]"

**🏆 Criterios de Éxito:**
- ✅ El código funciona sin errores
- ✅ Incluye documentación adecuada
- ✅ Sigue las mejores prácticas de Python
- ✅ Ofrece explicaciones claras
- ✅ Sugiere mejoras

## 🎓 Resumen del Módulo 1 y Próximos Pasos

### 📊 Evaluación de Conocimientos

Pon a prueba lo aprendido:
- [ ] ¿Puedes explicar las diferencias entre los modelos del catálogo?
- [ ] ¿Has creado y probado un agente personalizado con éxito?
- [ ] ¿Sabes cómo optimizar parámetros para distintos casos de uso?
- [ ] ¿Puedes diseñar prompts de sistema efectivos?

### 📚 Recursos Adicionales

- **Documentación AI Toolkit**: [Official Microsoft Docs](https://github.com/microsoft/vscode-ai-toolkit)
- **Guía de Ingeniería de Prompts**: [Best Practices](https://platform.openai.com/docs/guides/prompt-engineering)
- **Modelos en AI Toolkit**: [Models in Develpment](https://github.com/microsoft/vscode-ai-toolkit/blob/main/doc/models.md)

**🎉 ¡Felicidades!** Has dominado los fundamentos del AI Toolkit y estás listo para crear aplicaciones AI más avanzadas.

### 🔜 Continúa al Siguiente Módulo

¿Listo para capacidades más avanzadas? Continúa a **[Módulo 2: MCP con Fundamentos de AI Toolkit](../lab2/README.md)** donde aprenderás a:
- Conectar tus agentes con herramientas externas usando Model Context Protocol (MCP)
- Crear agentes de automatización de navegador con Playwright
- Integrar servidores MCP con tus agentes AI Toolkit
- Potenciar tus agentes con datos y capacidades externas

**Prohlášení o vyloučení odpovědnosti**:  
Tento dokument byl přeložen pomocí AI překladatelské služby [Co-op Translator](https://github.com/Azure/co-op-translator). Přestože usilujeme o přesnost, mějte prosím na paměti, že automatizované překlady mohou obsahovat chyby nebo nepřesnosti. Originální dokument v jeho mateřském jazyce by měl být považován za autoritativní zdroj. Pro důležité informace se doporučuje profesionální lidský překlad. Nejsme odpovědní za jakékoliv nedorozumění nebo chybné výklady vzniklé použitím tohoto překladu.