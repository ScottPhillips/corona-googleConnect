Google Connect
============

Google Connect is a simple module for connecting with google APIs via OAUTH2

Configuration
-------------------------

Change options.client_id and options.client_secret to reflect your app


Basic Usage
-------------------------

##### Require The Code
```lua
local gConnect = require("googleConnect")
```
##### Call "connect" passing a callback as a parameter. 
##### If the user never used the app, it will open a WebPopUp so the user can authorize the app. The module will save the user refresh token and try to use it on all subsequent usages without presenting a webPopUp again.
```lua
gConnect.connect(callback)
```

##### On your callback function (or anytime after the callback was called, you can call google APIs using google.api(URL, METHOD, CALLBACK), for example:
```lua
google.api("https://www.googleapis.com/oauth2/v1/userinfo", "GET", function(event)
	print(event.response)
end)
```

##### The complete example would be:
```lua
local gConnect = require("googleconnect")
function connectCallback(event)
	if(not event.isError) then
		gConnect.api("https://www.googleapis.com/oauth2/v1/userinfo", "GET", function(event)
			print(event.response)
		end)
	end
end
gConnect.connect(connectCallback)
```
