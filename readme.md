# LB 324

Laufende Applikation: https://tagebbbuch-wigetpascal-hsdvf3d3exdxajhj.austriaeast-01.azurewebsites.net

## Aufgabe 2
Erklären Sie hier, wie man `pre-commit` installiert.

Die Konfiguration liegt in `.pre-commit-config.yaml`. Sie enthält zwei Automatisierungen:

- **bei jedem `git commit`**: `black` formatiert den geänderten Python-Code automatisch.
- **bei jedem `git push`**: `pytest` führt alle Tests aus. Schlägt ein Test fehl, wird der Push abgebrochen.

Einmalig nach dem Klonen des Repos (PowerShell, im Projektordner):

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
pip install pre-commit
pre-commit install
```

`pre-commit install` installiert dank `default_install_hook_types` in der Konfiguration sowohl den `pre-commit`- als auch den `pre-push`-Hook. Gleichwertig und ausdrücklich:

```powershell
pre-commit install --hook-type pre-commit --hook-type pre-push
```

Danach laufen die Hooks automatisch bei `git commit` bzw. `git push`. Hat `black` beim Commit eine Datei umformatiert, bricht der Commit ab; die Änderungen mit `git add` erneut hinzufügen und den Commit wiederholen.

Manuell ausführen (z. B. zum Prüfen):

```powershell
pre-commit run --all-files                        # Formatierung über alle Dateien
pre-commit run --hook-stage pre-push --all-files  # Tests wie beim Push
```

Wichtig: Die virtuelle Umgebung muss aktiviert sein, wenn man committet bzw. pusht, weil der Test-Hook `python -m pytest` aus der aktiven Umgebung aufruft.

## Aufgabe 4
Erklären Sie hier, wie Sie das Passwort aus Ihrer lokalen `.env` auf Azure übertragen.

Die `.env` ist in `.gitignore` eingetragen und gelangt nie ins Repository. Auf Azure wird das Passwort stattdessen als Umgebungsvariable hinterlegt, die `os.getenv("PASSWORD")` in `app.py` ausliest:

1. Im [Azure-Portal](https://portal.azure.com) die Web-App öffnen.
2. Links unter **Settings** → **Environment variables** → Reiter **App settings** → **+ Add**.
3. **Name:** `PASSWORD`, **Value:** das Passwort (auf Azure = GitHub-Benutzername `Spascalee`), ohne Anführungszeichen.
4. **Apply** und anschliessend **Apply** / **Confirm** bestätigen. Die App startet dabei neu.

Ausserdem ist unter **Settings** → **Configuration** → **General settings** als **Startup Command** eingetragen:

```
gunicorn --bind=0.0.0.0 --timeout 600 app:app
```

Die automatische Auslieferung erfolgt über den vom Azure Deployment Center erzeugten Workflow in `.github/workflows/`, der bei jedem Push bzw. Merge auf `main` ausgelöst wird.
