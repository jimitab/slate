---
title: API Reference

language_tabs:
  - PHP
  - Android
  - Objective-C

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>


search: true
---

# Introduction

Welcome to the SocialPilot API!

# Authenticate User

## Register

This api is used for user registration.

### HTTP Request

`POST https://panel.socialpilot.co/mobapi/register`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | Yes | It should be user's email address.
password | Yes | It should be user's password.
mix_id | Yes | Mixpanel's distinct id.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"msg": "You have successfully registered. Please check your email for activation",
	"url": "https://panel.socialpilot.co/companyUser/resend?mail=p1N0zL01961d210ozU81Y21001Gszv41q81Y2zT81w8zO917+",
	"info": {
		"access_token": "Lzv7wxwijMc4T7TIcMDuRb5kEg19bKVbTSckL0KmwKiUZwbXqiBDL1eokbYRoRKXHAmKDiTWzGKqztTV",
		"token_type": "Bearer",
		"expires": 1491299941,
		"expires_in": 5184000
	}
}
```

<aside class="notice">
After successful registration, get all accounts, groups, settings and send device token to server.
</aside>

> Example Error Response:

>Response Code: 200
 
 ```json
 {
	"error": 1,
	"msg": "<div><ul><li>User is already exist with this email address</li></ul></div>"
}
```

## Register with other social media

This api is used for user registration.

### HTTP Request

`POST https://panel.socialpilot.co/mobapi/registerbysm`

<aside class="notice">
As twitter api do not provide email id, send full name compulsory in that case.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | No | Twitter registration do not require email, while linkedin and fb registration requires email.
full_name | No | Full name fetched from third party.
email_verified | No | Static Y or N is passed.
from | Yes | Name of social media you are using.
mix_id | Yes | Mixpanel's distinct id.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"msg": {
		"access_token": "EEOJh0hT8g7hZcJDH2PGOVV44WfJHmnlnJ3QsmqhuJZcnzLrUSTUhUbi4oQUYSYLzmCkQw3mIR0ff60Q",
		"token_type": "Bearer",
		"expires": 1491300443,
		"expires_in": 5184000
	}
}
```

> Example Error Response:

>Response Code: 500
 
 ```json
 {
	"name": "Internal Server Error",
	"message": "There was an error at the server.",
	"code": 0,
	"status": 500
}
```


## Login

This api is used for user login.

### HTTP Request

`POST https://panel.socialpilot.co/mobapi/login`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
username | Yes | It should be user's email address.
password | Yes | It should be user's password.

<aside class="notice">
After successful login, get all accounts, groups, settings and send device token to server.
</aside>

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"msg": {
		"access_token": "x0VtS4B4OcYuwUDAfkEmqMyqQcME3VF4oiYu5qBwzT6jB4a4LDHXMAuMBxpP6XTpps8Pnx5fYTPWsPtM",
		"token_type": "Bearer",
		"expires": 1503049878,
		"expires_in": 5184000
	},
	"master_user": "N",
	"company_id": 12416
}
```

> Example Error Response:

>Response Code: 200
 
 ```json
 {
	"error": 1,
	"msg": "We didn't recognize the email address and/or password. Please try again"
}
```

## Verify Accesstoken

This api is used for verifying user's accesstoken.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/ping`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.

<aside class="notice">
After verifying accesstoken, get all accounts, groups, settings and send device token to server.
</aside>

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"data": {
		"client_id": "eduwk99yb1ou85wq2l533puvhw3q553kjyg38q2j",
		"organization_id": "36803",
		"company_id": "36803",
		"user_id": "36803",
		"is_email_verified": "N",
		"login_as": 0,
		"user_email": "dhruvi@creativeglance.com"
	}
}
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

# Settings

## Get All Settings

