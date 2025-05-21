# Git-Server auf Synology einrichten 


 * Um auf einem **Synology NAS** einen Git-Server einzurichten, kannst du dies entweder über den **Paketmanager** mit vorhandenen Tools oder manuell über SSH und `git init --bare` tun. Hier ist eine **Schritt-für-Schritt-Anleitung** für beide Methoden:

---

## 🔧 **Variante 1: Mit dem Paket "Git Server" (einfachste Methode)**

### Voraussetzungen:

* DSM (DiskStation Manager) installiert
* Administratorrechte
* SSH-Zugriff (optional für erweiterte Nutzung)

### Schritte:

1. **Git Server installieren**

   * Öffne das **Paket-Zentrum** auf deinem Synology NAS.
   * Suche nach **„Git Server“** (von Synology).
   * Klicke auf **Installieren**.

2. **Benutzerrechte für Git einrichten**

   * Gehe zu **Systemsteuerung > Benutzer > Benutzer bearbeiten**.
   * Aktiviere bei gewünschten Benutzern unter dem Tab **Anwendungen** die **Git Server**-Berechtigung.
   * (Optional: SSH-Zugriff erlauben unter „Terminal & SNMP“)

3. **SSH aktivieren (für Push-Zugriff nötig)**

   * Öffne **Systemsteuerung > Terminal & SNMP**.
   * Aktiviere **SSH-Dienst aktivieren**.

4. **Repository erstellen**

   * Verbinde dich per SSH mit dem NAS:

     ```bash
     ssh benutzername@dein-nas-ip
     ```
   * Erstelle ein „bare“-Repository:

     ```bash
     mkdir -p /volume1/git/projektname.git
     cd /volume1/git/projektname.git
     git init --bare
     ```

5. **Repository vom Client klonen**

   ```bash
   git clone ssh://benutzername@dein-nas-ip/volume1/git/projektname.git
   ```

---

## 🧰 **Variante 2: Docker-GitLab oder Gitea (wenn du Web-GUI willst)**

### Gitea:

1. **Docker installieren** (falls noch nicht geschehen)
2. **Gitea-Container starten** (einfach via Container Manager oder mit Docker Compose)
3. Zugriff per Web-GUI: Benutzer, Repos, Berechtigungen etc.

> Vorteil: Admin-Weboberfläche, einfache Verwaltung von Repos, Benutzerkonten, Pull Requests usw.

---

## 🔐 Tipps zu Sicherheit

* Nutze SSH-Schlüssel statt Passwortauthentifizierung.
* Konfiguriere Firewall/Portweiterleitungen sicher.
* Ggf. VPN-Verbindung nutzen, um das NAS nicht direkt im Internet zugänglich zu machen.

---

Möchtest du lieber eine Weboberfläche wie GitLab oder Gitea auf deinem NAS einrichten? Dann kann ich dir ein passendes Setup dafür schreiben.
