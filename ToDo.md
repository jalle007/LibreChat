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
