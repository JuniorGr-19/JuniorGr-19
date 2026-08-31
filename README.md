<?php
require_once 'C:/inetpub/wwwroot/witlink_rf/config/bootstrap.php';
$db = rf_db();
foreach (array('rf_fotos','rf_validacion_auto','rf_validacion_tecnico','rf_analisis_gemini','rf_analisis_modelo','rf_sot_intentos','rf_sync_runs','rf_sot') as $t) {
  try { $db->exec('DELETE FROM '.$t); } catch (Exception $e) {}
}
echo "OK rf_sot=".$db->query('SELECT COUNT(*) FROM rf_sot')->fetchColumn()." rf_fotos=".$db->query('SELECT COUNT(*) FROM rf_fotos')->fetchColumn()."\n";

notepad witlink_rf/tools/limpiar_rf_prueba.php

rm -rf witlink_rf/storage/descargas_toa/* witlink_rf/storage/fotos/*
