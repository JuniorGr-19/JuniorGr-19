P=$(grep "\$pass =" /c/inetpub/wwwroot/contratos/app/config/database.php | head -1 | sed "s/.*'\(.*\)'.*/\1/")
"/c/Program Files/MySQL/MySQL Server 8.0/bin/mysql.exe" -u root -p"$P" sistema -N -e "SELECT COUNT(*) FROM contratos_arriendo_arrendador"
