## Les 0.1

### Vraag & Antwoord
Straks laat je Claude Code op jouw computer committen en pushen. Met wiens credentials gebeurt dat, en wie is verantwoordelijk voor wat er in die commit staat?

Claude werkt onder mijn eigen credentials (zie `gh auth status`).
Claude doet wijzigingen en commits, maar evaluatie en een uiteindelijke merge blijf ik zelf verantwoordelijk.

### Behandeld
Controle benodigde tools:   `git --version`, `gh --version`, etc.

### Terugblik

1. **Waarom zijn API-aanroepen van een agent auditeerbaar?**
   Elke aanroep gaat met een token (PAT, GitHub App-token of GITHUB_TOKEN) dat bij een identiteit hoort. GitHub legt zelf vast wie wat deed: commit-auteur, PR-maker, actor van een workflow run, auditlog. GitHub is het *system of record*; chatgeschiedenis of agentgeheugen is dat niet.

2. **Waar hoort een API-key?**
   In GitHub: Settings → Secrets van de repo (of een environment). Lokaal: in een omgevingsvariabele of de login van de tool. Nooit in een bestand dat gecommit kan worden (code, config, instructiebestanden).

3. **Assistent versus agent**
   Een assistent is reactief en geeft de besturing terug aan de gebruiker. Een agent houdt een doel vast over meerdere stappen, kiest zelf tussenstappen, gebruikt tools, maakt blijvende artefacten (branch, commits, PR) en werkt in de lus plan → act → evaluate.
