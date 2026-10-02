php -r 'require "sots/app/config/database.php"; $st=$pdo->prepare("SELECT sot, fecha, departamento, cliente, estado_contrata FROM sots WHERE tipo_trabajo=? ORDER BY fecha"); $st->execute(["CLARO EMPRESAS HFC - SERVICIOS MENORES"]); $n=0; foreach($st as $r){ $n++; echo $r["sot"]."\t".$r["fecha"]."\t".$r["departamento"]."\t".$r["cliente"]."\t".$r["estado_contrata"]."\n"; } echo "TOTAL=$n\n";'

