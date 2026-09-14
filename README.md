cd /c/inetpub/wwwroot
git fetch origin
git checkout origin/main -- \
  witlink_rf/tools/borrar_rf_fecha.php \
  sots/tools/borrar_prog_fecha.php
php witlink_rf/tools/borrar_rf_fecha.php 2026-09-14
php sots/tools/borrar_prog_fecha.php 2026-09-14
