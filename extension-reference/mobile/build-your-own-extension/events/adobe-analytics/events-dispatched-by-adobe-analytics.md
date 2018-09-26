# Events Dispatched by Adobe Analytics

## Analytics Response Content

This event is a response from the Analytics module to notify the result of the track calls or to return the analytics hits queue size.

This event will be generated by:

* If Analytics server returns a response content, the Analytics extension after the _com.adobe.eventSource.requestContent is processed_ and the hit is sent to the server.
* The Analytics extension as a response for the _GetQueueSize_ API requests.

### Event Details

| **Event Type** | **Event Source** | **Paired** |
| :--- | :--- | :--- |
| com.adobe.eventType.analytics | com.adobe.eventSource.responseContent | No |

### Data Payload Definition

Here is the definition of the key-value pairs in this event:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| analyticsserverresponse | String | Yes | The Analytics server response that is used for forwarding by the Audience Manager module. |
| queuesize | Long | Yes | The Analytics queue size value. |

### Event Data Example

#### Forwarding the Analytics Server Response

```javascript
{
    "analyticsserverresponse": "example response to be forwarded"
}
```

### Event Data Example

#### Analytics Queue Size

```javascript
{
    "queuesize": 42
}
```

## Analytics Response Identity

This event is a response from the Analytics module that contains the unique tracking identifier. This value might be null if the Identity module is enabled, and a valid MID was generated.

This event is generated as a paired response for the `getTrackingIdentifier` public API that creates an _com.adobe.eventType.analytics_ event type and a _com.adobe.eventSource.requestIdentity_ event source.

### Event Details

| **Event Type** | **Event Source** | **Paired** | **Paired Event** |
| :--- | :--- | :--- | :--- |
| com.adobe.eventType.analytics | com.adobe.eventSource.responseIdentity | Yes | [Analytics Request Identity](https://github.com/jiabingeng/sdk-v5-docs/tree/4fa90676b2b07605dcdc8301ab8acc3691271667/build-your-own-extension/events/link/to/the/eventpage/andsection/README.md) |

### Data Payload Definition

Here is the definition of the key-value pairs in this event:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| aid | String | No | The analytics tracking identifier value |

### Event Data Example

```javascript
{
    "aid" : "aidValue"
}
```
