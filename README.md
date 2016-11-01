[![](http://i.imgur.com/iJQSL9a.png)](https://numbarapp.com)

# Numbar Documentation

Keep an eye on your most important metric. Numbar is a macOS app that displays _your_ most valued metrics in your menu bar. Learn how to get started in seconds, using the instructions below.

[![](http://i.imgur.com/cnvGseA.png)](https://numbarapp.com)
  
![](http://i.imgur.com/bWhaMrs.png)

  <br/><br/><br/>


## Table of Contents

- [How it Works](#how-it-works)
- [Getting Started](#getting-started)
- [Dropdown](#dropdown)
- [Security (Basic Auth)](#security-basic-auth)
- [Headers](#headers)  

<br/><br/><br/>

## How it Works

![](http://i.imgur.com/jLMqBiF.png)

  <br/><br/><br/>

## Getting Started

To get started, output some JSON with a property called `primary` with a value or metric that is very important to you. This should be a value that often changes and something you want to keep a close eye on at all times. 

For example, you could output your business' daily revenue, or count the number of today’s new users from your database.

```
{
  "primary": "$123.42"
}
```

<img src="http://i.imgur.com/7tO6Mxm.png" alt="" width="421">

Next, make this JSON publically available online and accessible from a URL. You'll want to visit your JSON's URL to verify your important metric is displaying correctly. (Note: You can protect this endpoint using Basic Auth. [Learn More](#security-basic-auth))

Finally, copy the URL for your JSON and paste it in the “Endpoint” setting inside of the Numbar app preferences:

<img src="http://i.imgur.com/zXGVgMO.png" alt="" width="450">

Numbar will now ping your endpoint every 30 seconds and check for any changes. If there is a change, that new value will reflect in your macOS menu bar. 

Note: You can modify the update interval inside the Numbar General Preferences.

  <br/><br/><br/>

## Dropdown

Displaying one important metric is great, but sometimes you need to access more data quickly. You can extend your metrics using the Numbar dropdown.

To display more metrics inside the Numbar dropdown include a `secondary` property in your remote JSON. There are two formats you can use:

<br/>

#### Option A: Plain List

Include a `secondary` property with an array of metrics:

```
{
  "primary": 948,
  "secondary": [
   "Average Sales - 1.69",
   "Funnel Completion - 70.20%"
  ]
}
```

<img src="http://i.imgur.com/6zYC6bg.png" alt="" width="365">

<br/>

#### Option B: Structured Rows

Structure your list in easy to read rows using the following output in the `secondary` property:

```
{
  "primary": 379,
  "secondary": [
    {
      "title": "New Users",
      "value": 364
    },
    {
      "title": "Active Users",
      "value": 12
    },
  ],
  "title": "MyStartup.com"
}
```

<img src="http://i.imgur.com/qkaIFGt.png" alt="" width="365">

Tip: You can change the title inside the dropdown from “Numbar” to a custom title (e.g. MyStartup.com) by including the `title` property in your JSON. See the example above.

  <br/><br/><br/>

## Security (Basic Auth)

You can secure your important metrics from the public by activating Basic Auth on your endpoint. Numbar will automatically detect and display a prompt to enter your username and password if authorization is required.

Be sure to select the "Remember" checkbox to securely save your password to the macOS Keychain. This will prevent the need to reenter your credentials in the future.

<img src="http://i.imgur.com/KEUUOuY.png" alt="" width="444">

  <br/><br/><br/>

## Headers

Numbar supports sending custom headers for each request to your endpoint. You can manage your headers inside the Numbar General Preferences. [List of HTTP header fields](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields)

<img src="http://i.imgur.com/8t8uT15.png" alt="" width="450">
