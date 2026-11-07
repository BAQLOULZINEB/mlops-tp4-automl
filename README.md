# TP04 - AutoML (FLAML)

Fiche explicative : `EXPLICATION_TP4.html` | Rapport : `rapport_tp4.md`

```powershell
.venv\Scripts\Activate.ps1
python donnees.py
# terminal 1
mlflow server --host 127.0.0.1 --port 5000 --backend-store-uri sqlite:///mlflow.db --default-artifact-root ./mlartifacts
# terminal 2
python src/references.py
python src/automl.py 60
python src/rendement.py
python src/inspecter.py reports/flaml_60s.log
python src/fuite.py
```
