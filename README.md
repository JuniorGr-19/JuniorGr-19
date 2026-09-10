cd /c/inetpub/wwwroot
git fetch origin
git checkout origin/main -- \
  witlink_rf/src/rf/GeminiAnalyzer.php \
  witlink_rf/config/database.php \
  witlink_rf/src/rf/SyncService.php \
  sots/app/calidad_rf.php \
  sots/api_calidad_rf.php \
  sots/calidad.php \
  sots/partials/calidad_rf_data.php \
  sots/partials/calidad_rf_view.php \
  sots/partials/calidad_rf_script.php \
  sots/assets/calidad.css
