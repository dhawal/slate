---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='http://www.adsnative.com' target="_blank">AdsNative Hompepage</a>
  - <a target="_blank" href="mailto:contact@adsnative.com">Developer Support</a>
  
includes:
  - errors

search: true
---

# Introduction

Welcome to the AdsNative API! You can use our API to access AdsNative ads API endpoints.

You can view code examples in the dark area to the right.

## Basics

### Base URL

The base URL for all the API endpoints is given below

`http://api.adsnative.com/v1/`

### HTTPS / SSL

Just make an https:// call instead of http:// and you're all set.

### JSON & JSONP Response Format

v1 only supports a single format, JSON. JSONP is also officially supported, just add a callback parameter to your request and the response will be encapsulated in the value you specified.

### Request Rate Limiting

We do not currently enforce a rate limit

# Native Ad

List a single ad unit for an ad-zone placement on your website.  

### HTTP Request

`GET /ad.json`

> Example Request

```shell
curl "http://api.adsnative.com/v1/ad.json?zid=ping"
```
> Example Response

```json
{
  "ad": {
      "backgroundColor": "#fefff2",
      "brandImageUrl": "http://dev-www.adsnative.com/media/brand_images/1/82cc86ad-9070-4b90-9006-1fbca6697694.jpg",
      "embedUrl": "http://api.adsnative.com/v1/creative.html?crid=xyz&sid=sid123",
      "imageSrc": "http://files-www2.adsnative.com/media/1/xyz.jpg",
      "promotedBy": "Tesla",
      "promotedByTag": "Promoted by",
      "promotedByUrl": "http://api.adsnative.com/v1/ad.click?u=http%3A%2F%2Fxyz.com%2F&sid=sid123",
      "summary": "Tesla teased electric motorheads earlier this week by announcing an event that would show off its curious battery swapping system...",
      "target": "_parent",
      "title": "Tesla Shows Off A 90-Second Battery Swap System, Wants It At Supercharging Stations By Year's End",
      "trackingTags": "",
      "type": "story",
      "url": "http://api.adsnative.com/v1/ad.click?u=http%3A%2F%2Fxyz.com%2F&sid=sid123"
  },
  "cid": "cid123",
  "count": 1,
  "crid": "crid123",
  "sid": "sid123",
  "status": "OK",
  "uuid": "uuid123",
  "zid": "ping"
}
```

### Optional Query Parameters

Parameter | Description
--------- | -----------
zid | This is the ad placement token that can be found in your dashboard

### Required Query Parameters

Parameter | Description
--------- | -----------
ip | client's ipaddress to be used for city, region or country targeting 
ua | client's user agent 
al | client's accept-language settings (e.g. 'en-us') to be used for language specific targeting 
uuid | client's unique identifier to be used for frequency capping. AdsNative will attempt to set a uuid value in a cookie if parameter is not passed. 
kw | keyword targeting 
cat | category targeting

### Response

Parameter | Description
--------- | -----------
status | The status of the ad response. Returns 'OK' when a valid ad is present. 
count | Number of native ads returned.  
type | content type of the native ad. It's either 'story' or 'video'.  
title | title of the native ad. 
summary | summary part of the native ad.  
imageSrc | URL of the image attached with native ad. 
embedUrl | Returns the IFRAME embed code of a video player, in case the 'type' of the ad is 'video'. This embed code video works on all platforms. For native, platforms it need to be wrapped in a Web View.  
url | click URL for the whole native ad.  
target | after click action for the native ad. If it's '_blank', it should be opened in new window/view. If it's '_parent' or empty, it should be opened in the same window/view.  
backgroundColor | Background color value set in Adsnative Dashboard for the ad unit. This allows you to control the background color of the ad unit from AdsNative Dashboard. You can choose to ignore this value 
brandImageUrl | URL of the brand image/logo.  
promotedBy | Name of the brand promoting the content.  
promotedByTag | Prefix for the brand name configured in AdsNative Dashboard for the current ad unit. For e.g. 'Promoted by' or 'Sponsored by'.  
promotedByUrl | click URL that needs to be called in case user clicks on either brand name or brand image.  
trackingTags | tags for tracking impression and third-party tracking. These are typically image or script tags that can droppped anywhere in the web page or in case of native platforms, within a 1x1 Web View. If you are looking for an alternative method for your platform, please contact AdsNative team for more options.

