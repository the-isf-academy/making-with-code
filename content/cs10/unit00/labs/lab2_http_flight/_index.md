---
title: "3. HTTP Flight"
type: lab
# draft: true
---


# HTTP: How Computers Communicate

The Internet may be humanity's most profound invention. A global
network of computers talking to one another, making it possible for people all
over the world to interact. In this lab, we will start learning about *how*
computers talk with one another. 

{{< aside "FYI" >}}
**All actions on the Internet are composed of HTTP Requests.** 

 - Every time you access a website, it triggers a series of HTTP Requests depending on its complexity. 
 - Every time a client requests information from a server, the request is recorded along with the status code.

{{<expand "An Analogy to better understand HTTP Requests" >}}
It can be tricky to understand how HTTP functions because it’s difficult to examine what your browser is actually doing. (And perhaps also because we explained it using acronyms that may be new to you.) Let’s review what we learned by using an analogy that could be more familiar to you.

Imagine the internet is a town. You are a client and your address determines where you can be reached. Businesses in town, such as Codecademy.com, serve requests that are sent to them. The other houses are filled with other clients like you that are making requests and expecting responses from these businesses in town. This town also has a crazy fast mail service, an army of mail delivery staff that can travel on trains that move at the speed of light.

Suppose you want to read the morning newspaper. In order to retrieve it, you write down what you need in a language called HTTP and ask your local mail delivery staff agent to retrieve it from a specific business. The mail delivery person agrees and builds a railroad track (connection) between your house and the business nearly instantly, and rides the train car labeled “TCP” to the address of the business you provided.

Upon arriving at the business, she asks the first of several free employees ready to fulfill the request. The employee searches for the page of the newspaper that you requested but cannot find it and communicates that back to the mail delivery person.

The mail delivery person returns on the light speed train, ripping up the tracks on the way back, and tells you that there was a problem “404 Not Found.” After you check the spelling of what you had written, you realize that you misspelled the newspaper title. You correct it and provide the corrected title to the mail delivery person.

This time the mail delivery person is able to retrieve it from the business. You can now read your newspaper in peace until you decide you want to read the next page, at which point, you would make another request and give it to the mail delivery person.

