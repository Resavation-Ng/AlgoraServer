# Agora Node Token Server

This is an example of a simple Node/Express server that generates tokens for Agora applications.

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

### Run the server

Install the dependencies

```node
npm install
```

Start the service

```node
npm start
```

## Endpoints

### Ping

**endpoint structure**

```
/ping
```

response:

```
{"message":"pong"}
```

### RTC Token

The `rtc` token endpoint requires a `tokentype` (uid || userAccount), `channelName`, and the user's `uid` (type varies based on `tokentype`).
`(optional)` Pass an integer to represent the token lifetime in seconds.

**endpoint structure**

```
/rtc/:channelName/:role/:tokentype/:uid/?expiry=
```

response:

```
{"rtcToken":" "}
```

## RTM Token

The `rtm` token endpoint requires the user's `uid`.
`(optional)` Pass an integer to represent the privelege lifetime in seconds.
**endpoint structure**

```
/rtm/:uid/?expiry=
```

response:

```
{"rtmToken":" "}
```

### Both Tokens

The `rte` token endpoint generates both the `rtc` and `rtm` tokens with a single request. This endpoint requires a `tokentype` (uid || userAccount), `channelName`, and the user's `uid` (type varies `String/Int` based on `tokentype`).
`(optional)` Pass an integer to represent the token lifetime in seconds.

**endpoint structure**

```
/rte/:channelName/:role/:tokentype/:uid/?expiry=
```

response:

```
{
  "rtcToken":" ",
  "rtmToken":" "
}
```

e.g
https://agora-tokens-server.herokuapp.com/rtc/test/publisher/uid/1
https://agora-tokens-server.herokuapp.com/rtc/test/publisher/uid/1?expiry=1000
https://agora-tokens-server.herokuapp.com/rtc/test/subscriber/userAccount/ekaansh
