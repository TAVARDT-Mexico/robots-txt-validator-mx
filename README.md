# Validador de Robots.txt y Gobernanza de Rastreadores

[![Validador Robots.txt](https://img.shields.io/badge/TAVARDT-Robots.txt-5b3cf5.svg)](https://tools.tavardt.com/mx/validador-robots-txt/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

El **TAVARDT Validador de Robots.txt** proporciona auditoría automatizada de directivas de rastreo, conformidad con la norma RFC 9309 y control de robots de inteligencia artificial para sitios web en México.

***

## Arquitectura del Protocolo y Matriz de Gobernanza

Los rastreadores de motores de búsqueda e inteligencias artificiales interpretan robots.txt para establecer límites de acceso e indexación. Errores de configuración como bloqueos globales involuntarios provocan la desindexación total de dominios y la pérdida de tráfico orgánico.

Esta herramienta analiza la sintaxis de las directivas, detecta valores desmedidos de crawl-delay, supervisa políticas para agentes de IA y verifica declaraciones de sitemap desde una base de 100 puntos sin dependencias externas.

El motor de análisis evalúa las reglas según la norma RFC 9309 y las pautas operativas de rastreadores globales:

<table>
  <thead>
    <tr>
      <th>Vector de Gobernanza</th><th>Criterio de Auditoría</th><th>Deducción</th><th>Impacto en Rastreo y SEO</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Regla de Disallow Global</strong></td><td>Verifica bloques <code>User-agent: *</code> con <code>Disallow: /</code> sin directivas compensatorias <code>Allow:</code>.</td><td>-50 pts</td><td>Bloqueo crítico que impide la indexación total del portal en todos los buscadores.</td>
    </tr>
    <tr>
      <td><strong>Declaración de Sitemap XML</strong></td><td>Supervisa la existencia de al menos una directiva <code>Sitemap:</code> que apunte a un feed XML válido.</td><td>-20 pts</td><td>Dificulta el rastreo sistemático y retrasa la indexación de páginas recientes.</td>
    </tr>
    <tr>
      <td><strong>Crawl-Delay Desmedido</strong></td><td>Identifica directivas <code>Crawl-delay</code> superiores a 5 segundos aplicadas a todos los agentes.</td><td>-15 pts</td><td>Restricción innecesaria del presupuesto de rastreo en catálogos extensos.</td>
    </tr>
    <tr>
      <td><strong>Gobernanza de Bots de IA</strong></td><td>Supervisa políticas para 12 agentes de IA (GPTBot, ClaudeBot, PerplexityBot, etc.), reportando bloqueos o acceso libre.</td><td>Señal Analítica</td><td>Protege contenidos contra extracción automatizada para entrenamiento de modelos.</td>
    </tr>
    <tr>
      <td><strong>Accesibilidad del Host</strong></td><td>Verifica código de respuesta HTTP 200 y conectividad durante la descarga del archivo.</td><td>Puntuación reseteada a 0</td><td>Servidor inaccesible impidiendo la extracción de las directivas de rastreo.</td>
    </tr>
  </tbody>
</table>

### Escala de Gobernanza y Niveles de Estado

La herramienta determina un índice consolidado de salud para el archivo robots.txt:

* <strong>80 a 100 (COMPLIANT)</strong>: Conformidad plena con RFC 9309; sitemaps declarados, ausencia de bloqueos globales y directivas ordenadas.
* <strong>50 a 79 (WARNING)</strong>: Directivas operativas con puntos de mejora como ausencia de sitemap o retardos elevados.
* <strong>0 a 49 (CRITICAL)</strong>: Bloqueo total de motores de búsqueda, inaccesibilidad del archivo o reglas desastrosas.

***

## Instalación y Ejecución

Construido íntegramente con la librería estándar de Python 3.8+ sin dependencias externas.

```bash
git clone https://github.com/TAVARDT-Mexico/robots-txt-validator-mx.git
cd robots-txt-validator-mx
```

### Ejecución Estándar CLI

```bash
python robots_validator.py https://ejemplo.mx
```

### Salida Estructurada para Pipelines en JSON

```bash
python robots_validator.py https://ejemplo.mx -j
```

***

## Ciberseguridad y Gobernanza Web en México

El control riguroso de directivas robots.txt apoya las buenas prácticas de ciberseguridad y gobernanza digital en México. Definir reglas claras protege paneles administrativos contra rastreos indebidos mientras asegura la presencia orgánica institucional.

Se aconseja integrar la comprobación automatizada de robots.txt en los despliegues continuos para prevenir desindexaciones no deseadas.

***

## Preguntas Frecuentes Técnicas

### ¿Cómo detecta el validador bloqueos globales de indexación?

El analizador procesa los bloques con <code>User-agent: *</code>. Si detecta la regla <code>Disallow: /</code> sin directivas complementarias <code>Allow:</code>, el sistema resta 50 puntos y genera un aviso crítico de bloqueo.

### ¿Por qué se penaliza omitir la directiva Sitemap en robots.txt?

Declarar la ubicación del sitemap XML en robots.txt orienta a los motores de búsqueda hacia las fuentes oficiales de contenido. La omisión de la directiva <code>Sitemap:</code> conlleva una penalización de 20 puntos.

### ¿Qué perjuicio ocasiona un crawl-delay excesivo?

Fijar un <code>Crawl-delay</code> superior a 5 segundos limita drásticamente el presupuesto de rastreo asignado por los buscadores, demorando la indexación de nuevos contenidos. Dicha configuración resta 15 puntos.

### ¿Cuáles rastreadores de inteligencia artificial son auditados?

El sistema monitoriza doce bots de IA destacados: GPTBot, ChatGPT-User, ClaudeBot, Anthropic-AI, PerplexityBot, CCBot, Cohere-AI, Google-Extended, Applebot-Extended, Omgilibot, Diffbot y ByteSpider.

### ¿Qué indican las categorías de puntuación y estado de conformidad?

Notas de 80 a 100 reflejan estado COMPLIANT bajo RFC 9309. Entre 50 y 79 puntos el estado es WARNING por omisiones o retardos, y por debajo de 50 puntos el estado es CRITICAL, indicando bloqueos severos.

***

## Soporte Técnico y Consultoría Especializada

Para soporte prioritario en gobernanza de rastreadores, SEO técnico y ciberseguridad web, contacte a **TAVARDT**.

***

## Enlaces Útiles

* **Portal Corporativo:** https://ag.tavardt.com/mx/
* **Suite de Diagnósticos:** https://tools.tavardt.com/mx/
* **Contacto Técnico:** https://ag.tavardt.com/mx/contacto/

***

### Licencia
Distribuido bajo la Licencia MIT.

***

© 2026 TAVARDT. Todos os direitos reservados.
