[<img src="http://i.imgur.com/LsDRVD9.png" alt="" width="155">](https://numbarapp.com)

# Numbar Documentation

Keep an eye on your most important metric. Numbar is a macOS app that displays _your_ most valued metrics in your menu bar. Learn how to get started in seconds using the instructions below.

[<img src="http://i.imgur.com/IKWWYdm.png" alt="" width="274">](https://numbarapp.com)
  
<img src="http://i.imgur.com/XvxejHE.png" alt="" width="590">

  <br/><br/><br/>


## Table of Contents

- [How it Works](#how-it-works)
- [Getting Started](#getting-started)
- [Dropdown](#dropdown)
- [Security (Basic Auth)](#security-basic-auth)
- [Headers](#headers)  

<br/><br/><br/>

## How it Works

<img src="http://i.imgur.com/bhGwcKI.png" alt="">

  <br/><br/><br/>

## Getting Started

Numbar is simply a client that reads JSON from a remote web page that you create. Below are the specific JSON properties that Numbar can receive to display your metrics in your menu bar. You can use whichever programming language you want, as long as it returns valid JSON to the page.

<br>

To begin, output a property called `primary` with a value or metric that is very important to you. The `primary` value is what you'll see in your menu bar, so this should be a value that often changes and is of high interest to you. 

For example, you could output your business' daily revenue, or count the number of today’s new users from your database.

```json
{
  "primary": "$123.42"
}
```

<img src="http://i.imgur.com/7tO6Mxm.png" alt="" width="421">

Next, make this JSON publically available online and accessible from a URL. You'll want to visit your JSON URL to verify your important metric is displaying correctly. (Note: You can always secure this endpoint using Basic Auth. [Learn More](#security-basic-auth))

Finally, copy the URL for your remote JSON page and paste it in the “Endpoint” setting inside of the Numbar app preferences:

<img src="http://i.imgur.com/zXGVgMO.png" alt="" width="462">

Numbar will now visit your endpoint every 30 seconds and check for any changes. If there is a change, the new value will reflect in your macOS menu bar.

Note: You can modify how often Numbar checks for changes inside the Numbar General Preferences.

  <br/><br/><br/>

## Dropdown

Displaying one important metric is great, but sometimes you need access to more data. You can extend your metrics using the Numbar dropdown.

To display more metrics inside the Numbar dropdown, include a `secondary` property in your remote JSON. There are two formats you can use:

<br/>

#### Option A: Plain List

Include a `secondary` property with an array of metrics:

```json
{
  "primary": 948,
  "secondary": [
   "Average Sales - 1.69",
   "Funnel Completion - 70.20%"
  ]
}
```

<img src="http://i.imgur.com/6zYC6bg.png" alt="" width="398">

<br/>

#### Option B: Structured Rows

Structure your list in easy to read rows using the following output in the `secondary` property:

```json
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

<img src="http://i.imgur.com/qkaIFGt.png" alt="" width="398">

<br/>

#### Dropdown Title

You can change the title inside the dropdown from “Numbar” to a custom title (e.g. MyStartup.com) by including the `title` property in your JSON. See the example above.

  <br/><br/><br/>

## Security (Basic Auth)

You can secure your important metrics from the public by activating Basic Auth on your endpoint. Numbar will automatically detect and display a prompt to enter your username and password if authorization is required.

Be sure to select the "Remember" checkbox to securely save your password to the macOS Keychain. This will prevent the need to reenter your credentials in the future.

<img src="http://i.imgur.com/KEUUOuY.png" alt="" width="536">

  <br/><br/><br/>

## Headers

Numbar supports sending custom headers for each request to your endpoint. You can manage your headers inside the Numbar General Preferences. [List of HTTP header fields](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields)

<img src="http://i.imgur.com/8t8uT15.png" alt="" width="494">