# Native Ad with Formatted HTML

Ad JSON call to get formatted html to render native ad

### HTTP Request

`GET /ad-template.json`

> Example Request

```shell
curl "http://api.adsnative.com/v1/ad-template.json?zid=ping"
```
> Example Response

```json
{
  "ad": {
      "backgroundColor": "#fefff2",
      "brandImageUrl": "http://dev-www.adsnative.com/media/brand_images/1/82cc86ad-9070-4b90-9006-1fbca6697694.jpg",
      "embedUrl": "http://api.adsnative.com/v1/creative.html?crid=xyz&sid=sid123",
      "imageSrc": "http://files-www2.adsnative.com/media/1/xyz.jpg",
      "promotedBy": "Tesla",
      "promotedByTag": "Promoted by",
      "promotedByUrl": "http://api.adsnative.com/v1/ad.click?u=http%3A%2F%2Fxyz.com%2F&sid=sid123",
      "summary": "Tesla teased electric motorheads earlier this week by announcing an event that would show off its curious battery swapping system...",
      "target": "_parent",
      "title": "Tesla Shows Off A 90-Second Battery Swap System, Wants It At Supercharging Stations By Year's End",
      "trackingTags": "",
      "type": "story",
      "url": "http://api.adsnative.com/v1/ad.click?u=http%3A%2F%2Fxyz.com%2F&sid=sid123"
  },
  "cid": "cid123",
  "count": 1,
  "crid": "crid123",
  "sid": "sid123",
  "status": "OK",
  "uuid": "uuid123",
  "zid": "ping"
}
```

### Optional Query Parameters

Parameter | Description
--------- | -----------
zid | This is the ad placement token that can be found in your dashboard

### Required Query Parameters

Parameter | Description
--------- | -----------
ip | client's ipaddress to be used for city, region or country targeting 
ua | client's user agent 
al | client's accept-language settings (e.g. 'en-us') to be used for language specific targeting 
uuid | client's unique identifier to be used for frequency capping. AdsNative will attempt to set a uuid value in a cookie if parameter is not passed. 
kw | keyword targeting 
cat | category targeting

### Response

Parameter | Description
--------- | -----------
status | The status of the ad response. Returns 'OK' when a valid ad is present. 
count | Number of native ads returned.  
type | content type of the native ad. It's either 'story' or 'video'.  
title | title of the native ad. 
summary | summary part of the native ad.  
imageSrc | URL of the image attached with native ad. 
embedUrl | Returns the IFRAME embed code of a video player, in case the 'type' of the ad is 'video'. This embed code video works on all platforms. For native, platforms it need to be wrapped in a Web View.  
url | click URL for the whole native ad.  
target | after click action for the native ad. If it's '_blank', it should be opened in new window/view. If it's '_parent' or empty, it should be opened in the same window/view.  
backgroundColor | Background color value set in Adsnative Dashboard for the ad unit. This allows you to control the background color of the ad unit from AdsNative Dashboard. You can choose to ignore this value 
brandImageUrl | URL of the brand image/logo.  
promotedBy | Name of the brand promoting the content.  
promotedByTag | Prefix for the brand name configured in AdsNative Dashboard for the current ad unit. For e.g. 'Promoted by' or 'Sponsored by'.  
promotedByUrl | click URL that needs to be called in case user clicks on either brand name or brand image.  
trackingTags | tags for tracking impression and third-party tracking. These are typically image or script tags that can droppped anywhere in the web page or in case of native platforms, within a 1x1 Web View. If you are looking for an alternative method for your platform, please contact AdsNative team for more options.
