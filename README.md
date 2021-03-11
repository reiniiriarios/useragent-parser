# useragent-parser
User agent parser that returns vaguely useful browser and OS information. Rather than aim for comprehensiveness, this aims only to return broad information on the most common devices, browsers, hardware, etc.

Most useful when utilizing `get_icon($type)` or `get_all_icons()`.

## Usage

### Configuring

Set `$ua->assets_uri` to path to icon pngs. (Default: `/assets/ua/`)

### Result Types

* Operating System `os`
  * e.g. Windows, macOS
* Browser `browser`
  * e.g. Firefox, Safari, Firefox iOS
* Hardware `hardware`
  * e.g. Nintendo Switch, Apple iPad
* Miscellaneous `misc`
  * e.g. Slack, WhatsApp, Gmail, cURL, Python-urllib
* Bot `bot`
  * e.g. Googlebot, BingBot, Baidu Spider

### Result Data

* Name
* Icon
* Version
* Brand (hardware only)
* Model (hardware only)
* Mobile (boolean, can be inaccurate)

```php
$user_agent      = new \reiniiriarios\Useragent\Parser($user_agent_string);
$user_agent_info = $user_agent->parse();
$user_agent_os   = $user_agent->parse('os');
$browser_icon    = $user_agent->get_icon('browser');
/*
$user_agent_info = [
	'os' => [
		'name'    => 'Windows',
		'icon'    => 'win10',
		'version' => '10'
	],
	'browser' => [
		'name'    => 'Firefox',
		'icon'    => 'firefox',
		'version' => '86.0'
	],
	'hardware' => false,
	'misc' => false,
	'bot' => false
];
$user_agent_os = [
	'name'    => 'Windows',
	'icon'    => 'win10',
	'version' => '10'
];
$browser_icon = '<img class="ua" src="/assets/ua/firefox.png" alt="Firefox 86.0" data-toggle="tooltip" data-placement="left" title="Firefox 86.0" />';
*/
```

