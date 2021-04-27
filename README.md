<!--
Copyright 2018 Adobe. All rights reserved.
This file is licensed to you under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License. You may obtain a copy
of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under
the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR REPRESENTATIONS
OF ANY KIND, either express or implied. See the License for the specific language
governing permissions and limitations under the License.
-->

[![Version](https://img.shields.io/npm/v/@adobe/aio-lib-target.svg)](https://npmjs.org/package/@adobe/aio-lib-target)
[![Downloads/week](https://img.shields.io/npm/dw/@adobe/aio-lib-target.svg)](https://npmjs.org/package/@adobe/aio-lib-target)
![Node.js CI](https://github.com/adobe/aio-lib-target/workflows/Node.js%20CI/badge.svg)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Codecov Coverage](https://img.shields.io/codecov/c/github/adobe/aio-lib-target/master.svg?style=flat-square)](https://codecov.io/gh/adobe/aio-lib-target/)

# I/O Adobe Target SDK
Node Javascript Core SDK wrapping [Adobe Target APIs](https://developers.adobetarget.com/api/).


### Installing

```bash
$ npm install
```

### Target API Technical Requirements

The Adobe Target 1.0 APIs need to set an `Accepts` header for them to work properly. With version `2.x` or greater of this SDK, we set the proper `Accepts` header for the calls as [documented](https://developers.adobetarget.com/api/). Previous versions of this SDK may or may not work since for some Target API calls the `Accepts` header is not enforced consistently.

### User-based OAuth Tokens and Role Requirements

For scenarios in which user-based OAuth tokens are used instead of a JWT technical account ones, the user may require specific roles/permissions to be assigned in Adobe Target in order to successfully perform API calls.
Otherwise, the Adobe Target API calls performed by the API Client will result in 500 errors.

For more detailed information, please read the [Adobe Target Enterprise user permissions documentation](https://docs.adobe.com/content/help/en/target/using/administer/manage-users/enterprise/property-channel.html).

### Usage
1) Initialize the SDK

```
var sdk = require('@adobe/aio-lib-target')

async function sdkTest() {
  //initialize sdk
  const targetClient = await sdk.init('<tenant>', 'x-api-key', '<valid auth token>')
}
```
Init method returns an Instance of Class [<code>TargetCoreAPI</code>](#TargetCoreAPI)

2) Call methods using initialized sdk

```
var sdk = require('@adobe/aio-lib-target')

async function sdkTest() {
    //initialize sdk
    const targetClient = await sdk.init('<tenant>', 'x-api-key', '<valid auth token>')

    //get activities
    const activities = await targetClient.getActivities({limit:5, offset:0})
    console.log(util.inspect(activities));

    //get offers
    const offers = await targetClient.getOffers({limit:5, offset:0})
    console.log(util.inspect(offers));

     //get offer by id activity
     const offer = await targetClient.getOfferById(123)
     console.log(util.inspect(offer));
}
```
All Methods available under sdk are documented [<code>here</code>](#TargetCoreAPI)

## Classes

<dl>
<dt><a href="#TargetCoreAPI">TargetCoreAPI</a></dt>
<dd><p>This class provides methods to call Adobe Target APIs.
Before calling any method initialize the instance by calling init method on it
with valid tenant, apiKey and auth token</p>
</dd>
</dl>

## Functions

<dl>
<dt><a href="#init">init(tenant, apiKey, token)</a> ⇒ <code><a href="#TargetCoreAPI">Promise.&lt;TargetCoreAPI&gt;</a></code></dt>
<dd><p>Returns a Promise that resolves with a new TargetCoreAPI object.</p>
</dd>
</dl>

<a name="TargetCoreAPI"></a>

## TargetCoreAPI
This class provides methods to call Adobe Target APIs.
Before calling any method initialize the instance by calling init method on it
with valid tenant, apiKey and auth token

**Kind**: global class  

* [TargetCoreAPI](#TargetCoreAPI)
    * [.init(tenant, apiKey, token)](#TargetCoreAPI+init) ⇒ [<code>TargetCoreAPI</code>](#TargetCoreAPI)
    * [.getActivities([options])](#TargetCoreAPI+getActivities) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.createABActivity(body, [options])](#TargetCoreAPI+createABActivity) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.createXTActivity(body, [options])](#TargetCoreAPI+createXTActivity) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getABActivityById(id, [options])](#TargetCoreAPI+getABActivityById) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getXTActivityById(id, [options])](#TargetCoreAPI+getXTActivityById) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.updateABActivity(id, body, [options])](#TargetCoreAPI+updateABActivity) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.updateXTActivity(id, body, [options])](#TargetCoreAPI+updateXTActivity) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.setActivityName(id, name, [options])](#TargetCoreAPI+setActivityName) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.setActivityState(id, state, [options])](#TargetCoreAPI+setActivityState) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.setActivityPriority(id, priority, [options])](#TargetCoreAPI+setActivityPriority) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.setActivitySchedule(id, schedule, [options])](#TargetCoreAPI+setActivitySchedule) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.deleteABActivity(id, [options])](#TargetCoreAPI+deleteABActivity) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.deleteXTActivity(id, [options])](#TargetCoreAPI+deleteXTActivity) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getActivityChangeLog(id, [options])](#TargetCoreAPI+getActivityChangeLog) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getOffers([options])](#TargetCoreAPI+getOffers) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getOfferById(id, [options])](#TargetCoreAPI+getOfferById) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.createOffer(body, [options])](#TargetCoreAPI+createOffer) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.updateOffer(id, body, [options])](#TargetCoreAPI+updateOffer) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.deleteOffer(id, [options])](#TargetCoreAPI+deleteOffer) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getAudiences([options])](#TargetCoreAPI+getAudiences) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.createAudience(body, [options])](#TargetCoreAPI+createAudience) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getAudienceById(id, [options])](#TargetCoreAPI+getAudienceById) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.updateAudience(id, body, [options])](#TargetCoreAPI+updateAudience) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.deleteAudience(id, [options])](#TargetCoreAPI+deleteAudience) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getProperties([options])](#TargetCoreAPI+getProperties) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getPropertyById(id, [options])](#TargetCoreAPI+getPropertyById) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getMBoxes([options])](#TargetCoreAPI+getMBoxes) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getMBoxByName(name, [options])](#TargetCoreAPI+getMBoxByName) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getMBoxProfileAttributes([options])](#TargetCoreAPI+getMBoxProfileAttributes) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getEnvironments([options])](#TargetCoreAPI+getEnvironments) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getABActivityPerformance(id, [options])](#TargetCoreAPI+getABActivityPerformance) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getXTActivityPerformance(id, [options])](#TargetCoreAPI+getXTActivityPerformance) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getActivityPerformance(id, [options])](#TargetCoreAPI+getActivityPerformance) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.getOrdersReport(id, [options])](#TargetCoreAPI+getOrdersReport) ⇒ <code>Promise.&lt;Response&gt;</code>
    * [.executeBatch(body)](#TargetCoreAPI+executeBatch) ⇒ <code>Promise.&lt;Response&gt;</code>

<a name="TargetCoreAPI+init"></a>

### targetCoreAPI.init(tenant, apiKey, token) ⇒ [<code>TargetCoreAPI</code>](#TargetCoreAPI)
Initialize sdk.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: [<code>TargetCoreAPI</code>](#TargetCoreAPI) - a TargetCoreAPI instance  

| Param | Type | Description |
| --- | --- | --- |
| tenant | <code>string</code> | Adobe Target tenant name |
| apiKey | <code>string</code> | Your api key |
| token | <code>string</code> | Valid auth token |

<a name="TargetCoreAPI+getActivities"></a>

### targetCoreAPI.getActivities([options]) ⇒ <code>Promise.&lt;Response&gt;</code>
List activities.
Get a list of activities created in your Target account, with the ability to filter and sort by attributes.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| [options] | <code>object</code> |  | to control activity search |
| [options.limit] | <code>number</code> | <code>2147483647</code> | Defines the number of items to return |
| [options.offset] | <code>number</code> | <code>0</code> | Defines the first activity to return from the list of total activities. Used in conjunction with limit, you can provide pagination in your application for users to browse through a large set of activities. |
| [options.sortBy] | <code>string</code> |  | Defines the sorting criteria on the returned items |
| [options.headers] | <code>object</code> |  | headers to pass to API call |

<a name="TargetCoreAPI+createABActivity"></a>

### targetCoreAPI.createABActivity(body, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Create AB Activity.
Creates a new AB activity with the specified contents and returns the created activity.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| body | <code>object</code> | Activity JSON. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+createXTActivity"></a>

### targetCoreAPI.createXTActivity(body, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Create XT Activity.
Creates a new XT activity with the specified contents and returns the created activity.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| body | <code>object</code> | Activity JSON. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getABActivityById"></a>

### targetCoreAPI.getABActivityById(id, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Get AB activity.
Fetch the current definition of an AB activity if it is found as referenced by the id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getXTActivityById"></a>

### targetCoreAPI.getXTActivityById(id, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Get XT activity.
Fetch the current definition of XT activity if it is found as referenced by the id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+updateABActivity"></a>

### targetCoreAPI.updateABActivity(id, body, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Update AB activity.
Updates the AB activity definition with the contents as provided in the request. This can change the state and behaviour of an existing activity.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| body | <code>object</code> | activity JSON |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+updateXTActivity"></a>

### targetCoreAPI.updateXTActivity(id, body, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Update XT activity.
Update the current definition of XT activity if it is found as referenced by the id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| body | <code>object</code> | activity JSON |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+setActivityName"></a>

### targetCoreAPI.setActivityName(id, name, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Update activity name.
Updates the name of the AB activity that is referenced by the supplied id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| name | <code>string</code> | New Activity name. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+setActivityState"></a>

### targetCoreAPI.setActivityState(id, state, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Update Activity state.
Update state of an activity if it is found as referenced by the id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| state | <code>string</code> | New Activity state. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+setActivityPriority"></a>

### targetCoreAPI.setActivityPriority(id, priority, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Update Activity priority.
Update priority of an activity if it is found as referenced by the id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| priority | <code>string</code> | New Activity priority. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+setActivitySchedule"></a>

### targetCoreAPI.setActivitySchedule(id, schedule, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Update Activity schedule.
Update schedule of an activity if it is found as referenced by the id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| schedule | <code>string</code> | New Activity schedule. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+deleteABActivity"></a>

### targetCoreAPI.deleteABActivity(id, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Delete AB activity.
Deletes the AB activity that is referenced by the id, if it is found.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+deleteXTActivity"></a>

### targetCoreAPI.deleteXTActivity(id, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Delete XT activity.
Delete the current definition of an XT activity if it is found as referenced by the id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getActivityChangeLog"></a>

### targetCoreAPI.getActivityChangeLog(id, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Get Activity changelog.
Returns the changelog for a given activity id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getOffers"></a>

### targetCoreAPI.getOffers([options]) ⇒ <code>Promise.&lt;Response&gt;</code>
List Offers.
Retrieve the list of previously-created content offers. The parameters passed through the query string are optional and are used to indicate the sorting and filtering options.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| [options] | <code>object</code> |  | to control offer search. |
| [options.limit] | <code>number</code> | <code>2147483647</code> | Defines the number of items to return |
| [options.offset] | <code>number</code> | <code>0</code> | Defines the first offers to return from the list of Offers. Used in conjunction with limit, you can provide pagination in your application for users to browse through a large set of offers. |
| [options.sortBy] | <code>string</code> |  | Defines the sorting criteria on the returned items. |
| [options.headers] | <code>object</code> |  | headers to pass to API call |

<a name="TargetCoreAPI+getOfferById"></a>

### targetCoreAPI.getOfferById(id, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Get Offer.
Retrieves the contents of an offer given an offer id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Offer id. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+createOffer"></a>

### targetCoreAPI.createOffer(body, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Create Offer.
Creates a new content offer as defined by the request data.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| body | <code>object</code> | Offer JSON. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+updateOffer"></a>

### targetCoreAPI.updateOffer(id, body, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Update Offer.
Updates the content offer referenced by the id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Offer id. |
| body | <code>object</code> | Offer JSON |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+deleteOffer"></a>

### targetCoreAPI.deleteOffer(id, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Delete Offer.
Deletes the content offer referenced by the provided id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Offer id. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getAudiences"></a>

### targetCoreAPI.getAudiences([options]) ⇒ <code>Promise.&lt;Response&gt;</code>
List Audiences.
List all available audiences with options to filter and sort by each available field.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| [options] | <code>object</code> |  | options to control audience search. |
| [options.limit] | <code>number</code> | <code>2147483647</code> | Defines the number of items to return. Default value is 2147483647 |
| [options.offset] | <code>number</code> | <code>0</code> | Defines the first audience to return from the list of total offers. Used in conjunction with limit, you can provide pagination in your application for users to browse through a large set of offers. |
| [options.sortBy] | <code>string</code> |  | Defines the sorting criteria on the returned items. |
| [options.headers] | <code>object</code> |  | headers to pass to API call |

<a name="TargetCoreAPI+createAudience"></a>

### targetCoreAPI.createAudience(body, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Create Audience.
Create a new audience as specified by the contents of the request and return the newly-created audience definition.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| body | <code>object</code> | Audience JSON. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getAudienceById"></a>

### targetCoreAPI.getAudienceById(id, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Get Audience.
Get the audience definition specified by the provided id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Audience id. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+updateAudience"></a>

### targetCoreAPI.updateAudience(id, body, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Update Audience.
Update an audience with the new rules specified by the request data.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Audience id. |
| body | <code>object</code> | audience JSON |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+deleteAudience"></a>

### targetCoreAPI.deleteAudience(id, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Delete Audience.
Delete the audience referenced by the specified id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Audience id. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getProperties"></a>

### targetCoreAPI.getProperties([options]) ⇒ <code>Promise.&lt;Response&gt;</code>
List Properties.
Get a list of properties.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getPropertyById"></a>

### targetCoreAPI.getPropertyById(id, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Get Property.
Retrieve property by property Id..

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Property id. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getMBoxes"></a>

### targetCoreAPI.getMBoxes([options]) ⇒ <code>Promise.&lt;Response&gt;</code>
List MBoxes.
List all available mboxes for a specific client with the options to filter and sort.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getMBoxByName"></a>

### targetCoreAPI.getMBoxByName(name, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Get MBox by name.
Get the list of mbox parameters.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| name | <code>string</code> | MBox name. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getMBoxProfileAttributes"></a>

### targetCoreAPI.getMBoxProfileAttributes([options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Get Profile Attributes.
Retrieve the list of available profile attributes and mbox parameters of type profile.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getEnvironments"></a>

### targetCoreAPI.getEnvironments([options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Get Environments.
List all available environments with the options to filter and sort. Use the Environments API to retrieve the environment IDs corresponding to the various host groups set for the client.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getABActivityPerformance"></a>

### targetCoreAPI.getABActivityPerformance(id, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Get AB activity performance.
Retrieve property by property Id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getXTActivityPerformance"></a>

### targetCoreAPI.getXTActivityPerformance(id, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Get activity performance.
Retrieve property by property Id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getActivityPerformance"></a>

### targetCoreAPI.getActivityPerformance(id, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Get activity performance.
Retrieve the performance report data for the Automated Personalization activity referenced by the provided id.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+getOrdersReport"></a>

### targetCoreAPI.getOrdersReport(id, [options]) ⇒ <code>Promise.&lt;Response&gt;</code>
Get Orders report.
Retrieve the orders/audit report data for an AB, XT or Autotmated Personalization Activity.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>number</code> | Activity id. |
| [options] | <code>object</code> | sdk options |
| [options.headers] | <code>object</code> | headers to pass to API call |

<a name="TargetCoreAPI+executeBatch"></a>

### targetCoreAPI.executeBatch(body) ⇒ <code>Promise.&lt;Response&gt;</code>
Execute Batch APIs.
Multiple Admin APIs can be executed as a single batch request.

**Kind**: instance method of [<code>TargetCoreAPI</code>](#TargetCoreAPI)  
**Returns**: <code>Promise.&lt;Response&gt;</code> - a Promise resolving to a Response  

| Param | Type | Description |
| --- | --- | --- |
| body | <code>object</code> | json to execute batch |

<a name="init"></a>

## init(tenant, apiKey, token) ⇒ [<code>Promise.&lt;TargetCoreAPI&gt;</code>](#TargetCoreAPI)
Returns a Promise that resolves with a new TargetCoreAPI object.

**Kind**: global function  
**Returns**: [<code>Promise.&lt;TargetCoreAPI&gt;</code>](#TargetCoreAPI) - Promise resolving to a TargetCoreAPI instance  

| Param | Type | Description |
| --- | --- | --- |
| tenant | <code>string</code> | tenant Adobe Target tenant name |
| apiKey | <code>string</code> | apiKey Your api key |
| token | <code>string</code> | Valid auth token |

### Debug Logs

LOG_LEVEL=debug  <your_call_here>

### Contributing

Contributions are welcome! Read the [Contributing Guide](./.github/CONTRIBUTING.md) for more information.

### Licensing

This project is licensed under the Apache V2 License. See [LICENSE](LICENSE) for more information.
