[<img src="https://i.imgur.com/Ko0ULbt.png" alt="" width="155">](https://numbarapp.com)

# Numbar Documentation

Keep an eye on your most important metric. Numbar is a macOS app that displays _your_ metrics in the macOS menu bar. Get started in seconds using the instructions below.

[<img src="https://i.imgur.com/IKWWYdm.png" alt="" width="274">](https://numbarapp.com/download)
  
<img src="https://i.imgur.com/XvxejHE.png" alt="" width="590">

  <br/><br/><br/>


## Table of Contents

- [How it Works](#how-it-works)
- [Getting Started](#getting-started)
- [Dropdown](#dropdown)
- [Security (Basic Auth)](#security-basic-auth)
- [Headers](#headers)  

<br/><br/><br/>

## How it Works

<br/><br/>

<img src="https://i.imgur.com/dPcKicx.png" alt="">

  <br/>

## Getting Started

Numbar is a simple client that reads JSON on a remote web page that you've created. Below are the specific JSON properties that Numbar can receive for displaying values in your menu bar. You may use whichever programming language you want, as long as it outputs valid JSON.

<br>

To begin, output a property called `menubar` with a value or metric that is very important to you. The `menubar` value is what you'll see in your macOS menu bar, so this should be something that often changes and is important to you. 


```json
{
  "menubar": "$123.42"
}
```

<img src="http://i.imgur.com/7tO6Mxm.png" alt="" width="421">

Next, make this JSON accessible online via a URL. Then, copy that URL to the “Endpoint” setting inside of the Numbar app preferences:

<img src="http://i.imgur.com/zXGVgMO.png" alt="" width="462">

Numbar will now check your endpoint every 30 seconds for any changes. If there is a change, the new value will reflect in your menu bar.

Note: You can secure this endpoint using a password by enabling Basic Auth. [Learn More](#security-basic-auth)

  <br/><br/><br/>

## Dropdown

Displaying one important metric is great, but sometimes you need quick access to more. Numbar allows you to extend your metrics inside the Numbar dropdown.

To display a table of metrics inside the Numbar dropdown, include the `dropdown` property in your remote JSON. There are two formats you can use:

<br/>

#### Dropdown Option A: Plain List

Include a `dropdown` property with an array of metrics:

```json
{
  "menubar": 948,
  "dropdown": [
   "Average Sales - 1.69",
   "Funnel Completion - 70.20%"
  ]
}
```

<img src="http://i.imgur.com/6zYC6bg.png" alt="" width="398">

<br/>

#### Dropdown Option B: Structured Rows

Structure your list in easy to read rows using the `title`, `value` properties inside the `dropdown` array:

```json
{
  "menubar": 379,
  "dropdown": [
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

<img src="https://i.imgur.com/qkaIFGt.png" alt="" width="398">

<br/>

#### Dropdown Title

You can change the title inside the dropdown header from “Numbar” to any custom title (e.g. MyStartup.com). Just include the `title` property in your JSON. See the example above.

  <br/><br/><br/>

## Security (Basic Auth)

Secure your important metrics from the public by activating [Basic Auth](https://en.wikipedia.org/wiki/Basic_access_authentication) on your JSON endpoint. Numbar will automatically display a prompt to enter your username and password if authorization is required.

Be sure to select the "Remember" checkbox to save your password to the macOS Keychain. This will prevent the need to reenter your credentials in the future.

<img src="https://i.imgur.com/KEUUOuY.png" alt="" width="536">

  <br/><br/><br/>

## Headers

Numbar supports custom headers for each request to your endpoint. You can manage your headers inside the Numbar General Preferences. [List of HTTP header fields](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields)

<img src="https://i.imgur.com/8t8uT15.png" alt="" width="494">
