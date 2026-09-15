cd /c/inetpub/wwwroot
git fetch origin
git checkout origin/main -- \
  sots/programacion.php \
  sots/app/prog_bolsa_lib.php \
  sots/api_prog_bolsa_upload.php \
  sots/api_prog_bolsa_grupos.php \
  sots/partials/prog_bolsa_modal.php \
  sots/assets/prog_bolsa.js \
  sots/uploads/bolsa/.gitkeep \
  sots/uploads/bolsa/.htaccess \
  sots/uploads/bolsa/web.config
mkdir -p sots/uploads/bolsa
git status --short
