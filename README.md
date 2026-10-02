cat > liq_oct_tmp.php << 'EOF'
<?php
require "sots/app/config/database.php";
$sql = "SELECT COUNT(*) FROM sots_liquidacion_sots ls JOIN sots_liquidaciones l ON l.id = ls.liquidacion_id WHERE l.anio = 2026 AND l.mes = 10 AND (TRIM(IFNULL(ls.estado_final,'')) = 'LIQUIDADO' OR TRIM(IFNULL(ls.estado_pago,'')) = 'LIQUIDADO')";
$antes = (int) $pdo->query($sql)->fetchColumn();
echo "ANTES=$antes\n";
$n = $pdo->exec("UPDATE sots_liquidacion_sots ls JOIN sots_liquidaciones l ON l.id = ls.liquidacion_id SET ls.estado_final = IF(TRIM(IFNULL(ls.estado_final,'')) = 'LIQUIDADO', NULL, ls.estado_final), ls.estado_pago = IF(TRIM(IFNULL(ls.estado_pago,'')) = 'LIQUIDADO', NULL, ls.estado_pago) WHERE l.anio = 2026 AND l.mes = 10 AND (TRIM(IFNULL(ls.estado_final,'')) = 'LIQUIDADO' OR TRIM(IFNULL(ls.estado_pago,'')) = 'LIQUIDADO')");
echo "ACTUALIZADAS=$n\n";
$despues = (int) $pdo->query($sql)->fetchColumn();
echo "QUEDAN=$despues\n";
EOF
php liq_oct_tmp.php
rm -f liq_oct_tmp.php