This api is used to fetch all settings.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/settings`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.

>Example Success Response:

>Response Code: 200

```json
[{
	"key": "is_active",
	"value": "Y",
	"array_value": []
}, {
	"key": "time_zone",
	"value": "+05:30",
	"array_value": []
}, {
	"key": "time_zone_full",
	"value": "Asia\/Calcutta",
	"array_value": []
}, {
	"key": "membership",
	"value": "10",
	"array_value": []
}, {
	"key": "url_shortner",
	"value": "1",
	"array_value": []
}, {
	"key": "bitly_token",
	"value": "p0kxYlcremGukZqFvnWtFGgbYFE2DLGzszo5a1cLOyumGVWVY1fSTLbSBBVw9Jzr",
	"array_value": []
}, {
	"key": "trial_used",
	"value": "Y",
	"array_value": []
}, {
	"key": "user_type",
	"value": "I",
	"array_value": []
}, {
	"key": "country",
	"value": "INDIA",
	"array_value": []
}, {
	"key": "last_login_country",
	"value": "India",
	"array_value": []
}, {
	"key": "company_id",
	"value": "12416",
	"array_value": []
}, {
	"key": "s_id",
	"value": "0",
	"array_value": []
}, {
	"key": "team_option",
	"value": "",
	"array_value": [{
		"id": "0",
		"name": "My Panel"
	}, {
		"id": "12325",
		"name": "D"
	}, {
		"id": "162",
		"name": "S"
	}, {
		"id": "36803",
		"name": "D"
	}]
}, {
	"key": "login_as",
	"value": "0",
	"array_value": []
}]
```

> Example Error Response:

>Response Code: 401

```json
{
	"error": 1,
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Update Status

This API is used to update status.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/updatestatus`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.

>Example Success Response:

>Response Code: 200

```json
 {
	"error": 0,
	"status": "Paused"
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": 1,
	"msg": "Invalid access token provided. Check your access_token value"
}
```


# Accounts

## Get All Accounts

This api is used for fetching all accounts.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/accounts`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
team_owner_id | Yes | It should be "0" for MyPanel or ownerid of team selected.

>Example Success Response:

>Response Code: 200

```json
[{
	"id": "81087",
	"nickname": "My books",
	"url": "https:\/\/www.facebook.com\/rutulssss\/",
	"access_type": "O",
	"profile_picture": "https:\/\/scontent.xx.fbcdn.net\/v\/t1.0-1\/c15.0.50.50\/p50x50\/399548_10149999285987789_1102888142_n.png?oh=bdf22659929b60d2530a472381162098&oe=590DF16A",
	"status": "Running",
	"account_type": "facebook-official",
	"groups": [],
	"timeslots": [{
		"day": "Sun",
		"slot": [{
			"slot_id": "2616999",
			"timevalue": "10:36 AM"
		}, {
			"slot_id": "2616997",
			"timevalue": "06:28 PM"
		}, {
			"slot_id": "2616998",
			"timevalue": "08:08 PM"
		}]
	}, {
		"day": "Mon",
		"slot": [{
			"slot_id": "2617002",
			"timevalue": "10:36 AM"
		}, {
			"slot_id": "2617000",
			"timevalue": "06:28 PM"
		}, {
			"slot_id": "2617001",
			"timevalue": "08:08 PM"
		}]
	}, {
		"day": "Tue",
		"slot": [{
			"slot_id": "2617005",
			"timevalue": "10:36 AM"
		}, {
			"slot_id": "2617003",
			"timevalue": "06:28 PM"
		}, {
			"slot_id": "2617004",
			"timevalue": "08:08 PM"
		}]
	}, {
		"day": "Wed",
		"slot": [{
			"slot_id": "2617008",
			"timevalue": "10:36 AM"
		}, {
			"slot_id": "2617006",
			"timevalue": "06:28 PM"
		}, {
			"slot_id": "2617007",
			"timevalue": "08:08 PM"
		}]
	}, {
		"day": "Thu",
		"slot": [{
			"slot_id": "2617012",
			"timevalue": "10:36 AM"
		}, {
			"slot_id": "2617009",
			"timevalue": "04:51 PM"
		}, {
			"slot_id": "2617010",
			"timevalue": "06:28 PM"
		}, {
			"slot_id": "2617011",
			"timevalue": "08:08 PM"
		}]
	}, {
		"day": "Fri",
		"slot": [{
			"slot_id": "2617015",
			"timevalue": "10:36 AM"
		}, {
			"slot_id": "2617013",
			"timevalue": "06:28 PM"
		}, {
			"slot_id": "2617014",
			"timevalue": "08:08 PM"
		}]
	}, {
		"day": "Sat",
		"slot": [{
			"slot_id": "2617018",
			"timevalue": "10:36 AM"
		}, {
			"slot_id": "2617016",
			"timevalue": "06:28 PM"
		}, {
			"slot_id": "2617017",
			"timevalue": "08:08 PM"
		}]
	}]
}, {
	"id": "114976",
	"nickname": "SocialPilot.co",
	"url": "https:\/\/www.xing.com\/companies\/socialpilot.co",
	"access_type": "O",
	"profile_picture": "https:\/\/www.xing.com\/img\/custom\/cp\/assets\/logo\/4\/3\/0\/308272\/image_192px\/logo_230.jpg",
	"status": "Running",
	"account_type": "xing-square",
	"groups": [],
	"timeslots": [{
		"day": "Sun",
		"slot": [{
			"slot_id": "2616978",
			"timevalue": "10:34 AM"
		}, {
			"slot_id": "2616976",
			"timevalue": "03:54 PM"
		}, {
			"slot_id": "2616977",
			"timevalue": "09:09 PM"
		}]
	}, {
		"day": "Mon",
		"slot": [{
			"slot_id": "2616981",
			"timevalue": "10:34 AM"
		}, {
			"slot_id": "2616979",
			"timevalue": "03:54 PM"
		}, {
			"slot_id": "2616980",
			"timevalue": "09:09 PM"
		}]
	}, {
		"day": "Tue",
		"slot": [{
			"slot_id": "2616984",
			"timevalue": "10:34 AM"
		}, {
			"slot_id": "2616982",
			"timevalue": "03:54 PM"
		}, {
			"slot_id": "2616983",
			"timevalue": "09:09 PM"
		}]
	}, {
		"day": "Wed",
		"slot": [{
			"slot_id": "2616987",
			"timevalue": "10:34 AM"
		}, {
			"slot_id": "2616985",
			"timevalue": "03:54 PM"
		}, {
			"slot_id": "2616986",
			"timevalue": "09:09 PM"
		}]
	}, {
		"day": "Thu",
		"slot": [{
			"slot_id": "2616990",
			"timevalue": "10:34 AM"
		}, {
			"slot_id": "2616988",
			"timevalue": "03:54 PM"
		}, {
			"slot_id": "2616989",
			"timevalue": "09:09 PM"
		}]
	}, {
		"day": "Fri",
		"slot": [{
			"slot_id": "2616993",
			"timevalue": "10:34 AM"
		}, {
			"slot_id": "2616991",
			"timevalue": "03:54 PM"
		}, {
			"slot_id": "2616992",
			"timevalue": "09:09 PM"
		}]
	}, {
		"day": "Sat",
		"slot": [{
			"slot_id": "2616996",
			"timevalue": "10:34 AM"
		}, {
			"slot_id": "2616994",
			"timevalue": "03:54 PM"
		}, {
			"slot_id": "2616995",
			"timevalue": "09:09 PM"
		}]
	}]
}]
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Connect Accounts

This API will used to connect to account

### HTTP Request

`GET https://panel.socialpilot.co/oauth/connectaccounts`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"account": [{
		"account_name": "Twitter Profile",
		"account_type": "twitter",
		"account_data": [{
			"data_title": "",
			"data_field": [{
				"name": "connect a profile",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Ftwitter"
			}]
		}]
	}, {
		"account_name": "Facebook Profile",
		"account_type": "facebook",
		"account_data": [{
			"data_title": "Connect new FB Account",
			"data_field": [{
				"name": "Use Default Setting",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Ffacebook"
			}]
		}, {
			"data_title": "Custom FB Branding",
			"data_field": [{
				"name": "test",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Ffbbranding%253Fapp_id%253D599"
			}, {
				"name": "test12",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Ffbbranding%253Fapp_id%253D613"
			}]
		}]
	}, {
		"account_name": "Facebook Page",
		"account_type": "facebook-official",
		"account_data": [{
			"data_title": "Connected Accounts",
			"data_field": [{
				"name": "Rutul Gajjar",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fpage%253Flogin_id%253D36403"
			}, {
				"name": "Rutul Gajjar",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fpage%253Flogin_id%253D88177"
			}, {
				"name": "Ronak Patel",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fpage%253Flogin_id%253D88565"
			}]
		}, {
			"data_title": "Connect with new FB Account",
			"data_field": [{
				"name": "Use Default Setting",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Ffacebook%253Ftype%253Dpage"
			}]
		}, {
			"data_title": "Custom FB Branding",
			"data_field": [{
				"name": "test",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Ffbbranding%253Ftype%253Dpage%2526app_id%253D599"
			}, {
				"name": "test12",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Ffbbranding%253Ftype%253Dpage%2526app_id%253D613"
			}]
		}]
	}, {
		"account_name": "Facebook Group",
		"account_type": "users",
		"account_data": [{
			"data_title": "Connected Accounts",
			"data_field": [{
				"name": "Rutul Gajjar",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fgroup%253Flogin_id%253D36403"
			}, {
				"name": "Rutul Gajjar",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fgroup%253Flogin_id%253D88177"
			}, {
				"name": "Ronak Patel",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fgroup%253Flogin_id%253D88565"
			}]
		}, {
			"data_title": "Connect with new FB Account",
			"data_field": [{
				"name": "Use Default Setting",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Ffacebook%253Ftype%253Dgroup"
			}]
		}, {
			"data_title": "Custom FB Branding",
			"data_field": [{
				"name": "test",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Ffbbranding%253Fgroup%253Dpage%2526app_id%253D599"
			}, {
				"name": "test12",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Ffbbranding%253Fgroup%253Dpage%2526app_id%253D613"
			}]
		}]
	}, {
		"account_name": "LinkedIn Profile",
		"account_type": "linkedin",
		"account_data": [{
			"data_title": "",
			"data_field": [{
				"name": "connect a profile",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Flinkedin"
			}]
		}]
	}, {
		"account_name": "LinkedIn Page",
		"account_type": "suitcase",
		"account_data": [{
			"data_title": "",
			"data_field": [{
				"name": "rutull gajjar",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fpage%253Flogin_id%253D59621"
			}, {
				"name": "jigar testaccount",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fpage%253Flogin_id%253D99578"
			}, {
				"name": "Connect with new LinkedIn Account",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Flinkedin%253Ftype%253Dpage"
			}]
		}]
	}, {
		"account_name": "LinkedIn Group",
		"account_type": "linkedin-square",
		"account_data": [{
			"data_title": "",
			"data_field": [{
				"name": "rutull gajjar",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fgroup%253Flogin_id%253D59621"
			}, {
				"name": "jigar testaccount",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fgroup%253Flogin_id%253D99578"
			}, {
				"name": "Connect with new LinkedIn Account",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Flinkedin%253Ftype%253Dgroup"
			}]
		}]
	}, {
		"account_name": "Pinterest Board",
		"account_type": "pinterest-p",
		"account_data": [{
			"data_title": "",
			"data_field": [{
				"name": "connect a Board",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fpinterestauth"
			}]
		}]
	}, {
		"account_name": "Vk Profile",
		"account_type": "vk",
		"account_data": [{
			"data_title": "",
			"data_field": [{
				"name": "connect a profile",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fvkauth"
			}]
		}]
	}, {
		"account_name": "Vk Community",
		"account_type": "vk-group",
		"account_data": [{
			"data_title": "",
			"data_field": [{
				"name": "Rutul Gajjar",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fgroup%253Flogin_id%253D35734"
			}, {
				"name": "Connect with new Vk.com Account",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fvkauth%253Ftype%253Dgroup"
			}]
		}]
	}, {
		"account_name": "Xing Profile",
		"account_type": "xing",
		"account_data": [{
			"data_title": "",
			"data_field": [{
				"name": "connect a profile",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fxingauth"
			}]
		}]
	}, {
		"account_name": "Xing Pages",
		"account_type": "xing-square",
		"account_data": [{
			"data_title": "",
			"data_field": [{
				"name": "rutul gajjar",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fpage%253Flogin_id%253D71511"
			}, {
				"name": "ronak patel",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fpage%253Flogin_id%253D112444"
			}, {
				"name": "Jimit Bagadiya",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fpage%253Flogin_id%253D116583"
			}, {
				"name": "Connect with new Xing Account",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fxingauth%253Ftype%253Dpage"
			}]
		}]
	}, {
		"account_name": "Tumblr Blog",
		"account_type": "tumblr",
		"account_data": [{
			"data_title": "",
			"data_field": [{
				"name": "connect a Blog",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Ftumblrauth"
			}]
		}]
	}, {
		"account_name": "Instagram",
		"account_type": "instagram",
		"account_data": [{
			"data_title": "",
			"data_field": [{
				"name": "connect a profile",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Finstamoblogin"
			}]
		}]
	}, {
		"account_name": "Google+ Profile",
		"account_type": "google-plus",
		"account_data": [{
			"data_title": "",
			"data_field": [{
				"name": "connect a profile",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fgoogleauth"
			}]
		}]
	}, {
		"account_name": "Google+ Page",
		"account_type": "google-plus-square",
		"account_data": [{
			"data_title": "Connected Accounts",
			"data_field": [{
				"name": "Rutul Gajjar",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fpage%253Flogin_id%253D80048"
			}, {
				"name": "Connect with new Google+ profile",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fgoogleauth%253Ftype%253Dpage"
			}]
		}]
	}, {
		"account_name": "Google+ Collection",
		"account_type": "google-plus-official",
		"account_data": [{
			"data_title": "Connect a collection",
			"data_field": [{
				"name": "music",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fcollection%253Flogin_id%253D80044"
			}, {
				"name": "Rutul Gajjar",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fcollection%253Flogin_id%253D80048"
			}, {
				"name": "my page",
				"url": "https:\/\/panel.socialpilot.co\/oauth\/accountredirect?url=https%253A%252F%252Fpanel.socialpilot.co%252Faccounts%252Fcollection%253Flogin_id%253D88190"
			}]
		}]
	}]
}
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Edit Account

