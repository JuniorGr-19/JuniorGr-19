cd /c/inetpub/wwwroot
git fetch origin
git checkout origin/main -- \
  witlink_rf/api/rf_fetch_cola.php \
  witlink_app/app/rf_bridge.php \
  witlink_app/assets/js/rf-validar.js \
  sots/api_calidad_rf.php
