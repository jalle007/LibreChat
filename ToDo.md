## Project
LibreChat fork
[LibreChat](https://github.com/danny-avila/LibreChat)

## Dev Environment
Windows pc with docker installed
Developer preffer to run LibreChat inside container, so he doesnt have to install  LibreChat depedencies in windows pc
## Task
Add new  translation for bosnian language and deploy the app

## Word done
* Enable admin access
  1. Sign up the first user in LibreChat.
  2. Confirm in the database (MongoDB, users collection) that the user has the `role: admin`.
  3. Log in as this user; admin menus should be enabled automatically for admin users.
  4. If admin menus are not visible, check the frontend for role-based menu rendering or clear browser cache.
* Find a way on how to add new LibreChat UI language translation. We will use English language file to create Bosnian.
  1. Go to `client/public/locales/en/translation.json` (or similar path for English).
  2. Copy the entire file and create a new folder: `client/public/locales/bs/`.
  3. Paste the copied file as `translation.json` in the new folder.
  4. Translate all values in the JSON file from English to Bosnian.
  5. Add `bs` to the list of supported languages in the LibreChat UI language selector (if needed).
  6. Restart the frontend if required.

## Run
we build the app with:  docker compose build --no-cache
then run it with :            docker compose up
http://localhost:3080/

## Result
Bosnian language WAS  added to the menu.
When selected ,  UI language is translated to ENGLISH instead of bosnian (bs)

## LOGS
No errors reported in browser console OR shell

## RELATED CODE
client\src\components\Nav\SettingsTabs\General\General.tsx
client\src\locales\i18n.ts
client\src\locales\bs\translation.json


docker compose exec api sh
chmod -R 777 /app/api/logs
exit


### INSTRUCT

## 🔄 Rebuilding Process for Code Changes

### For Local Development Changes:

```bash
# 1. Make your changes to the code
# Edit files like: client/src/locales/bs/translation.json

# 2. Rebuild only the API container (faster)
docker compose build api

# 3. Restart containers with new build
docker compose down
docker compose up -d

# 4. Check logs to ensure everything works
docker compose logs api
```

### Quick vs Full Rebuild:
- **Quick rebuild**: `docker compose build api` (only rebuilds changed parts)
- **Full clean rebuild**: `docker compose build --no-cache api` (rebuilds everything, slower but safer)

---

## 🚀 Deploying to Server

### Option 1: Direct Docker Deployment
```bash
# On your server:
git clone your-fork-repo
cd LibreChat
cp .env.example .env
# Edit .env with production values

# Create production docker-compose.override.yml
# (similar to yours but without dev settings)

docker compose build --no-cache
docker compose up -d
```

### Option 2: Using Docker Registry (Recommended)
```bash
# 1. Build and tag your image locally
docker build -t your-registry/librechat:latest .

# 2. Push to registry (Docker Hub, AWS ECR, etc.)
docker push your-registry/librechat:latest

# 3. On server, pull and run
docker pull your-registry/librechat:latest
docker compose up -d
```

### Option 3: CI/CD Pipeline
Set up GitHub Actions to automatically build and deploy when you push changes.

---

## ⚡ Development Workflow Summary:

1. **Make changes** → Edit translation files
2. **Test locally** → `docker compose build api && docker compose up -d`
3. **Commit & push** → `git add . && git commit -m "Updated translations" && git push`
4. **Deploy** → Pull changes on server and rebuild

The key is that once you have the working Docker setup (which we just established), adding more translations is just editing JSON files and rebuilding!
