cd /c/inetpub/wwwroot
git fetch origin
git checkout origin/main -- \
  sots/partials/calidad_rf_view.php \
  sots/partials/calidad_rf_script.php \
  sots/api_calidad_rf.php \
  sots/assets/calidad.css \
  witlink_rf/src/rf/GeminiAnalyzer.php
