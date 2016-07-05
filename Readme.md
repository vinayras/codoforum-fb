
## Codoforums Facebook Registration Problem fix

## Installation
Replace your local version of facebook.php in the folder: sys/Ext/hybridauth/Hybrid/Providers 

## What is does?
Existing code was replaced with following code at line 50 - 61. 

```php
		if ($this->token("access_token") || isset($_REQUEST["code"])) {
			if($this->token("access_token")) {
				$this->api->setAccessToken($this->token("access_token"));
			} else if(
				isset($_REQUEST["code"]) &&
				$access_token_from_code = $this->api->getAccessTokenFromCode($_REQUEST["code"], "https://www.indcareer.com/forum/uni_login/authorize?hauth.done=Facebook")
			) {
				$this->api->setAccessToken($access_token_from_code);
			}

			$this->api->setExtendedAccessToken();
			$access_token = $this->api->getAccessToken();

			if ($access_token) {
				$this->token("access_token", $access_token);
				$this->api->setAccessToken($access_token);
			}

			$this->api->setAccessToken($this->token("access_token"));
		}
```

With this change, the Facebook registration and login is working fine for me. You can check at our live forum at https://www.indcareer.com/forum/

## What is CodoForum? 
For more details about CodoForums, please visit http://codoforum.com/


