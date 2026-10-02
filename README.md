cat > liq_oct_tmp.php << 'EOF'
<?php
require "sots/app/config/database.php";
try {
    $ids = $pdo->query("SELECT ls.id FROM sots_liquidacion_sots ls JOIN sots_liquidaciones l ON l.id = ls.liquidacion_id WHERE l.anio = 2026 AND l.mes = 10 AND (TRIM(IFNULL(ls.estado_final,'')) = 'LIQUIDADO' OR TRIM(IFNULL(ls.estado_pago,'')) = 'LIQUIDADO')")->fetchAll(PDO::FETCH_COLUMN);
    echo "ANTES=" . count($ids) . "\n";
    $n = 0;
    if ($ids) {
        $ph = implode(',', array_fill(0, count($ids), '?'));
        $st = $pdo->prepare("UPDATE sots_liquidacion_sots SET estado_final = IF(TRIM(IFNULL(estado_final,'')) = 'LIQUIDADO', NULL, estado_final), estado_pago = IF(TRIM(IFNULL(estado_pago,'')) = 'LIQUIDADO', NULL, estado_pago) WHERE id IN ($ph)");
        $st->execute(array_map('intval', $ids));
        $n = $st->rowCount();
    }
    echo "ACTUALIZADAS=$n\n";
    $despues = (int) $pdo->query("SELECT COUNT(*) FROM sots_liquidacion_sots ls JOIN sots_liquidaciones l ON l.id = ls.liquidacion_id WHERE l.anio = 2026 AND l.mes = 10 AND (TRIM(IFNULL(ls.estado_final,'')) = 'LIQUIDADO' OR TRIM(IFNULL(ls.estado_pago,'')) = 'LIQUIDADO')")->fetchColumn();
    echo "QUEDAN=$despues\n";
} catch (Throwable $e) {
    echo "ERROR=" . $e->getMessage() . "\n";
}
EOF
php liq_oct_tmp.php
rm -f liq_oct_tmp.php
