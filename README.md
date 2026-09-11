cd /c/inetpub/wwwroot
git fetch origin
git checkout origin/main -- \
  witlink_rf/config/database.php \
  witlink_rf/src/rf/GeminiAnalyzer.php \
  witlink_rf/src/rf/VisionChecks.php \
  witlink_rf/public/assets/rf.js \
  sots/app/calidad_rf.php
rm -f witlink_rf/storage/.use_sqlite