This api is used to edit account's name.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/account/update/{ACCOUNT_ID}`

<aside class="notice">
You must replace <code>{ACCOUNT_ID}</code> with your own account id in above api.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
account_name | Yes | It should be account name you edited.
group_id[position] | Yes | It should be group_id's array of groups which are connected to this account.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"data": {
		"id": 41342
	}
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": 1,
	"msg": "Something went wrong. Try again later."
}
```

## Delete Account

This api is used to delete account.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/account/delete/{ACCOUNT_ID}`

<aside class="notice">
You must replace <code>{ACCOUNT_ID}</code> with your own account id in above API.
</aside>


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Update Account Status

This API is used to update account status.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/account/status/{ACCOUNT_ID}`

<aside class="notice">
You must replace <code>{ACCOUNT_ID}</code> with your own account id in above API.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.

>Example Success Response:

>Response Code: 200

```json
 {
 	"error": 0,
 	"data": {
 		"new_status": "Paused"
 	}
 }
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": 1,
	"msg": "Something went wrong. Try again later."
}
```

## Add Account To Group

This API is used to add account to specific group.

### HTTP Request

`POST https://panel.socialpilot.co/oauth/account/add/{ACCOUNT_ID}`

<aside class="notice">
You must replace <code>{ACCOUNT_ID}</code> with your own account id in above API.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
group_id | Yes | It should be group_id to which you want to add your account.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"data": {
		"id": 36403
	}
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": 1,
	"msg": "Something went wrong. Try again later."
}
```


## Delete Account From Group

This API is used to delete account from specific group.

### HTTP Request

`POST https://panel.socialpilot.co/oauth/account/remove/{ACCOUNT_ID}`

<aside class="notice">
You must replace <code>{ACCOUNT_ID}</code> with your own account id in above API.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
group_id | Yes | It should be group_id to which you want to add your account.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"data": {
		"id": 36403
	}
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": 1,
	"msg": "Something went wrong. Try again later."
}
```

## Add TimeSlot

This API is used to add timeslot.

### HTTP Request

`POST https://panel.socialpilot.co/oauth/timeslot/create/{ACCOUNT_ID}`

<aside class="notice">
You must replace <code>{ACCOUNT_ID}</code> with your account_id in which you want to add new timeslot in above API.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
time_zone | Yes | It should be time_zone retrieve in response of settings web service.
timeslot | Yes | It should be time you like to schedule.
dayname[position] | Yes | It should be day name to which you want to add timeslot.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"slot_day": [{
		"day": "Tue",
		"slot_id": ""
	}, {
		"day": "Fri",
		"slot_id": "2679643"
	}, {
		"day": "Thu",
		"slot_id": "2679644"
	}]
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": 1,
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Delete TimeSlot

This API is used to delete timeslot.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/timeslot/delete/{SLOT_ID}`

<aside class="notice">
You must replace <code>{SLOT_ID}</code> with your slot_id which you want to delete in above API.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0
}
```

> Example Error Response:

>Response Code: 401

```json
{
	"error": 1,
	"msg": "Invalid access token provided. Check your access_token value"
}
```

# Groups

## Get All Groups

