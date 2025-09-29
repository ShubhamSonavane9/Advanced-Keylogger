Keylogger Admin Dashboard - Deployment Package
This folder contains a minimal, production-ready subset to deploy the Streamlit dashboard (MongoDB mode).

What's included
app_mongo.py – Main Streamlit app entry for deployment
db_utils.py – Database utilities (reads MONGO_URI/DB_NAME from secrets/env)
utils.py – Non-OS-bound helpers used by the app
requirements.txt – Slim dependencies for Streamlit Cloud
Streamlit Community Cloud Deployment
Push only the contents of this folder to your GitHub repo root, or set the app's main file to deployment_package/app_mongo.py when creating the app in Streamlit Cloud.

In the Streamlit app Settings → Secrets, add:

MONGO_URI = "mongodb+srv://<user>:<pass>@<cluster>/<db>?retryWrites=true&w=majority"
DB_NAME = "keylogger_db"
App settings:
Repository: your GitHub repo
Branch: main
Main file: deployment_package/app_mongo.py (or move files to repo root and use app_mongo.py)
Deploy. On the login page, you should see a success message indicating MongoDB is connected.
Optional: Local Secrets file for quick tests (do not commit)
Create .streamlit/secrets.toml locally with:

MONGO_URI = "mongodb+srv://<user>:<pass>@<cluster>/<db>?retryWrites=true&w=majority"
DB_NAME = "keylogger_db"
Then run streamlit run deployment_package/app_mongo.py.

Local development
pip install -r requirements.txt
set MONGO_URI=...   # on Windows; use export on Linux/macOS
set DB_NAME=keylogger_db
streamlit run app_mongo.py
Notes
Local "files-only" mode relies on a Windows path and is not applicable in Streamlit Cloud; MongoDB mode is recommended for cloud.
Keep credentials only in Streamlit Secrets or environment variables; do not commit them.
