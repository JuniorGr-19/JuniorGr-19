cd /c/inetpub/wwwroot
git fetch origin
git checkout origin/main -- \
  sots/app/prog_csv_bot_lib.php \
  sots/api_prog_importar_csv_bot.php \
  sots/api_prog_bot_tick.php \
  sots/programacion.php