This api is used for fetching all groups.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/groups`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.

>Example Success Response:

>Response Code: 200

```json
[{
	"id": "17277",
	"group_name": "Test12345",
	"group_desc": "yyttty",
	"accounts": [{
		"id": "88193",
		"nickname": "mytestblog",
		"url": "http:\/\/mytestblog.tumblr.com\/",
		"status": "Running",
		"account_type": "tumblr"
	}, {
		"id": "35734",
		"nickname": "Rutul Gajjar",
		"url": "https:\/\/vk.com\/id306627681",
		"status": "Running",
		"account_type": "vk"
	}, {
		"id": "7696",
		"nickname": "Jimit Bagadiya",
		"url": "https:\/\/vk.com\/id305615613",
		"status": "Running",
		"account_type": "vk"
	}, {
		"id": "42791",
		"nickname": "my business",
		"url": "http:\/\/vk.com\/club99796837",
		"status": "Running",
		"account_type": "vk-group"
	}, {
		"id": "71512",
		"nickname": "super-rutul",
		"url": "http:\/\/super-rutul.tumblr.com\/",
		"status": "Running",
		"account_type": "tumblr"
	}, {
		"id": "108468",
		"nickname": "Creative Glance",
		"url": "https:\/\/www.pinterest.com\/jbagadiya\/creative-glance\/",
		"status": "Running",
		"account_type": "pinterest-p"
	}, {
		"id": "71527",
		"nickname": "test1",
		"url": "https:\/\/www.pinterest.com\/rutulg\/test1\/",
		"status": "Running",
		"account_type": "pinterest-p"
	}, {
		"id": "108469",
		"nickname": "Mobile Apps",
		"url": "https:\/\/www.pinterest.com\/jbagadiya\/mobile-apps\/",
		"status": "Running",
		"account_type": "pinterest-p"
	}, {
		"id": "99580",
		"nickname": "tes4",
		"url": "https:\/\/www.pinterest.com\/rutulg\/tes4\/",
		"status": "Running",
		"account_type": "pinterest-p"
	}, {
		"id": "53140",
		"nickname": "testing2",
		"url": "https:\/\/www.pinterest.com\/rutulg\/testing2\/",
		"status": "Running",
		"account_type": "pinterest-p"
	}, {
		"id": "80044",
		"nickname": "music",
		"url": "https:\/\/plus.google.com\/104651522595299228273",
		"status": "Running",
		"account_type": "google-plus-square"
	}, {
		"id": "88190",
		"nickname": "my page",
		"url": "https:\/\/plus.google.com\/105760589956175049099",
		"status": "Running",
		"account_type": "google-plus-square"
	}, {
		"id": "80046",
		"nickname": "music collection",
		"url": "https:\/\/plus.google.com\/collection\/kV2FkB",
		"status": "Running",
		"account_type": "google-plus-official"
	}, {
		"id": "99832",
		"nickname": "SocialPilot",
		"url": "http:\/\/www.linkedin.com\/company\/socialpilot",
		"status": "Running",
		"account_type": "suitcase"
	}, {
		"id": "59755",
		"nickname": "Mento.io",
		"url": "http:\/\/www.linkedin.com\/company\/mento-io",
		"status": "Running",
		"account_type": "suitcase"
	}, {
		"id": "99834",
		"nickname": "PocketApp.co",
		"url": "http:\/\/www.linkedin.com\/company\/pocketapps.co",
		"status": "Running",
		"account_type": "suitcase"
	}, {
		"id": "42788",
		"nickname": "Android",
		"url": "http:\/\/vk.com\/club107731330",
		"status": "Running",
		"account_type": "vk-group"
	}, {
		"id": "88177",
		"nickname": "Rutul Gajjar",
		"url": "https:\/\/www.facebook.com\/app_scoped_user_id\/269607903400321\/",
		"status": "Running",
		"account_type": "facebook"
	}, {
		"id": "71511",
		"nickname": "rutul gajjar",
		"url": "https:\/\/www.xing.com\/profile\/rutul_gajjar",
		"status": "Running",
		"account_type": "xing"
	}, {
		"id": "93017",
		"nickname": "harshil",
		"url": "https:\/\/www.instagram.com\/",
		"status": "Running",
		"account_type": "instagram"
	}, {
		"id": "99581",
		"nickname": "rutul123",
		"url": "https:\/\/www.instagram.com\/",
		"status": "Running",
		"account_type": "instagram"
	}]
}, {
	"id": "17279",
	"group_name": "Ghfhfhfbfhhh1",
	"group_desc": "",
	"accounts": [{
		"id": "810",
		"nickname": "SocialPilot",
		"url": "http:\/\/www.twitter.com\/socialpilot_co",
		"status": "Running",
		"account_type": "twitter"
	}, {
		"id": "36403",
		"nickname": "Rutul Gajjar",
		"url": "https:\/\/www.facebook.com\/app_scoped_user_id\/111494222545024\/",
		"status": "Running",
		"account_type": "facebook"
	}, {
		"id": "74156",
		"nickname": "jigar_murabiya",
		"url": "http:\/\/www.twitter.com\/jigar_murabiya",
		"status": "Running",
		"account_type": "twitter"
	}, {
		"id": "80048",
		"nickname": "Rutul Gajjar",
		"url": "https:\/\/plus.google.com\/104837002510557825022",
		"status": "Running",
		"account_type": "google-plus"
	}, {
		"id": "71512",
		"nickname": "super-rutul",
		"url": "http:\/\/super-rutul.tumblr.com\/",
		"status": "Running",
		"account_type": "tumblr"
	}, {
		"id": "88193",
		"nickname": "mytestblog",
		"url": "http:\/\/mytestblog.tumblr.com\/",
		"status": "Running",
		"account_type": "tumblr"
	}, {
		"id": "7696",
		"nickname": "Jimit Bagadiya",
		"url": "https:\/\/vk.com\/id305615613",
		"status": "Running",
		"account_type": "vk"
	}, {
		"id": "35734",
		"nickname": "Rutul Gajjar",
		"url": "https:\/\/vk.com\/id306627681",
		"status": "Running",
		"account_type": "vk"
	}, {
		"id": "80044",
		"nickname": "music",
		"url": "https:\/\/plus.google.com\/104651522595299228273",
		"status": "Running",
		"account_type": "google-plus-square"
	}, {
		"id": "88190",
		"nickname": "my page",
		"url": "https:\/\/plus.google.com\/105760589956175049099",
		"status": "Running",
		"account_type": "google-plus-square"
	}, {
		"id": "99832",
		"nickname": "SocialPilot",
		"url": "http:\/\/www.linkedin.com\/company\/socialpilot",
		"status": "Running",
		"account_type": "suitcase"
	}, {
		"id": "99833",
		"nickname": "Creative Glance Technologies",
		"url": "http:\/\/www.linkedin.com\/company\/creative-glance-technologies",
		"status": "Running",
		"account_type": "suitcase"
	}, {
		"id": "59755",
		"nickname": "Mento.io",
		"url": "http:\/\/www.linkedin.com\/company\/mento-io",
		"status": "Running",
		"account_type": "suitcase"
	}, {
		"id": "99834",
		"nickname": "PocketApp.co",
		"url": "http:\/\/www.linkedin.com\/company\/pocketapps.co",
		"status": "Running",
		"account_type": "suitcase"
	}, {
		"id": "42788",
		"nickname": "Android",
		"url": "http:\/\/vk.com\/club107731330",
		"status": "Running",
		"account_type": "vk-group"
	}, {
		"id": "88177",
		"nickname": "Rutul Gajjar",
		"url": "https:\/\/www.facebook.com\/app_scoped_user_id\/269607903400321\/",
		"status": "Running",
		"account_type": "facebook"
	}, {
		"id": "99578",
		"nickname": "jigar testaccount",
		"url": "http:\/\/www.linkedin.com\/profile\/view?id=PgAvYfSBXo",
		"status": "Paused",
		"account_type": "linkedin"
	}, {
		"id": "41342",
		"nickname": "rutul110",
		"url": "http:\/\/www.twitter.com\/rutul110",
		"status": "Running",
		"account_type": "twitter"
	}, {
		"id": "103085",
		"nickname": "Test123",
		"url": "https:\/\/www.facebook.com\/Test-1351588231539525\/",
		"status": "Paused",
		"account_type": "facebook-official"
	}]
}]
```

> Example Error Response:

>Response Code: 401

```json
{
	"error": 1,
	"msg": "Invalid access token provided. Check your access_token value"
}
```


## Create Group

This api is used to create new group.

### HTTP Request

`POST https://panel.socialpilot.co/oauth/group/create`

