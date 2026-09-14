git fetch origin
git checkout origin/main -- \
  sots/app/prog_import_csv_lib.php \
  sots/tools/borrar_prog_fecha.php \
  witlink_rf/tools/borrar_rf_fecha.php

"/c/PHP/php.exe" witlink_rf/tools/borrar_rf_fecha.php 2026-09-14
"/c/PHP/php.exe" sots/tools/borrar_prog_fecha.php 2026-09-14
