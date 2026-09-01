cd /c/inetpub/wwwroot/witlink_rf
test -f .env || cp .env.example .env
php -r '
$path = getcwd() . DIRECTORY_SEPARATOR . ".env";
$text = is_file($path) ? file_get_contents($path) : "";
if ($text !== "" && substr($text, -1) !== "\n") $text .= "\n";
$keys = [
  "KIMI_API_KEY" => "sk-F1CpmjhIYb1nosN9u9fGPzeGViqHztCxN1JblOvvFsGmHcVB",
  "KIMI_MODEL" => "kimi-k3",
  "KIMI_API_BASE" => "https://api.moonshot.ai/v1",
  "XAI_API_KEY" => "xai-EeFEIuUQVGrlMJCOCPg889lPeynA42JBJdh4ws0Cl4SVMcYyUOe6K4vDINg9Lc78upynSHL341dKmqrP",
  "XAI_MODEL" => "grok-4.6",
  "XAI_API_BASE" => "https://api.x.ai/v1",
];
foreach ($keys as $k => $v) {
  $line = $k . "=" . $v;
  if (preg_match("/^" . preg_quote($k, "/") . "\s*=/m", $text)) {
    $text = preg_replace("/^" . preg_quote($k, "/") . "\s*=.*$/m", $line, $text, 1);
  } else {
    $text .= $line . "\n";
  }
}
file_put_contents($path, $text);
echo "Kimi y Grok listos en .env\n";
'