<aside class="notice">
You must replace <code>{ACCOUNT_ID}</code> with your own account id in above API.
</aside>


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
group_name | Yes | It should be name with at least 5 characters.
description | No | Whatever description you like to add about this group.
account_id[position] | No | It should be account_id of account which you want to add in this group.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"data": {
		"group_id": "20687"
	}
}
```

> Example Error Response:

>Response Code: 401

```json
{
	"error": 1,
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Delete Group

This api is used to delete group.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/group/delete/{GROUP_ID}`

<aside class="notice">
You must replace <code>{GROUP_ID}</code> with your own group id in above API.
</aside>


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Edit Group

This api is used to edit group details.

### HTTP Request

`POST https://panel.socialpilot.co/oauth/group/update/{GROUP_ID}`

<aside class="notice">
You must replace <code>{GROUP_ID}</code> with your own group id in above API.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
group_name | Yes | It should be name of group at least of 5 characters.
description | No | It should be description of your group.
account_id[position] | Yes | It should be account_id's array of accounts which are connected to this account.


>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"data": {
		"group_id": "20687"
	}
}
```

> Example Error Response:

>Response Code: 401

```json
{
	"error": 1,
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Add Group To Account

This API is used to add account to this group.

### HTTP Request

`POST https://panel.socialpilot.co/oauth/group/add/{GROUP_ID}`

<aside class="notice">
You must replace <code>{GROUP_ID}</code> with your own group id in above API.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
account_id | Yes | It should be account_id which you want to add to this group.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"data": {
		"group_id": "19677"
	}
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": 1,
	"msg": "Something went wrong. Try again later."
}
```

## Delete Group From Account

This API is used to delete account from this group.

### HTTP Request

`POST https://panel.socialpilot.co/oauth/group/remove/{GROUP_ID}`

<aside class="notice">
You must replace <code>{GROUP_ID}</code> with your own group id in above API.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
account_id | Yes | It should be account_id which you want to delete from this group.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"data": {
		"group_id": "19677"
	}
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": 1,
	"msg": "Something went wrong. Try again later."
}
```

# Device Token

## Send Device Token

This api is used to send device token to server.

### HTTP Request

`POST https://panel.socialpilot.co/oauth/devicetoken`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
version | Yes | It should be current version of your phone.
device_token | Yes | It should be device token received from FCM server.
device_model | Yes | It should be your device's model.
app_version | Yes | It should be current version of your app same as in your app level build.gradle file.
os | Yes | It should be os of your device.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

# Posts

## Queued Posts

This api is used for fetching queued posts.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/post/queue`

<aside class="notice">
If we don't want any kind of filter ie. default filter would be "Accounts - All", for this we don't need to pass "filter" and "id" parameters.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
p | No | It should be page number for doing pagination if the value of "nextpage" in previous response is not blank.
filter | No | It should be filter name i.e. accounts, groups, team member, clients, etc.
id | No | It should be filter id.
team_owner_id | Yes | It should be "0" for MyPanel or ownerid of team selected.

>Example Success Response:

>Response Code: 200

><aside class="notice">
If "nextpage" parameter in below response contains any url, just call this url for pagination.
</aside>

```json
{
	"posts": [{
		"log_id": "10053065",
		"account": {
			"account_id": 110538,
			"account_url": "https:\/\/www.facebook.com\/My-name-1240112166000411\/",
			"account_username": "My name",
			"is_deleted": "N",
			"account_type": "facebook-official"
		},
		"post_content": "If you're managing your own social media marketing, automation tools come in handy\u2026especially since timing of getting content out there is critical o engaging your audience. http:\/\/bit.ly\/2scQBbB ",
		"post_title": "",
		"description": "If you're managing your own social media marketing, automation tools come in handy\u2026especially since timing of getting content out there is critical o engaging your audience. http:\/\/bit.ly\/2scQBbB ",
		"post_image": "http:\/\/www.socialmediatoday.com\/sites\/default\/files\/aashish%20sarma\/files\/Sendible-600x340.png",
		"post_type": "I",
		"post_url": "https:\/\/goo.gl\/PsJPkB",
		"posttime_format": "Jun 17, 2017 12:05 PM",
		"post_video": "",
		"post_status": "Y",
		"post_extra_params": "{\"aspect_ratio\":\"64:33\",\"duration\":\"00:17\",\"bit_rate\":308567,\"frame_rate\":\"30\/1\",\"video_codec\":\"h264\",\"width\":640,\"height\":330,\"video_frames\":516,\"pixel_aspect_ratio\":\"1:1\",\"duration_sec\":17,\"size\":670455,\"mime_type\":\"video\/mp4\",\"video_key\":\"JXNa81497594241598.mp4\"}",
		"is_paused": "N",
		"thumb_image": "https:\/\/panel.socialpilot.co\/themes\/socialpilot\/assets\/timthumb.php?w=60&h=60&zc=1&src=http:\/\/www.socialmediatoday.com\/sites\/default\/files\/aashish%20sarma\/files\/Sendible-600x340.png",
		"access_type": "O",
		"via": "Web",
		"created_on": "2017-06-17 06:34:28",
		"by": "Rutul"
	}],
	"queuecnt": 1
}
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Unscheduled Posts

