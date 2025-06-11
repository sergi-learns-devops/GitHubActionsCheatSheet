# 🚀 GitHub Actions Cheat Sheet 🎉

🌐 **Disponible en:** [Español](./README.md) | [English](./README.en.md)

Benvingut/da a aquesta guia ràpida i visual sobre GitHub Actions. Aquí hi trobaràs els conceptes clau i exemples pràctics per crear i optimitzar els teus propis workflows. Ideal per tenir sempre a mà i consultar en el teu dia a dia com a desenvolupador/a. 😎

---

## 📁 Estructura bàsica d'un workflow

```yaml
name: CI/CD Pipeline

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout del codi
        uses: actions/checkout@v4
      - name: Salutació inicial
        run: echo "Hola, món!"
```

---

## 🏁 Esdeveniments més comuns

- `push` 🚀: Executa el workflow quan fas push a una branca.
- `pull_request` 🔀: S'activa quan s'obre o s'actualitza un Pull Request.
- `schedule` ⏰: Permet programar tasques automàtiques (cron jobs).
- `workflow_dispatch` 🖱️: Permet llançar el workflow manualment des de la interfície de GitHub.

---

## 🧩 Accions més utilitzades

- `actions/checkout@v4`: Clona el repositori al runner.
- `actions/setup-node@v4`: Configura l'entorn de Node.js.
- `actions/upload-artifact@v4`: Puja artefactes generats durant el workflow.
- `actions/download-artifact@v4`: Descarrega artefactes d'altres jobs.

---

## 🛠️ Variables i secrets

- `${{ github.ref }}`: Referència a la branca o tag que ha disparat el workflow.
- `${{ secrets.EL_MEU_SECRET }}`: Accés segur als secrets definits al repositori.

---

## 🧪 Matrius de jobs

Executa el teu workflow en diferents versions o plataformes de manera paral·lela:

```yaml
strategy:
  matrix:
    node-version: [14, 16, 18]
```

---

## 🔄 Reutilització de workflows

Pots reutilitzar workflows amb `workflow_call` per mantenir la teva configuració DRY:

```yaml
on:
  workflow_call:
    inputs:
      nom:
        required: true
        type: string
```

---

## 📝 Exemple de job amb passos habituals

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Instal·lar dependències
        run: npm install
      - name: Executar tests
        run: npm test
```

---

## 🧙‍♂️ Consells pràctics

- Utilitza `needs:` per definir dependències entre jobs i controlar el flux d'execució.
- Fes servir la condició `if:` per executar passos o jobs només en certes circumstàncies.
- Els artefactes són útils per compartir fitxers entre jobs o etapes.
- Gestiona sempre els teus secrets des de la configuració de GitHub, mai els publiquis al repositori.

---

## 🌟 Bones pràctiques per crear workflows

- **Divideix i venceràs:** Separa els workflows per propòsit (deploy, test, lint, etc.) per facilitar-ne el manteniment.
- **Posa noms descriptius als jobs i passos:** Ajuda a entendre ràpidament què fa cada part del workflow.
- **Reutilitza codi:** Fes servir accions i workflows reutilitzables per evitar duplicats.
- **Mantén els workflows actualitzats:** Revisa periòdicament les versions de les accions que utilitzes.
- **Aprofita les matrius:** Utilitza-les per provar el teu codi en diferents entorns o versions de dependències.
- **Documenta els workflows:** Afegeix comentaris útils per a altres desenvolupadors/es (o per a tu en el futur!).

---

## 🔒 Bones pràctiques de seguretat a GitHub Actions

- **Fes servir només accions de fonts fiables:** Prefereix accions oficials o revisa el codi d'accions de tercers abans d'utilitzar-les.
- **Fixa versions específiques:** Utilitza tags de versió (`@v4.0.0`) en comptes de `@master` o `@main` per evitar canvis inesperats.
- **Minimitza els permisos:** Configura els permisos del workflow i dels tokens (`GITHUB_TOKEN`) al mínim necessari.
- **No exposis secrets:** No utilitzis mai `echo` per mostrar secrets o variables sensibles als logs.
- **Revisa els artefactes:** No descarreguis ni executis artefactes de fonts no fiables.
- **Desactiva workflows innecessaris:** Si un workflow ja no s'utilitza, elimina'l o desactiva'l.

---

## 📚 Enllaços útils i documentació oficial

- [Documentació oficial de GitHub Actions](https://docs.github.com/ca/actions)
- [Guia d'inici ràpid de GitHub Actions](https://docs.github.com/ca/actions/quickstart)
- [Marketplace de GitHub Actions](https://github.com/marketplace?type=actions)
- [Expressions i sintaxi als workflows](https://docs.github.com/ca/actions/learn-github-actions/expressions)
- [Seguretat a GitHub Actions](https://docs.github.com/ca/actions/security-guides/security-hardening-for-github-actions)

---

Aquesta Cheat Sheet està pensada per ser una referència ràpida. Si necessites aprofundir, consulta els enllaços anteriors per obtenir tota la informació oficial i actualitzada sobre GitHub Actions. 