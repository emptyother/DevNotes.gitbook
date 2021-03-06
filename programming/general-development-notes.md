---
description: Anything that hasn't been categorized.
---

# General Programming Notes

## Good MVC application architecture

### Server side

#### Database / Disk storage / Memcache / Tables

Might do serverside caching. Objects stored in a db does not need to be saved to memcaches unless there is multiple databases. Memcache is useful for temporary data storage. Disk storage is useful for large binary temporary storage. Tables are useful for large binary persistent storage.

#### Persistence / DBLayer / Data Access Layer

Does ALL data retrieval and data storage. Server side caching \(memcache etc\). Returns one or a list of objects. Should not return serialized data, only objects or list of primary keys. The returned objects should contain as much data as you can allow, because if the client request an object they will probably want related objects to it next. No need to make the user query twice. Makes sure the data will fit its container \(string length, number clamping etc.\).

#### Domain

Does businesslogic. No authorization or authentication on this layer. Should not be static.

#### Service

Types: WCF, REST etc.. Does authorization checks. Manages client side caching.

### Client side

#### Stores

A collection of stores which retrieves or saves data. Never create more than one store per object in the application. Does cache busting when user modifies an object. Stores should fire events when something is modified.

Data sources might be:

* A service
* A localStorage
* Cookies
* Browser
  * Browser API calls \(GPS, device information, etc..\)
* No data source \(data only available while the browser window is open\)

#### Application / Controllers / Routes

The application and its controllers and routes. Contains action logic. Requests models from store and sends it to the view, or takes a model and sends it back to the store.

#### UI Rendering

Views. Rendered after retrieving a model. Renders html. Binds actions to UI events. Might subscribe to events from the store, and might refresh if a certain event is fired.

