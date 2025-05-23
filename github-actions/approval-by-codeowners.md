# Approval nur durch festgelegte CODEOWNER (in .github/CODEOWNERS)

## Situation 

  * Nur bestimmte Personen sollen als Approval zählen
  * Achtung: Approven können alle, die mindestens Leserechte für das Repo haben, sie zählen dann aber nicht mit

## 3 Bausteine 

  1. Team in der Organisation anlegen mit den gewünschten Benutzer: z.B. team_reviewer
  2. 2 Haken bei branch-protection - rule setzen

![image](https://github.com/user-attachments/assets/6568f169-d2b0-44ba-8acb-33e16bb78727)

  3. Dann müssen im Repo unter .git/CODEOWNERS diese noch eingetragen werden

```
# Datei: .github/CODEOWNERS

# Alle Dateien im Projekt sollen von einem Team geprüft werden
* @gitmeisterei/team-reviewer
```

