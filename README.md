cmd //c "icacls C:\inetpub\wwwroot\witlink_rf\storage /grant IIS_IUSRS:(OI)(CI)M /T"

mkdir -p /c/inetpub/wwwroot/witlink_rf/storage/descargas_toa /c/inetpub/wwwroot/witlink_rf/storage/fotos

notepad witlink_rf/api/rf_diag.php

<?php
header('Content-Type: application/json; charset=utf-8');
$root = 'C:/inetpub/wwwroot/witlink_rf';
require_once $root . '/config/bootstrap.php';
$dir = $root . '/storage/descargas_toa';
if (!is_dir($dir)) mkdir($dir, 0775, true);
$probe = $dir . '/_probe.txt';
$w = file_put_contents($probe, 'ok') !== false;
if ($w) unlink($probe);
$db = rf_db();
echo json_encode(array(
  'file_uploads' => (bool) ini_get('file_uploads'),
  'upload_max' => ini_get('upload_max_filesize'),
  'post_max' => ini_get('post_max_size'),
  'pdo_mysql' => in_array('mysql', PDO::getAvailableDrivers(), true),
  'storage_ok' => $w,
  'driver' => $db->getAttribute(PDO::ATTR_DRIVER_NAME),
  'rf_sot' => (int) $db->query('SELECT COUNT(*) FROM rf_sot')->fetchColumn(),
  'rf_fotos' => (int) $db->query('SELECT COUNT(*) FROM rf_fotos')->fetchColumn()
), JSON_PRETTY_PRINT);
