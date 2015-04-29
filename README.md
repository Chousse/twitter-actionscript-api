#Twitter API library for Flex/AIR/ActionScript 3.0

(Updated for Twitter API 1.1)

ActionScript 3.0 library for [Twitter](http://twitter.com/) [API](http://apiwiki.twitter.com/). For use in Adobe Flash, Adobe Flex, Adobe AIR.

oAuth connector is implemented using [ActionScript 3.0 library for oAuth](http://code.google.com/p/oauth-as3/).

Example of using:

	var twitterApi:TwitterAPI = new TwitterAPI();
	twitterApi.connection.setAccessToken(key, secret);
	
	var op:TwitterOperation = new VerifyCredentials();
	var handler:Function = function (event:TwitterEvent):void
	{
		op.removeEventListener(TwitterEvent.COMPLETE, handler);
		if (event.success)
		{
			trace("Credentials verified. User is: " + TwitterUser(event.data).screenName);
		}
		else
		{
			trace("Verification error. Twitter error message: " + event.data);
		}
	};
	op.addEventListener(TwitterEvent.COMPLETE, handler);
	twitterApi.post(op, TwitterAPI.POST_TYPE_ASYNC_STATIC, TwitterAPI.PRIORITY_HIGHEST);