This api is used for fetching unscheduled posts.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/post/unscheduled`

<aside class="notice">
If we don't want any kind of filter ie. default filter would be "Accounts - All", for this we don't need to pass "filter" and "id" parameters.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
p | No | It should be page number for doing pagination if the value of "nextpage" in previous response is not blank.
filter | No | It should be filter name i.e. accounts, groups, team member, clients, etc.
id | No | It should be filter id.
team_owner_id | Yes | It should be "0" for MyPanel or ownerid of team selected.


>Example Success Response:

>Response Code: 200

><aside class="notice">
If "nextpage" parameter in below response contains any url, just call this url for pagination.
</aside>

```json
{
	"posts": [{
		"log_id": "10053065",
		"account": {
			"account_id": 110538,
			"account_url": "https:\/\/www.facebook.com\/My-name-1240112166000411\/",
			"account_username": "My name",
			"is_deleted": "N",
			"account_type": "facebook-official"
		},
		"post_content": "If you're managing your own social media marketing, automation tools come in handy\u2026especially since timing of getting content out there is critical o engaging your audience. http:\/\/bit.ly\/2scQBbB ",
		"post_title": "",
		"description": "If you're managing your own social media marketing, automation tools come in handy\u2026especially since timing of getting content out there is critical o engaging your audience. http:\/\/bit.ly\/2scQBbB ",
		"post_image": "http:\/\/www.socialmediatoday.com\/sites\/default\/files\/aashish%20sarma\/files\/Sendible-600x340.png",
		"post_type": "I",
		"post_url": "https:\/\/goo.gl\/PsJPkB",
		"posttime_format": "Jun 17, 2017 12:05 PM",
		"post_video": "",
		"post_status": "Y",
		"post_extra_params": "{\"aspect_ratio\":\"64:33\",\"duration\":\"00:17\",\"bit_rate\":308567,\"frame_rate\":\"30\/1\",\"video_codec\":\"h264\",\"width\":640,\"height\":330,\"video_frames\":516,\"pixel_aspect_ratio\":\"1:1\",\"duration_sec\":17,\"size\":670455,\"mime_type\":\"video\/mp4\",\"video_key\":\"JXNa81497594241598.mp4\"}",
		"is_paused": "N",
		"thumb_image": "https:\/\/panel.socialpilot.co\/themes\/socialpilot\/assets\/timthumb.php?w=60&h=60&zc=1&src=http:\/\/www.socialmediatoday.com\/sites\/default\/files\/aashish%20sarma\/files\/Sendible-600x340.png",
		"access_type": "O",
		"via": "Web",
		"created_on": "2017-06-17 06:34:28",
		"by": "Rutul"
	}],
	"nextpage": "",
	"recordcnt": 3
}
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Error Posts

This api is used for fetching error posts.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/post/errors`

<aside class="notice">
If we don't want any kind of filter ie. default filter would be "Accounts - All", for this we don't need to pass "filter" and "id" parameters.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
p | No | It should be page number for doing pagination if the value of "nextpage" in previous response is not blank.
filter | No | It should be filter name i.e. accounts, groups, team member, clients, etc.
id | No | It should be filter id.
team_owner_id | Yes | It should be "0" for MyPanel or ownerid of team selected.

>Example Success Response:

>Response Code: 200

><aside class="notice">
If "nextpage" parameter in below response contains any url, just call this url for pagination.
</aside>

```json
{
	"posts": [{
		"log_id": "10053065",
		"account": {
			"account_id": 110538,
			"account_url": "https:\/\/www.facebook.com\/My-name-1240112166000411\/",
			"account_username": "My name",
			"is_deleted": "N",
			"account_type": "facebook-official"
		},
		"post_content": "If you're managing your own social media marketing, automation tools come in handy\u2026especially since timing of getting content out there is critical o engaging your audience. http:\/\/bit.ly\/2scQBbB ",
		"post_title": "",
		"description": "If you're managing your own social media marketing, automation tools come in handy\u2026especially since timing of getting content out there is critical o engaging your audience. http:\/\/bit.ly\/2scQBbB ",
		"post_image": "http:\/\/www.socialmediatoday.com\/sites\/default\/files\/aashish%20sarma\/files\/Sendible-600x340.png",
		"post_type": "I",
		"post_url": "https:\/\/goo.gl\/PsJPkB",
		"posttime_format": "Jun 17, 2017 12:05 PM",
		"post_video": "",
		"post_status": "Y",
		"post_extra_params": "{\"aspect_ratio\":\"64:33\",\"duration\":\"00:17\",\"bit_rate\":308567,\"frame_rate\":\"30\/1\",\"video_codec\":\"h264\",\"width\":640,\"height\":330,\"video_frames\":516,\"pixel_aspect_ratio\":\"1:1\",\"duration_sec\":17,\"size\":670455,\"mime_type\":\"video\/mp4\",\"video_key\":\"JXNa81497594241598.mp4\"}",
		"is_paused": "N",
		"thumb_image": "https:\/\/panel.socialpilot.co\/themes\/socialpilot\/assets\/timthumb.php?w=60&h=60&zc=1&src=http:\/\/www.socialmediatoday.com\/sites\/default\/files\/aashish%20sarma\/files\/Sendible-600x340.png",
		"access_type": "O",
		"via": "Web",
		"created_on": "2017-06-17 06:34:28",
		"by": "Rutul"
	}],
	"nextpage": "",
	"recordcnt": 3
}
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Delivered Posts

This api is used for fetching delivered posts.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/post/deliverd`

<aside class="notice">
If we don't want any kind of filter ie. default filter would be "Accounts - All", for this we don't need to pass "filter" and "id" parameters.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
p | No | It should be page number for doing pagination if the value of "nextpage" in previous response is not blank.
filter | No | It should be filter name i.e. accounts, groups, team member, clients, etc.
id | No | It should be filter id.
team_owner_id | Yes | It should be "0" for MyPanel or ownerid of team selected.

>Example Success Response:

><aside class="notice">
If "nextpage" parameter in below response contains any url, just call this url for pagination.
</aside>

>Response Code: 200

```json
{
	"posts": [{
		"log_id": "10053065",
		"account": {
			"account_id": 110538,
			"account_url": "https:\/\/www.facebook.com\/My-name-1240112166000411\/",
			"account_username": "My name",
			"is_deleted": "N",
			"account_type": "facebook-official"
		},
		"post_content": "If you're managing your own social media marketing, automation tools come in handy\u2026especially since timing of getting content out there is critical o engaging your audience. http:\/\/bit.ly\/2scQBbB ",
		"post_title": "",
		"description": "If you're managing your own social media marketing, automation tools come in handy\u2026especially since timing of getting content out there is critical o engaging your audience. http:\/\/bit.ly\/2scQBbB ",
		"post_image": "http:\/\/www.socialmediatoday.com\/sites\/default\/files\/aashish%20sarma\/files\/Sendible-600x340.png",
		"post_type": "I",
		"post_url": "https:\/\/goo.gl\/PsJPkB",
		"posttime_format": "Jun 17, 2017 12:05 PM",
		"post_video": "",
		"post_status": "Y",
		"post_extra_params": "{\"aspect_ratio\":\"64:33\",\"duration\":\"00:17\",\"bit_rate\":308567,\"frame_rate\":\"30\/1\",\"video_codec\":\"h264\",\"width\":640,\"height\":330,\"video_frames\":516,\"pixel_aspect_ratio\":\"1:1\",\"duration_sec\":17,\"size\":670455,\"mime_type\":\"video\/mp4\",\"video_key\":\"JXNa81497594241598.mp4\"}",
		"is_paused": "N",
		"thumb_image": "https:\/\/panel.socialpilot.co\/themes\/socialpilot\/assets\/timthumb.php?w=60&h=60&zc=1&src=http:\/\/www.socialmediatoday.com\/sites\/default\/files\/aashish%20sarma\/files\/Sendible-600x340.png",
		"access_type": "O",
		"via": "Web",
		"created_on": "2017-06-17 06:34:28",
		"by": "Rutul"
	}],
	"nextpage": "https:\/\/panel.socialpilot.co\/oauth\/post\/deliverd\/2",
	"recordcnt": 1513
}
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Contributed Posts

<aside class="notice">
If we don't want any kind of filter ie. default filter would be "Accounts - All", for this we don't need to pass "filter" and "id" parameters.
</aside>

