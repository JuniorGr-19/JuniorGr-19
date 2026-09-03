cd /c/inetpub/wwwroot
git fetch origin main
git checkout origin/main -- \
  witlink_app/rf_validar.php \
  witlink_app/index.php \
  witlink_app/login.php \
  witlink_app/app/auth.php \
  witlink_app/app/layout_shell.php \
  witlink_app/app/rf_bridge.php \
  witlink_app/api/rf_analizar.php \
  witlink_app/api/rf_buscar.php \
  witlink_app/api/rf_foto.php \
  witlink_app/api/rf_tecnicos.php \
  witlink_app/api/rf_traer_fotos.php \
  witlink_app/assets/js/rf-validar.js \
  witlink_app/assets/css/app.css
