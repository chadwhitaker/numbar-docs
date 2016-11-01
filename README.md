[![](http://i.imgur.com/iJQSL9a.png)](https://numbarapp.com)

# Numbar Documentation

Keep an eye on your most important metric. Numbar is a macOS app that reads remote JSON and displays your valued metrics in your menu bar.

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

To get started, output a property called `primary` with a value that is very important to you. For example, you could output your business’s daily revenue, or count the number of today’s new users from your database.

```
{
  "primary": "$123.42"
}
```

<img src="http://i.imgur.com/7tO6Mxm.png" alt="" width="421">

After your endpoint is online and displaying your one important metric, copy and paste the URL to the “Endpoint” setting inside the Numbar app preferences.

<img src="http://i.imgur.com/zXGVgMO.png" alt="" width="450">

Number will now ping your endpoint every 30 seconds and check for any change. If there is a change that new value will reflect in your menu bar. You can change the update interval inside the General Preferences.

  <br/><br/><br/>

## Dropdown

Want to list more data points? You can via the dropdown in Numbar. All you need to do is include a `secondary` property in your endpoint’s JSON. There are two formats you can use:

<br/>

#### Option A: Plain List

Include a `secondary` property with an array of values for as many data points as you wish:

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

You can structure your list in easy to read rows using the following output in your `secondary` property:

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

Note: You can change the title inside the dropdown from “Numbar” to a custom title (e.g. MyStartup.com) by including the title property (see above.)

  <br/><br/><br/>

## Security (Basic Auth)

You can secure your endpoint using Basic Auth. Numbar will automatically display a prompt to enter your username and password if authorization is required.

Be sure to select the checkbox to save your password to the macOS keychain. This will prevent the need to reenter you credentials in the future.

<img src="http://i.imgur.com/KEUUOuY.png" alt="" width="444">

  <br/><br/><br/>

## Headers

Numbar supports sending request headers for each request to your endpoint. You can manage your headers inside the General Preferences. [List of HTTP header fields](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields)

<img src="http://i.imgur.com/8t8uT15.png" alt="" width="450">