This api is used for fetching delivered posts.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/post/contribute`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
p | No | It should be page number for doing pagination if the value of "nextpage" in previous response is not blank.
filter | No | It should be filter name i.e. accounts, groups, team member, clients, etc.
id | No | It should be filter id.
team_owner_id | Yes | It should be "0" for MyPanel or ownerid of team selected.

>Example Success Response:

><aside class="notice">
If "nextpage" parameter in below response contains any url, just call this url for pagination.
</aside>

>Response Code: 200

```json
{
	"posts": [],
	"nextpage": "",
	"recordcnt": 0
}
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Create Post without image

This api is used for creating new post without image.

### HTTP Request

`POST https://panel.socialpilot.co/oauth/post/update`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
group_id | No | A group id whose associated accounts will receive the status update. Invalid ids will be ignored.
now | No | If now is set to true, this update will be sent immediately.
schedule_date | No | A date describing when the update should be posted. Overrides now parameter. If no UTC offset is specified, UTC is assumed.
post_content | Yes | It should be post content you edited.
account_id[position] | Yes | It should be account id from which you are creating this post.
preview[title]| No | A preview title
preview[url]| No |An URL of the preview title
preview[image]| No | A preview image path
preview[description]| No | A short description for the preview
post_image| No | No need to send this parameter now

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"data": {
		"post_id": ""
	},
	"msg": "Post successfully created!",
	"is_break": 0
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": "1",
	"msg": "Invalid post data"
}
```

## Create Post with image

This api is used for creating new post with image.

### HTTP Request

####Create post with image

`POST https://panel.socialpilot.co/oauth/post/updatewithimage`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
group_id | No | A group id whose associated accounts will receive the status update. Invalid ids will be ignored.
post_content | No | It should be post content you edited.
account_id[position] | Yes | It should be account id from which you are creating this post.
post_image| No | No need to send this parameter now
now | No | If now is set to true, this update will be sent immediately.
schedule_date | No | A date describing when the update should be posted. Overrides now parameter. If no UTC offset is specified, UTC is assumed.
image_url| No | S3's image url if its image post
video_url| No | S3's video url if its video post
is_new_video| No | Only when sharing same post from delivered tab ("1" if new video, else "0" if same old video)
post_extra_params| No | Only when resharing post from delivered tab (the value for this parameter is provided in all apis like queue, deleivred, etc. api, send the same value here)

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"data": {
		"post_id": ""
	},
	"msg": "Post successfully created!",
	"is_break": 0
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": "1",
	"msg": "Missing data"
}
```

## Delete Post

This api is used for deleting post.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/post/delete/{POST_ID}`

<aside class="notice">
<code>{POST_ID}</code> is to be replaced with your post_id.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
from | No | It should be only in case of contributed posts.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": 1,
	"msg": "Something went wrong. Try again later."
}
```

## Move To Top Post

This api is used for moving post to top.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/post/movetotop/{POST_ID}`

<aside class="notice">
<code>{POST_ID}</code> is to be replaced with your post_id.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": 1,
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Share Post

This api is used for sharing the post.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/post/sharenow/{POST_ID}`

<aside class="notice">
<code>{POST_ID}</code> is to be replaced with your post_id.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
from | No | It should be only in case of error posts.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": 1,
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Schedule Post

This api is used for sharing the post.

### HTTP Request

`POST https://panel.socialpilot.co/oauth/post/shareon/{POST_ID}`

<aside class="notice">
<code>{POST_ID}</code> is to be replaced with your post_id.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
postdate | Yes | It should be date on which you want to schedule your post.
posttime | Yes | It should be time on when want to schedule your post.
from | No | It should be only in case of error posts.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": 1,
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Add To Queue

This api is to add post to queue.

### HTTP Request

`POST https://panel.socialpilot.co/oauth/post/addtoqueue/{POST_ID}`

<aside class="notice">
<code>{POST_ID}</code> is to be replaced with your post_id.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
from | No | It should be only in case of error posts.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": 1,
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Approve

This api is to approve post for contribution.

### HTTP Request

`POST https://panel.socialpilot.co/oauth/post/approve/{POST_ID}`

<aside class="notice">
<code>{POST_ID}</code> is to be replaced with your post_id.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": 1,
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Edit Post

This api is used for editing post.

### HTTP Request

`POST https://panel.socialpilot.co/oauth/post/edit/{POST_ID}`

<aside class="notice">
<code>{POST_ID}</code> is to be replaced with your post_id.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
post_content| No | It is compulsory to write content if you are not attaching image.
is_removed | Yes | Either Y or N.
from | No | It should be only in case of contributed posts. 
post_image| No | No need to send this parameter now
image_url| No | S3's image url if its image post
video_url| No | S3's video url if its video post
is_new_video| No | Only when sharing same post from delivered tab ("1" if new video, else "0" if same old video)
post_extra_params| No | Only when resharing post from delivered tab (the value for this parameter is provided in all apis like queue, deleivred, etc. api, send the same value here)


>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"img_url": "https:\/\/socialpilotassets.s3.amazonaws.com\/postsimages\/dgxvv820ob2afu4.jpg"
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": "1",
	"msg": "<div><ul><li>Content cannot be blank</li></ul></div>"
}
```

## Filters for Posts

This api is used for fetching filters list which are used for filtering posts data.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/filteroption`

<aside class="notice">
You need to add groups and accounts list to the data received from above api.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
team_owner_id | Yes | It should be "0" for MyPanel or ownerid of team selected.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"msg": "",
	"filter_data": [{
		"name": "Team Member",
		"data": []
	}, {
		"name": "Clients",
		"data": [{
			"id": "237",
			"name": "ronak"
		}, {
			"id": "261",
			"name": "ravi"
		}, {
			"id": "431",
			"name": "ronu_2"
		}, {
			"id": "432",
			"name": "ronu_3"
		}, {
			"id": "573",
			"name": "Automation Team29_03_2017_12_18_53"
		}]
	}]
}
```

> Example Error Response:

>Response Code: 401
 
```json

{
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value",
	"access_token_expire": "1"
}
```
## Posts Count

This api is used for getting total posts count, queued post count, etc.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/postcount`

<aside class="notice">
If we don't want any kind of filter ie. default filter would be "Accounts - All", for this we don't need to pass "filter" and "id" parameters.
</aside>

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
filter | No | It should be filter name i.e. accounts, groups, team member, clients, etc.
id | No | It should be filter id.
team_owner_id | Yes | It should be "0" for MyPanel or ownerid of team selected.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"count": {
		"error": "0",
		"unschedule": "1",
		"contrituter": "4",
		"queue": "2"
	}
}
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```



# Insta Notifications

## Get Notifications

This api is used for getting instagram notifications.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/instagramnotification`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
team_owner_id | Yes | It should be "0" for MyPanel or ownerid of team selected.

>Example Success Response:

>Response Code: 200