*Source: [https://www.codecademy.com/articles/http-requests](https://www.codecademy.com/articles/http-requests)*

{{< /expand >}}

{{< /aside >}}

#### New Vocabulary

- **HTTP** stands for "**Hypertext Transfer Protocol**." It's a set of rules for how
  computers ask each other for content, and how they reply. 
- **JSON** stands for **JavaScript Object Notation**. It is the standard file format for exchanging data over the internet. The syntax mimics dictionaries by using `key` and `value` pairs. 
- **API** stands for **Application Programming Interface**. It is software that allows computers to communicate with each other. An `API` often provides `JSON`. 

---


## [0] HTTP GET

Every time you visit a URL, your computer opens a connection with the server at that address and uses **HTTP** to send and recieve the content. 

---

### GET Request

Communication starts when one computer (the client) sends a *request* to another computer (the server). For example, by visiting "cs.fablearn.org" you initiate
a `GET` request to recieve the *Making with Code* homepage from the server. 

A `GET` request contains following: 
{{< figure src="images/courses/cs10/unit00/lab1_http_0.png" width="50%" alt-text="An HTTP GET request" >}}

---

### GET Response

Once the request has been recieved by the server, it responds by sending the client a HTTP *response*. If a successful connection has been made, the server sends the content to the client. 

Here's an example of a HTTP response to a successful `GET` request to the course website:

  ```shell {linenos=table}
  HTTP/1.1 200 OK                                 // This is the response
  Content-Length: 2081                            // I am sending a lot
  Content-Type: text/html                         // I am sending HTML
  Date: Tue, 18 Aug 2020 19:23:28 GMT             // This is when I sent it
  Last-Modified: Tue, 18 Aug 2020 15:46:28 GMT    // There is new content
  
  <!DOCTYPE html>                                 // Here it comes!
  <html lang="en">                                // Here is your webpage
      . . . 
  <p><em>Making with Code</em> is a new, old 
  approach to teaching computer science 
  based in Constructionism.</p>
      . . .
  ```
- `200` (line 1) is the response status code. 
- `Content-Length` (line 2), `Content-Type`(line 3), `Date`(line 4), and `Last-Modified`(line 5) are response headers. They provide
  more detail about what is being requested and what is being sent back. For example, the `Content-Type` tells your computer what
  type of data is being recieved. For "cs.fablearn.org", your computer recieves the HTML, Javacsript, CSS, and image files that make
  up the homepage of the site. 
- `<!DOCTYPE html>` (line 7) is the beginning of the content sent with the response. This is the HTML of the course website which your
  browser then renders as a webpage.



---

### Status Codes
Status codes are used to signal how the communication between the client and the server is going.

**Common HTTP Status Codes**
- `200` means success.
- `300` means you're looking in the wrong place
- `304` means there's no new content since you last came to this page
- `400` means you did something wrong.
- `404` means the resource requested could not be found 
- `500` means, "Sorry, the server broke!" 

---

### Using HTTPIE


{{< checkpoint >}}

{{< write-action >}}**Complete the section, `the-isf-academy.github.io/making-with-code`, of the worksheet.** You will need to:
- Right click and click "Inspect"
- Select "Network" from the top toolbar in the developer tools
- Hard refresh the page with "Command + Shift + R"


{{< /checkpoint >}}

--- 

## [2] API: DATA.GOV.HK


{{< figure src="https://data.gov.hk/assets/shared/img/facebook_og-image.jpg" width="100%" alt-text="An HTTP GET request" width=25% >}}

**[DATA.GOV.HK](https://data.gov.hk/en/) hosts open data provided by the Hong Kong government.** It provides an open `APIs` that allows anyone to access their databases. We are going to use `HTTP Requests` to access this database. 

`API` stands for **Application Programming Interface**. It is software that allows computers to communicate with each other. An `API` often provides `JSON`. 

✈️ **In this lab, we will look at the data for the HK International Airport**

{{< figure src="https://experience.hongkongairport.com/images/grid-totem.jpg" width="100%" alt-text="An HTTP GET request" width=50% >}}

---

### JSON

**JSON** stands for **JavaScript Object Notation**. It is the standard file format for exchanging data over the internet. The syntax mimics dictionaries by using `key` and `value` pairs. 

{{< look-action >}} **For example, this is `JSON` for the HK International Airport.** What is the JSON describing? 
```shell
[
  {
    "date": "2025-08-01",
    "arrival": true,
    "cargo": true,
    "list": [
      {
        "time": "00:00",
        "flight": [
          {
            "no": "ET 3684",
            "airline": "ETH"
          }
        ],
        "status": "Cancelled",
        "statusCode": null,
        "origin": [
          "LGG",
          "KGF"
        ]
      },
      ...
  }
]
```
> Notice how it looks exactly like a dictionary with `key` and `value` pairs. 

---

### Making HTTP Requests

This lab will require you to make a series of `http requests` to the HKO API. 


{{< code-action "Go to" >}} [httpie.io/app](https://httpie.io/app). You will use this web app to send HTTP requests. 

{{< code-action >}}**Make a simple  `http get` request to recieve `JSON` from DATA.GOV.HK.**

{{< figure src="images/courses/cs10/unit00/lab1_http_1.png" width="100%" alt-text="An HTTP GET request" >}}
> - `GET` - tells the app you are making a `get` request 
> - `https://www.hongkongairport.com/flightinfo-rest/rest/flights/past` - tells the app which address you'd like to make the request to
> - `date: 2025-08-01` - tells the date you want is August 1st, 2025


{{< checkpoint >}}

💻 **Open the flight API documentation from DATA.GOV.HK: [API Documentation](https://www.hongkongairport.com/iwov-resources/misc/opendata/Flight_Information_DataSpec_en.pdf).** You will need to utilize this resource complete the worksheet. 


✏️ **Complete the section, `1. DATA.GOV.HK API`, of the worksheet to further explore `http requests`, `JSON`, and `APIs`.**


{{< /checkpoint >}}

---


## [3] Deliverables


{{< deliverables >}}  

**Once you've successfully completed the worksheet be sure to fill out [this Google form](https://docs.google.com/forms/d/e/1FAIpQLSfx0vcRky-7Wd0W1_0lIBbmhpru3s3By9-2ULRDdNqQKYvEjw/viewform?usp=sf_link).**

{{< /deliverables >}}

---

## [4] Extension
    

Now that you've had succifient practice accessing APIs, it's time to explore what type of APIs exist. 

{{< code-action "Explore an API of your choosing." >}} You may want to use the `httpie` Terminal commands. Here are some suggestions of APIs to explore:
- [Joke API](https://sv443.net/jokeapi/v2/)
- [ZenQuotes API](https://premium.zenquotes.io/zenquotes-documentation/)
- [Wikipedia API](https://www.mediawiki.org/wiki/API:Main_page) 
- [List of Public APIs](https://github.com/public-apis/public-apis)
  - We suggest only trying those with no Auth `apikey` requirement


<!-- 
### [ISF Energy Database]

The ISF Energy Database keep historical and current data about the school's energy usage. This includes tracking how many kilowatt hours were used over a period of time and the amount of money spent. This data is tracked by sensors placed all around the school.


{{< figure src="images/courses/cs10/unit00/isf_energy_sensors_00.png" width="100%" alt-text="An HTTP GET request" >}}

This API requires an authroization access token. As such, we will use an online service to make API requests easier than using the Terminal. 

{{< code-action >}} **To start, you will need to join our cs10 team on Postman via this [LINK](https://app.getpostman.com/join-team?invite_code=f4474c23d3b0d727b50c57a0c4ed6bd1&target_code=e00a10c981618d9db374041d68a577f1).** Simply sign in with your ISF Google account to get join. 

{{< code-action >}} **Once you've joined, click on `isf energy database` to see the details of the API.**
{{< figure src="images/courses/cs10/unit00/isf_energy_sensors_01.png" width="100%" alt-text="An HTTP GET request" >}}

{{< code-action >}} **You will first need to generate an `access_token` from the `POST Get Access Token` route and copy it.** We will learn more about `http POST` requests and routes in the next lab.
{{< figure src="images/courses/cs10/unit00/isf_energy_sensors_02.png" width="100%" alt-text="An HTTP GET request" >}}


{{< code-action >}} **You can then explore the 3 `GET` requests available. For each one, you will need to paste in the `access_token`.** To paste in the token:
> 0) Select a `GET` request
> 1) Select `Headers`
> 2) Paste in the `access_token`, replacing the old access token
{{< figure src="images/courses/cs10/unit00/isf_energy_sensors_03.png" width="100%" alt-text="An HTTP GET request" >}}



{{< code-action >}} **You can then `Send` the request to recieve the `JSON`.**
> 0) Select `Params`
> 1) Change any of the paramters under `Value` to your desired request. You may want to open the `Description` to learn more. 
{{< figure src="images/courses/cs10/unit00/isf_energy_sensors_04.png" width="100%" alt-text="An HTTP GET request" >}}

{{< code-action >}} **The `JSON` will appear below in the `Body`.** Feel free to experiment with the different display settings such as `Raw`.

{{< figure src="images/courses/cs10/unit00/isf_energy_sensors_05.png" width="75%" alt-text="An HTTP GET request" >}}

--- -->
