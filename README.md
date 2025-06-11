# 🚀 GitHub Actions Cheat Sheet 🎉

🌐 **Disponible en:** [English](./README.en.md) | [Català](./README.ca.md)

Bienvenido a esta guía rápida y visual sobre GitHub Actions. Aquí encontrarás los conceptos clave y ejemplos prácticos para crear y optimizar tus propios workflows. Ideal para tener siempre a mano y consultar en tu día a día como desarrollador. 😎

---

## 📁 Estructura básica de un workflow

```yaml
name: CI/CD Pipeline

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout del código
        uses: actions/checkout@v4
      - name: Saludo inicial
        run: echo "¡Hola, mundo!"
```

---

## 🏁 Eventos más comunes

- `push` 🚀: Ejecuta el workflow al hacer push a una rama.
- `pull_request` 🔀: Se activa cuando se abre o actualiza un Pull Request.
- `schedule` ⏰: Permite programar tareas automáticas (cron jobs).
- `workflow_dispatch` 🖱️: Permite lanzar el workflow manualmente desde la interfaz de GitHub.

---

## 🧩 Acciones más utilizadas

- `actions/checkout@v4`: Clona el repositorio en el runner.
- `actions/setup-node@v4`: Configura el entorno de Node.js.
- `actions/upload-artifact@v4`: Sube artefactos generados durante el workflow.
- `actions/download-artifact@v4`: Descarga artefactos de otros jobs.

---

## 🛠️ Variables y secretos

- `${{ github.ref }}`: Referencia a la rama o tag que disparó el workflow.
- `${{ secrets.MI_SECRETO }}`: Acceso seguro a secretos definidos en el repositorio.

---

## 🧪 Matrices de jobs

Ejecuta tu workflow en diferentes versiones o plataformas de forma paralela:

```yaml
strategy:
  matrix:
    node-version: [14, 16, 18]
```

---

## 🔄 Reutilización de workflows

Puedes reutilizar workflows con `workflow_call` para mantener tu configuración DRY:

```yaml
on:
  workflow_call:
    inputs:
      nombre:
        required: true
        type: string
```

---

## 📝 Ejemplo de job con pasos habituales

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Instalar dependencias
        run: npm install
      - name: Ejecutar tests
        run: npm test
```

---

## 🧙‍♂️ Consejos prácticos

- Utiliza `needs:` para definir dependencias entre jobs y controlar el flujo de ejecución.
- Usa la condición `if:` para ejecutar pasos o jobs solo bajo ciertas circunstancias.
- Los artefactos son útiles para compartir archivos entre jobs o etapas.
- Gestiona tus secretos siempre desde la configuración de GitHub, nunca los subas al repositorio.

---

## 🌟 Buenas prácticas para crear workflows

- **Divide y vencerás:** Separa los workflows por propósito (deploy, test, lint, etc.) para facilitar el mantenimiento.
- **Nombra tus jobs y pasos de forma descriptiva:** Ayuda a entender rápidamente qué hace cada parte del workflow.
- **Reutiliza código:** Usa acciones y workflows reutilizables para evitar duplicidad.
- **Mantén tus workflows actualizados:** Revisa periódicamente las versiones de las acciones que utilizas.
- **Aprovecha las matrices:** Úsalas para probar tu código en diferentes entornos o versiones de dependencias.
- **Documenta tus workflows:** Añade comentarios útiles para otros desarrolladores (¡o para ti en el futuro!).

---

## 🔒 Buenas prácticas de seguridad en GitHub Actions

- **Usa solo acciones de fuentes confiables:** Prefiere acciones oficiales o revisa el código de acciones de terceros antes de usarlas.
- **Fija versiones específicas:** Utiliza tags de versión (`@v4.0.0`) en vez de `@master` o `@main` para evitar cambios inesperados.
- **Minimiza los permisos:** Configura los permisos del workflow y de los tokens (`GITHUB_TOKEN`) al mínimo necesario.
- **No expongas secretos:** Nunca uses `echo` para mostrar secretos o variables sensibles en los logs.
- **Revisa los artefactos:** No descargues ni ejecutes artefactos de fuentes no confiables.
- **Deshabilita workflows innecesarios:** Si un workflow ya no se usa, elimínalo o desactívalo.

---

## 📚 Enlaces útiles y documentación oficial

- [Documentación oficial de GitHub Actions](https://docs.github.com/en/actions)
- [Guía de introducción a GitHub Actions](https://docs.github.com/en/actions/quickstart)
- [Marketplace de GitHub Actions](https://github.com/marketplace?type=actions)
- [Expresiones y sintaxis en workflows](https://docs.github.com/en/actions/learn-github-actions/expressions)
- [Seguridad en GitHub Actions](https://docs.github.com/en/actions/security-guides/security-hardening-for-github-actions)

---

Esta Cheat Sheet está pensada para ser una referencia rápida. Si necesitas profundizar, consulta los enlaces anteriores para obtener toda la información oficial y actualizada sobre GitHub Actions. 