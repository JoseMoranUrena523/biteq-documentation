---
description: This page shows how to use Biteq.
---

# API Documentation

First things first, let’s add sats to your API wallet. Use this endpoint to create an invoice which you can pay to fund your API wallet for paying others!

{% swagger src=".gitbook/assets/openapi.json" path="/create-invoice" method="post" %}
[openapi.json](.gitbook/assets/openapi.json)
{% endswagger %}

Now you can copy your invoice, and pay it with your personal wallet! Once you have paid your invoice, you can check with Biteq to see if it reflected. Copy the `checkingId` you got earlier and make this request!

{% swagger src=".gitbook/assets/openapi (1).json" path="/check-invoice" method="get" %}
[openapi (1).json](<.gitbook/assets/openapi (1).json>)
{% endswagger %}

Another thing you can do is make an invoice on your personal wallet and pay it with the sats you have in the Biteq API. Let's try that method out!

{% swagger src=".gitbook/assets/openapi (1).json" path="/pay-invoice" method="post" %}
[openapi (1).json](<.gitbook/assets/openapi (1).json>)
{% endswagger %}

Now, let’s verify to see if a lightning address exists! This endpoint will not just return if it’s valid, but basic metadata and more info of the Lightning address, like ZEBEDEE. (thanks to fiatjaf for the endpoint)

{% swagger src=".gitbook/assets/jsononline-net.json" path="/check-address" method="get" %}
[jsononline-net.json](.gitbook/assets/jsononline-net.json)
{% endswagger %}

Next, let's pay to a lightning address! (useful for play-to earn games and/or GPT sites) Let's try this endpoint out!

{% swagger method="post" path="/pay-address" baseUrl="https://biteq.teqquu.com" summary="" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="amount" type="Integer" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="address" type="String" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" name="comment" type="String" %}
Defaults to "Payment from Biteq"
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="POST /pay-address" %}
```json
{
    "success_action": {
        "tag": "string",
        "message": "string"
    },
    "payment_hash": "string",
    "checking_id": "string"
}
```
{% endswagger-response %}
{% endswagger %}

I should have covered this a while ago, but you can also check your balance before you try paying or stuff to make sure you don’t get any errors. Let’s try that out!

{% swagger method="get" path="/balance" baseUrl="https://biteq.teqquu.com" summary="" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="GET /balance" %}
```json
{
  "amount": "integer"
}
```
{% endswagger-response %}
{% endswagger %}

There will be more endpoints soon, but remember, Biteq is in beta-testing and we will continue adding endpoints for you.