```json
{
	"recordcnt": "323",
	"nextpage": "https:\/\/panel.socialpilot.co\/oauth\/instanotification?p=2",
	"error": 0,
	"posts": [{
		"image_url": "https:\/\/asset.socialpilot.co\/wp-content\/uploads\/2015\/07\/facebook_banner1.png",
		"thumb_image": "https:\/\/panel.socialpilot.co\/themes\/socialpilot\/assets\/timthumb.php?w=340&h=80&zc=1&src=https:\/\/asset.socialpilot.co\/wp-content\/uploads\/2015\/07\/facebook_banner1.png",
		"content": "SocialPilot: Social Media Scheduling & Marketing Automation Tool https:\/\/socialpilot.co ",
		"account_username": "harshil",
		"last_shared_on": "Apr 20, 2017 11:08 AM"
	}, {
		"image_url": "https:\/\/asset.socialpilot.co\/wp-content\/uploads\/2016\/06\/social-media-image-size-fb.png",
		"thumb_image": "https:\/\/panel.socialpilot.co\/themes\/socialpilot\/assets\/timthumb.php?w=340&h=80&zc=1&src=https:\/\/asset.socialpilot.co\/wp-content\/uploads\/2016\/06\/social-media-image-size-fb.png",
		"content": "The Complete Social Media Image Sizes Cheat Sheet http:\/\/bit.ly\/2p4iCnw ",
		"account_username": "ravi44shah",
		"last_shared_on": "Apr 20, 2017 08:13 AM"
	}]
}
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```




# Suggestions

## Get Suggestion Categories

This api is used for fetching categories of suggestions.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/suggestion/category`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.

>Example Success Response:

>Response Code: 200

```json
[{
	"name": "Business",
	"id": "2"
}, {
	"name": "Car & Vehicles",
	"id": "3"
}, {
	"name": "Construction & Real Estate",
	"id": "16"
}, {
	"name": "Education",
	"id": "15"
}, {
	"name": "Fashion",
	"id": "6"
}, {
	"name": "Health & Fitness",
	"id": "13"
}, {
	"name": "Inspiration",
	"id": "11"
}, {
	"name": "Lifehacking",
	"id": "14"
}, {
	"name": "Marketing",
	"id": "4"
}, {
	"name": "Photography",
	"id": "7"
}, {
	"name": "Sports",
	"id": "17"
}, {
	"name": "Startups",
	"id": "5"
}, {
	"name": "Tech",
	"id": "1"
}, {
	"name": "Travel",
	"id": "9"
}]
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Get Suggestions

This api is used for fetching suggestions.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/suggestionwithpage`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
nextpage | No | If pagination is to be performed, use this parameter.
id | No | If suggestions are to be filtered using category id.

>Example Success Response:

>Response Code: 200

```json
{
	"data": [{
		"id": "36855",
		"post_content": "Here are the world's largest weapons exporters https:\/\/goo.gl\/cPXCBj",
		"description": "Here are the world\\'s largest weapons exporters",
		"title": "Here are the world's largest weapons exporters",
		"category": {
			"id": 2,
			"name": "Business"
		},
		"image": "",
		"url": "https:\/\/goo.gl\/cPXCBj"
	}, {
		"id": "36860",
		"post_content": "When You Learn A Second Language, These 7 Amazing Things Will Happen To You https:\/\/goo.gl\/TlMHPG",
		"description": "When You Learn A Second Language, These 7 Amazing Things Will Happen To You",
		"title": "When You Learn A Second Language, These 7 Amazing Things Will Happen To You",
		"category": {
			"id": 14,
			"name": "Lifehacking"
			},
		"image": "http:\/\/i.amz.mshcdn.com\/KSCQeXebHwkv6YMcpm-JU549ze4=\/575x323\/filters:quality(90)\/https%3A%2F%2Fblueprint-api-production.s3.amazonaws.com%2Fuploads%2Fcard%2Fimage%2F364966%2F08147d4b-988a-4a3f-b23d-4f2838a2a4b5.jpg",
		"url": "https:\/\/goo.gl\/Jwyx0o"
	}],
	"nextpage": "https:\/\/panel.socialpilot.co\/oauth\/suggetionwithpage?nextpage=3",
	"recordcnt": 16180,
	"s_id": 0
}
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

# Feeds

## Get Feed Categories

This api is used for fetching categories of feeds.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/getfeednames`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
team_owner_id | Yes | It should be "0" for MyPanel or ownerid of team selected.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"feed": [{
		"name": "Juhi",
		"id": "2108"
	}, {
		"name": "Digisha",
		"id": "2148"
	}, {
		"name": "socialpilot",
		"id": "3249"
	}]
}
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

## Get Feeds

This api is used for fetching feeds.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/getfeeds`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.
id | No | If feeds are to be filtered using category id.
team_owner_id | Yes | It should be "0" for MyPanel or ownerid of team selected.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"recordcnt": 40,
	"pfeed": [{
		"account_id": ["59155", "69245"]
	}, {
		"account_id": ["59155", "69245"]
	}, {
		"account_id": ["35734"]
	}],
	"feeds": [{
		"post_title": "Mobile recharge shops in India's largest state are selling phone numbers of young girls: Report",
		"post_url": "http:\/\/mashable.com\/2017\/02\/03\/mobile-recharge-outlets-sell-phone-number-girls-india\/",
		"post_image": "http:\/\/i.amz.mshcdn.com\/XROe_CSVCpJFzyOwtEEHhCRe1iw=\/575x323\/filters:quality(90)\/https%3A%2F%2Fblueprint-api-production.s3.amazonaws.com%2Fuploads%2Fcard%2Fimage%2F371091%2Fb58c8b7b-b86a-4604-a502-c38fa4b0d03a.jpg",
		"long_post_desc": "A new safety issue has surfaced for young girls in northern India.&nbsp; Phone recharge shops in Uttar Pradesh, India's largest state by geography, are reportedly selling mobile phone numbers of innocent girls. SEE ALSO: Women in this country are marching for their right to go out Local police say t&hellip;",
		"via": "Mashable",
		"Published": "Published on Feb 03, 2017 09:01 AM",
		"post_desc": "Mobile recharge shops in India's largest state are selling phone numbers of young girls: Report - http:\/\/mashable.com\/2017\/02\/03\/mobile-recharge-outlets-sell-phone-number-girls-india\/"
	}, {
		"post_title": "Samsung Pay to launch in India in first half of 2017",
		"post_url": "http:\/\/mashable.com\/2017\/02\/03\/samsung-pay-india-launch\/",
		"post_image": "http:\/\/i.amz.mshcdn.com\/Jht2watZczziqMLuYvoRVlcewqo=\/575x323\/filters:quality(90)\/https%3A%2F%2Fblueprint-api-production.s3.amazonaws.com%2Fuploads%2Fcard%2Fimage%2F371059%2F12563067-f3e5-4be4-84db-20bb7535c6a7.jpg",
		"long_post_desc": "Domestic companies cashing in on India&rsquo;s cash crunched market with epayment solutions will soon have competition from a global technology giant &mdash; Samsung. SEE ALSO: Google is thinking about bringing digital payment services to India Samsung plans to launch its Samsung Pay mobile payment&hellip;",
		"via": "Mashable",
		"Published": "Published on Feb 03, 2017 08:32 AM",
		"post_desc": "Samsung Pay to launch in India in first half of 2017 - http:\/\/mashable.com\/2017\/02\/03\/samsung-pay-india-launch\/"
	}]
}
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```

# Membership

## Trial Membership

This api is used for activating trial membership.

### HTTP Request

`GET https://panel.socialpilot.co/oauth/trialmembership`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
access_token | Yes | It should be accesstoken provided from server on user's successful login.

>Example Success Response:

>Response Code: 200

```json
{
	"error": 0,
	"msg": "Your membership is successfully upgraded. Enjoy Pro benefits!"
}
```

> Example Error Response:

>Response Code: 401
 
 ```json
 {
	"error": "1",
	"msg": "Invalid access token provided. Check your access_token value"
}
```





