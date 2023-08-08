# openHAB-REST-API-Client-Libraries
Client libraries to access the REST API of openHAB.

| REST endpoints | [Android-Java](https://github.com/Michdo93/android-java-openHAB-Client-Library) | [Android-Kotlin](https://github.com/Michdo93/android-kotlin-openHAB-Client-Library) | [C++](https://github.com/Michdo93/cpp-openHAB-Client-Library) | [C#](https://github.com/Michdo93/csharp-openHAB-Client-Library) | [Java](https://github.com/Michdo93/java-openHAB-Client-Library) | [JavaScript](https://github.com/Michdo93/JavaScript-openHAB-Client-Library) | [jQuery](https://github.com/Michdo93/jQuery-openHAB-Client-Library) | [NodeJS](https://github.com/Michdo93/NodeJS-openHAB-Client-Library) | [Python](https://github.com/Michdo93/Python-openHAB-Client-Library) |
| -------------- | ------------ | -------------- | --- | -- | ---- | ---------- | ------ | ------ | ------ |
| addons         | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| audio          | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| auth           | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| bindings       | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| channel-types  | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| config-descriptions | :x:    | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| discovery      | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| events         | :x:          | :x:            | :x: | :heavy_check_mark:| :heavy_check_mark:  | :heavy_check_mark:        | :x:    | :x:    | :heavy_check_mark:    |
| habpanel       | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| iconsets       | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| inbox          | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| items          | :heavy_check_mark:          | :x:            | :x: | :heavy_check_mark:| :heavy_check_mark:  | :heavy_check_mark:        | :x:    | :x:    | :heavy_check_mark:    |
| links          | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| logging        | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| module-types   | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| persistence    | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| profile-types  | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| rules          | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| services       | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| sitemaps       | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| systeminfo     | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| templates      | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| things         | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| thing-types    | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| transformations| :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| ui             | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| uuid           | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |
| voice          | :x:          | :x:            | :x: | :x:| :x:  | :x:        | :x:    | :x:    | :x:    |

## Endpoint description

| Element        | Details                                                                       |
|----------------|-------------------------------------------------------------------------------|
| Endpoint       | /                                                                             |
| HTTP Method    | GET                                                                           |
| Tags           | "root"                                                                        |
| Summary        | "Gets information about the runtime, the API version and links to resources." |
| operationId    | "getRoot"                                                                     |
| Responses      | 200: "OK"                                                                     |
| Content        | application/json                                                              |
| Schema         | $ref: "#/components/schemas/RootBean"                                         |


### addons

| Endpoint   | Method | Tags   | Summary                                     | Operation ID | Parameters                                                  | Responses                           |
| ---------- | ------ | ------ | ------------------------------------------- | ------------ | ----------------------------------------------------------- | ----------------------------------- |
| /addons    | GET    | addons | Get all add-ons.                            | getAddons    | Accept-Language (header)<br>type: string<br>serviceId (query)<br>type: string | 200 - OK<br>404 - Service not found |
| /addons/{addonId}  | GET    | addons | Get add-on with given ID | getAddonById   | Accept-Language (header)<br>type: string<br>addonId (path)<br>type: string<br>serviceId (query)<br>type: string | 200 - OK<br>404 - Not found |
| /addons/services      | GET    | addons | Get all add-on types | getAddonTypes   | Accept-Language (header)<br>type: string | 200 - OK        |
| /addons/types         | GET    | addons | Get add-on services | getAddonServices  | Accept-Language (header)<br>type: string<br>serviceId (query)<br>type: string | 200 - OK<br>404 - Service not found |
| /addons/{addonId}/install | POST   | addons | Installs the add-on with the given ID. | installAddonById   | addonId (path)<br>type: string<br>required: true<br>serviceId (query)<br>type: string | 200 - OK<br>404 - Not found |
| /addons/url/{url}/install       | POST   | addons | Installs the add-on from the given URL. | installAddonFromURL | url (path)<br>type: string<br>required: true | 200 - OK<br>400 - The given URL is malformed or not valid. |
| /addons/{addonId}/uninstall      | POST   | addons | Uninstalls the add-on with the given ID. | uninstallAddon | addonId (path)<br>type: string<br>required: true | 200 - OK<br>404 - Not found       |

### audio

| Endpoint           | Method | Tags  | Summary                                               | Operation ID        | Responses                                                                                       |
| ------------------ | ------ | ----- | ----------------------------------------------------- | ------------------- | ----------------------------------------------------------------------------------------------- |
| /audio/defaultsink | GET    | audio | Get the default sink if defined or the first available sink. | getAudioDefaultSink | 200 - OK<br>content: application/json<br>schema: $ref: "#/components/schemas/AudioSinkDTO"<br>404 - Sink not found |
| /audio/defaultsource | GET    | audio | Get the default source if defined or the first available source. | getAudioDefaultSource  | 200 - OK<br>content: application/json<br>schema: $ref: "#/components/schemas/AudioSourceDTO"<br>404 - Source not found |
| /audio/sinks   | GET    | audio | Get the list of all sinks.   | getAudioSinks     | 200 - OK<br>content: application/json<br>schema: type: array<br>items: $ref: "#/components/schemas/AudioSinkDTO" |
| /audio/sources  | GET    | audio | Get the list of all sources.| getAudioSources    | 200 - OK<br>content: application/json<br>schema: type: array<br>items: $ref: "#/components/schemas/AudioSourceDTO" |


### auth

| Endpoint     | Method | Tags  | Summary                                           | Operation ID    | Request Body                                                                                            | Responses                                    |
| ------------ | ------ | ----- | ------------------------------------------------- | --------------- | ------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| /auth/logout | POST   | auth  | Delete the session associated with a refresh token. | deleteSession   | content: application/x-www-form-urlencoded<br>schema: type: object<br>properties: refresh_token: type: string id: type: string | 200 - OK<br>401 - User is not authenticated<br>404 - User or refresh token not found |
| /auth/apitokens    | GET    | auth  | List the API tokens associated to the authenticated user. | getApiTokens   | 200 - OK<br>401 - User is not authenticated<br>404 - User not found |
| /auth/sessions    | GET    | auth  | List the sessions associated to the authenticated user. | getSessionsForCurrentUser | 200 - OK<br>401 - User is not authenticated<br>404 - User not found |
| /auth/token   | POST   | auth  | Get access and refresh tokens. | getOAuthToken | useCookie (query)<br>type: boolean            | grant_type (form data)<br>type: string<br>code (form data)<br>type: string<br>redirect_uri (form data)<br>type: string<br>client_id (form data)<br>type: string<br>refresh_token (form data)<br>type: string<br>code_verifier (form data)<br>type: string | 200 - OK<br>400 - Invalid request parameters |
| /auth/apitokens/{name}   | DELETE | auth  | Revoke a specified API token associated to the authenticated user. | removeApiToken | name (path)<br>type: string | 200 - OK<br>401 - User is not authenticated<br>404 - User or API token not found |

### bindings

| Endpoint                | Method | Tags     | Summary           | Operation ID | Parameters                                | Responses                 |
| ----------------------- | ------ | -------- | ----------------- | ------------ | ----------------------------------------- | ------------------------- |
| /bindings               | GET    | bindings | Get all bindings. | getBindings  | Accept-Language (header)<br>type: string | 200 - OK<br>security: oauth2 |
| /bindings/{bindingId}/config           | GET    | bindings | Get binding configuration for given binding ID. | getBindingConfiguration  | bindingId (path)<br>type: string                     | 200 - OK<br>404 - Binding does not exist<br>500 - Configuration can not be read due to internal error<br>security: oauth2 |
| /bindings/{bindingId}/config           | PUT    | bindings | Updates a binding configuration for given binding ID and returns the old configuration. | updateBindingConfiguration | bindingId (path)<br>type: string<br>requestBody (content)<br>type: object<br>additionalProperties (type)<br>type: object | 200 - OK<br>204 - No old configuration<br>404 - Binding does not exist<br>500 - Configuration can not be updated due to internal error<br>security: oauth2 |

### channel-types

| Endpoint                               | Method | Tags            | Summary                                    | Operation ID      | Parameters                                                                                               | Responses                         |
| -------------------------------------- | ------ | --------------- | ------------------------------------------ | ----------------- | -------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| /channel-types                         | GET    | channel-types   | Gets all available channel types.          | getChannelTypes   | Accept-Language (header)<br>type: string<br>prefixes (query)<br>type: string<br>description: filter UIDs by prefix (multiple comma-separated prefixes allowed, for example: 'system,mqtt') | 200 - OK<br>security: oauth2       |
| /channel-types/{channelTypeUID}            | GET    | channel-types   | Gets channel type by UID.               | getChannelTypeByUID  | channelTypeUID (path)<br>type: string<br>description: channelTypeUID<br>required: true<br>Accept-Language (header)<br>type: string                                    | 200 - Channel type with provided channelTypeUID does not exist.<br>404 - No content<br>security: oauth2 |
| /channel-types/{channelTypeUID}/linkableItemTypes | GET    | channel-types   | Gets the item types the given trigger channel type UID can be linked to. | getLinkableItemTypesByChannelTypeUID | channelTypeUID (path)<br>type: string<br>description: channelTypeUID<br>required: true<br>Accept-Language (header)<br>type: string | 200 - OK<br>content: application/json<br>schema: uniqueItems: true<br>type: array<br>items: type: string<br>204 - No content: channel type has no linkable items or is no trigger channel.<br>404 - Given channel type UID not found. | security: oauth2 |

### config-descriptions

| Endpoint                 | Method | Tags                  | Summary                                | Operation ID          | Parameters                                                                                   | Responses                                                                                                     |
| ------------------------ | ------ | --------------------- | -------------------------------------- | --------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| /config-descriptions     | GET    | config-descriptions   | Gets all available config descriptions. | getConfigDescriptions | Accept-Language (header)<br>type: string<br>scheme (query)<br>type: string<br>description: scheme filter | 200 - OK<br>content: application/json<br>schema: type: array<br>items: $ref: "#/components/schemas/ConfigDescriptionDTO" | security: oauth2 |
| /config-descriptions/{uri}           | GET    | config-descriptions   | Gets a config description by URI.      | getConfigDescriptionByURI | Accept-Language (header)<br>type: string<br>uri (path)<br>type: string<br>description: uri | 200 - OK<br>content: application/json<br>schema: $ref: "#/components/schemas/ConfigDescriptionDTO"<br>400 - Invalid URI syntax<br>404 - Not found | security: oauth2 |

### discovery

| Endpoint                           | Method | Tags           | Summary                                    | Operation ID                      | Responses                                                                               |
| ---------------------------------- | ------ | -------------- | ------------------------------------------ | --------------------------------- | --------------------------------------------------------------------------------------- |
| /discovery                         | GET    | discovery      | Gets all bindings that support discovery.  | getBindingsWithDiscoverySupport  | 200 - OK<br>content: application/json<br>schema: uniqueItems: true<br>type: array<br>items: type: string | security: oauth2 |
| /discovery/bindings/{bindingId}/scan | POST   | discovery      | Starts asynchronous discovery process for a binding and returns the timeout in seconds of the discovery operation. | scan          | 200 - OK<br>content: text/plain<br>schema: type: integer<br>format: int32<br>security: oauth2 |

### events

| Endpoint                  | HTTP Method | Tags        | Summary                                                     | operationId                      | Parameters                |  Responses               |
|--------------------------|-------------|-------------|-------------------------------------------------------------|----------------------------------|---------------------------|-------------------------|
| /events                  | GET         | "events"    | Get all events.                                             | "getEvents"                      | | 200: "OK"               |
|                          |             |             |                                                             |                                  | 400: "Topic is empty or contains invalid characters" |
| /events/states           | GET         | "events"    | Initiates a new item state tracker connection             | "initNewStateTacker"             | | 200: "OK"               |
| /events/states/{connectionId} | POST    | "events"    | Changes the list of items a SSE connection will receive state updates to. | "updateItemListForStateUpdates" | name: "connectionId"      | 200: "OK"                |
|                          |             |             |                                                             |                                  | in: "path"                | 404: "Unknown connectionId" |


### habpanel

| Endpoint                                | Method | Tags      | Summary                        | Operation ID         | Parameters                                                                                              | Responses                                                                                                             |
| --------------------------------------- | ------ | --------- | ------------------------------ | -------------------- | ------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| /habpanel/gallery/{galleryName}/widgets | GET    | habpanel  | Gets the list of widget gallery items. | getGalleryWidgetList | 0: name: "galleryName"<br>   in: "path"<br>   description: "gallery name e.g. 'community'"<br>   required: true<br>   schema: type: "string" | 200 - OK<br>content: application/json<br>schema: type: "array"<br>items: $ref: "#/components/schemas/GalleryWidgetsListItem"<br>404 - Unknown gallery |
| /habpanel/gallery/{galleryName}/widgets/{id} | GET    | habpanel  | Gets the details about a widget gallery item. | getGalleryWidgetsItem | 0: name: "galleryName"<br>   in: "path"<br>   description: "gallery name e.g. 'community'"<br>   required: true<br>   schema: type: "string"<br> 1: name: "id"<br>   in: "path"<br>   description: "id within the gallery"<br>   required: true<br>   schema: type: "string" | 200 - OK<br>content: application/json<br>schema: $ref: "#/components/schemas/GalleryItem"<br>404 - Unknown gallery or gallery item not found |


### iconsets

| Endpoint    | Method | Tags      | Summary           | Operation ID | Parameters                                                      | Responses                                                     |
| ----------- | ------ | --------- | ----------------- | ------------ | --------------------------------------------------------------- | ------------------------------------------------------------ |
| /iconsets   | GET    | iconsets  | Gets all icon sets | getIconSets  | 0: name: "Accept-Language"<br>   in: "header"<br>   description: "language"<br>   schema: type: "string" | 200 - OK<br>content: application/json<br>schema: type: "array"<br>items: $ref: "#/components/schemas/IconSet" |


### inbox

| Endpoint                | Method | Tags   | Summary                                                           | Operation ID          | Parameters                                                                                         | Request Body                                              | Responses                                                                                                          | Security            |
| ----------------------- | ------ | ------ | ----------------------------------------------------------------- | --------------------- | -------------------------------------------------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | -------------------- |
| /inbox/{thingUID}/approve | POST   | inbox  | Approves the discovery result by adding the thing to the registry. | approveInboxItemById  | Accept-Language: header<br>thingUID: path (required)<br>newThingId: query (description: new thing ID) | content: text/plain<br>schema: type: string              | 200 - OK<br>400 - Invalid new thing ID<br>404 - Thing unable to be approved<br>409 - No binding found that supports this thing | oauth2: admin        |
| /inbox/{thingUID}  | DELETE | inbox  | Removes the discovery result from the inbox. | removeItemFromInbox | thingUID: path (required)                  | 200 - OK<br>404 - Discovery result not found in the inbox | oauth2: admin |
| /inbox                      | GET    | inbox  | Get all discovered things.       | getDiscoveredInboxItems | 200 - OK<br>content: application/json<br>schema: array items: $ref: "#/components/schemas/DiscoveryResultDTO" | oauth2: admin |
| /inbox/{thingUID}/ignore    | POST   | inbox  | Flags a discovery result as ignored.      | flagInboxItemAsIgnored     | 200 - OK              | oauth2: admin |
| /inbox/{thingUID}/unignore        | POST   | inbox  | Removes ignore flag from a discovery result. | removeIgnoreFlagOnInboxItem | 200 - OK              | oauth2: admin |

### items

| Endpoint                           | HTTP Method | Tags     | Summary                                    | operationId            | Parameters                               | Request Body   | Responses                                                          | Security          |
|-----------------------------------|-------------|----------|--------------------------------------------|------------------------|------------------------------------------|----------------|-------------------------------------------------------------------|-------------------|
| /items/{itemName}/members/{memberItemName} | PUT         | "items"  | "Adds a new member to a group item."       | "addMemberToGroupItem" | name: "itemName"                       |                | 200: "OK"                                                          | oauth2: "admin"   |
|                                   |             |          |                                            |                        | in: "path"                             |                | 404: "Item or member item not found or item is not of type group item." |                   |
|                                   |             |          |                                            |                        | description: "item name"               |                | 405: "Member item is not editable."                              |                   |
|                                   |             |          |                                            |                        | required: true                        |                |                                                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | name: "memberItemName"                 |                |                                                                   |                   |
|                                   |             |          |                                            |                        | in: "path"                             |                |                                                                   |                   |
|                                   |             |          |                                            |                        | description: "member item name"        |                |                                                                   |                   |
|                                   |             |          |                                            |                        | required: true                        |                |                                                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
| /items/{itemname}/metadata/{namespace} | PUT         | "items"  | "Adds metadata to an item."               | "addMetadataToItem"    | name: "itemname"                       |                | 200: "OK"                                                          | oauth2: "admin"   |
|                                   |             |          |                                            |                        | in: "path"                             |                | 201: "Created"                                                     |                   |
|                                   |             |          |                                            |                        | description: "item name"               |                | 400: "Metadata value empty."                                       |                   |
|                                   |             |          |                                            |                        | required: true                        |                | 404: "Item not found."                                             |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                | 405: "Metadata not editable."                                      |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | name: "namespace"                     |                |                                                                   |                   |
|                                   |             |          |                                            |                        | in: "path"                             |                |                                                                   |                   |
|                                   |             |          |                                            |                        | description: "namespace"              |                |                                                                   |                   |
|                                   |             |          |                                            |                        | required: true                        |                |                                                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
| /items/{itemname}/tags/{tag}       | PUT         | "items"  | "Adds a tag to an item."                   | "addTagToItem"         | name: "itemname"                       |                | 200: "OK"                                                          | oauth2: "admin"   |
|                                   |             |          |                                            |                        | in: "path"                             |                |                                                                   |                   |
|                                   |             |          |                                            |                        | description: "item name"               |                |                                                                   |                   |
|                                   |             |          |                                            |                        | required: true                        |                |                                                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                | 404: "Item not found."                                             |                   |
|                                   |             |          |                                            |                        |                                      |                | 405: "Item not editable."                                          |                   |
| /items/{itemname}/tags/{tag}       | DELETE      | "items"  | "Removes a tag from an item."              | "removeTagFromItem"    | name: "itemname"                       |                | 200: "OK"                                                          | oauth2: "admin"   |
|                                   |             |          |                                            |                        | in: "path"                             |                |                                                                   |                   |
|                                   |             |          |                                            |                        | description: "item name"               |                |                                                                   |                   |
|                                   |             |          |                                            |                        | required: true                        |                |                                                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                | 404: "Item not found."                                             |                   |
|                                   |             |          |                                            |                        |                                      |                | 405: "Item not editable."                                          |                   |
| /items/{itemname}                 | GET         | "items"  | "Gets a single item."                      | "getItemByName"        | name: "Accept-Language"                |                | 200: "OK"                                                          |                   |
|                                   |             |          |                                            |                        | description: "language"                |                | 404: "Item not found"                                              |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | name: "metadata"                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | description: "metadata selector - a comma separated list or a regular expression (suppressed if no value given)" | |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | name: "recursive"                     |                |                                                                   |                   |
|                                   |             |          |                                            |                        | description: "get member items if the item is a group item" |         |                                                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "boolean"              | default: true                  |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | name: "itemname"                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | description: "item name"               | required: true                 |                                                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                | 200: "OK"                                                          |                   |
|                                   |             |          |                                            |                        | content: application/json             | schema: {...}                  |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | 404: "Item not found."               |                                      |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | 405: "Item not editable."            |                                      |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | oauth2:                               |                                      |                                                                   |                   |
|                                   |             |          |                                            |                        | 0: "admin"                           |                                      |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
| /items                             | GET         | "items"  | "Get all available items."                 | "getItems"             | name: "Accept-Language"                |                | 200: "OK"                                                          |                   |
|                                   |             |          |                                            |                        | description: "language"                |                |                                                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | name: "type"                          |                |                                                                   |                   |
|                                   |             |          |                                            |                        | description: "item type filter"       |                |                                                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | name: "tags"                          |                |                                                                   |                   |
|                                   |             |          |                                            |                        | description: "item tag filter"        |                |                                                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | name: "metadata"                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | description: "metadata selector - a comma separated list or a regular expression (suppressed if no value given)" | |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | name: "recursive"                     |                |                                                                   |                   |
|                                   |             |          |                                            |                        | description: "get member items recursively" |                       |                                                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "boolean"              | default: false                 |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | name: "fields"                        |                |                                                                   |                   |
|                                   |             |          |                                            |                        | description: "limit output to the given fields (comma separated)" |       |                                                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | 200: "OK"                            | content: application/json       | schema: {...}                  |                                      |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
| /items                             | PUT         | "items"  | "Adds a list of items to the registry or updates the existing items." |         | name: "Accept-Language"                |                | 200: "OK"                                                          | oauth2: "admin"   |
|                                   |             |          |                                            |                        | description: "language"                |                | 400: "Payload is invalid."                                         |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | name: "itemname"                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | description: "item name"               | required: true                 |                                                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | 200: "OK"                            | content: */*                    | schema: {...}                  |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | 405: "Item not editable."            |                                      |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
|                                   |             |          |                                            |                        | oauth2:                               |                                      |                                                                   |                   |
|                                   |             |          |                                            |                        | 0: "admin"                           |                                      |                                                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                                                   |                   |
| /items/{itemname}/state           | GET         | "items"  | "Gets the state of an item."               | "getItemState_1"       | name: "itemname"                       |                | 200: "OK"                                                          |                   |
|                                   |             |          |                                            |                        | in: "path"                             |                | content: text/plain                 |                   |
|                                   |             |          |                                            |                        | description: "item name"               |                | schema: {...}                      |                   |
|                                   |             |          |                                            |                        | required: true                        |                |                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                   |                   |
|                                   |             |          |                                            |                        |                                      |                | 404: "Item not found"              |                   |
| /items/{itemname}/state           | PUT         | "items"  | "Updates the state of an item."            | "updateItemState"     | name: "Accept-Language"                |                | 202: "Accepted"                   |                   |
|                                   |             |          |                                            |                        | in: "header"                           |                | 400: "Item state null"           |                   |
|                                   |             |          |                                            |                        | description: "language"                |                | 404: "Item not found"              |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                   |                   |
|                                   |             |          |                                            |                        | name: "itemname"                      |                |                                   |                   |
|                                   |             |          |                                            |                        | description: "item name"               | required: true                 |                                   |                   |
|                                   |             |          |                                            |                        | schema: type: "string"                |                |                                   |                   |
|                                   |             |          |                                            |                        |                                      |                |                                   |                   |
|                                   |             |          |                                            |                        |                                      |                | 404: "Item not found"              |                   |
| /items/{itemName}/semantic/{semanticClass} | GET     | "items"  | "Gets the item which defines the requested semantics of an item." | "getSemanticItem" | name: "Accept-Language"                |                | 200: "OK"                      |               |
|                                   |             |          |                                                |                    | in: "header"                           |                | 404: "Item not found"          |               |
|                                   |             |          |                                                |                    | description: "language"                |                |                               |               |
|                                   |             |          |                                                |                    | schema: type: "string"                |                |                               |               |
|                                   |             |          |                                                |                    |                                      |                |                               |               |
|                                   |             |          |                                                |                    | name: "itemName"                      |                |                               |               |
|                                   |             |          |                                                |                    | description: "item name"               | required: true                 |                               |               |
|                                   |             |          |                                                |                    | schema: type: "string"                |                |                               |               |
|                                   |             |          |                                                |                    |                                      |                |                               |               |
|                                   |             |          |                                                |                    | name: "semanticClass"                  |                |                               |               |
|                                   |             |          |                                                |                    | description: "semantic class"        | required: true                 |                               |               |
|                                   |             |          |                                                |                    | schema: type: "string"                |                |                               |               |
| /items/metadata/purge             | POST        | "items"  | "Remove unused/orphaned metadata."            | "purgeDatabase"    |                                      |                | 200: "OK"                      | oauth2:        |
|                                   |             |          |                                                |                    |                                      |                |                               | 0: "admin"    |

### links

| Endpoint                          | HTTP Method | Tags     | Summary                                        | operationId        | Parameters                               | Request Body   | Responses                      | Security      |
|-----------------------------------|-------------|----------|------------------------------------------------|--------------------|------------------------------------------|----------------|-------------------------------|---------------|
| /links                            | GET         | "links"  | "Gets all available links."                  | "getItemLinks"     | name: "channelUID"                     |                | 200: "OK"                      | oauth2:        |
|                                   |             |          |                                                |                    | in: "query"                          |                |                               | 0: "admin"    |
|                                   |             |          |                                                |                    | description: "filter by channel UID" |                |                               |               |
|                                   |             |          |                                                |                    | schema: type: "string"                |                |                               |               |
|                                   |             |          |                                                |                    |                                      |                |                               |               |
|                                   |             |          |                                                |                    | name: "itemName"                     |                |                               |               |
|                                   |             |          |                                                |                    | description: "filter by item name"   |                |                               |               |
|                                   |             |          |                                                |                    | schema: type: "string"                |                |                               |               |
|                                   |             |          |                                                |                    |                                      |                |                               |               |
|                                   |             |          |                                                |                    |                                      |                | 200: "OK"                      |               |
|                                   |             |          |                                                |                    | content: application/json            | schema: {...}                  |                               |               |
|                                   |             |          |                                                |                    |                                      |                |                               |               |
|                                   |             |          |                                                |                    | oauth2:                               |                                |                               |               |
|                                   |             |          |                                                |                    | 0: "admin"                           |                                |                               |               |
| /links/{itemName}/{channelUID}   | GET                                           |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
|                                  |                                             |                                |
| /links/{itemName}/{channelUID}   | GET         | "links"  | "Retrieves an individual link."              | "getItemLink"          | name: "itemName"                     |                                    | 200: "OK"                          | oauth2: 0: "admin" |
|                                  |             |          |                                               |                        | in: "path"                           |                                    | 404: "Content does not match the path" |                   |
|                                  |             |          |                                               |                        | description: "item name"             |                                    |                                   |                   |
|                                  |             |          |                                               |                        | required: true                      |                                    |                                   |                   |
|                                  |             |          |                                               |                        | schema: type: "string"              |                                    |                                   |                   |
|                                  |             |          |                                               |                        |                                      |                                    |                                   |                   |
|                                  |             |          |                                               |                        | name: "channelUID"                  |                                    |                                   |                   |
|                                  |             |          |                                               |                        | description: "channel UID"          |                                    |                                   |                   |
|                                  |             |          |                                               |                        | required: true                      |                                    |                                   |                   |
|                                  |             |          |                                               |                        | schema: type: "string"              |                                    |                                   |                   |
|                                  |             |          |                                               |                        |                                      |                                    |                                   |                   |
|                                  |             |          |                                               |                        |                                      |                                    |                                   |                   |
|                                  |             |          |                                               |                        |                                      |                                    |                                   |                   |
|                                  |             |          |                                               |                        |                                      |                                    |                                   |                   |
| /links/{itemName}/{channelUID}    | PUT         | "links"  | "Links an item to a channel."                | "linkItemToChannel" | name: "itemName"                     |                | 200: "OK"                      | oauth2: 0: "admin" |
|                                   |             |          |                                               |                    | in: "path"                           |                | 400: "Content does not match the path" |               |
|                                   |             |          |                                               |                    | description: "item name"             |                | 405: "Link is not editable"    |               |
|                                   |             |          |                                               |                    | required: true                      |                |                               |               |
|                                   |             |          |                                               |                    | schema: type: "string"              |                |                               |               |
|                                   |             |          |                                               |                    |                                      |                |                               |               |
|                                   |             |          |                                               |                    | name: "channelUID"                  |                |                               |               |
|                                   |             |          |                                               |                    | description: "channel UID"          |                |                               |               |
|                                   |             |          |                                               |                    | required: true                      |                |                               |               |
|                                   |             |          |                                               |                    | schema: type: "string"              |                |                               |               |
| /links/{itemName}/{channelUID}    | DELETE      | "links"  | "Unlinks an item from a channel."           | "unlinkItemFromChannel" | name: "itemName"                     |                                    | 200: "OK"                          | oauth2: 0: "admin" |
|                                  |             |          |                                               |                        | in: "path"                           |                                    | 404: "Link not found."            |                   |
|                                  |             |          |                                               |                        | description: "itemName"             |                                    | 405: "Link not editable."         |                   |
|                                  |             |          |                                               |                        | required: true                      |                                    |                                   |                   |
|                                  |             |          |                                               |                        | schema: type: "string"              |                                    |                                   |                   |
|                                  |             |          |                                               |                        |                                      |                                    |                                   |                   |
|                                  |             |          |                                               |                        | name: "channelUID"                  |                                    |                                   |                   |
|                                  |             |          |                                               |                        | description: "channelUID"            |                                    |                                   |                   |
|                                  |             |          |                                               |                        | required: true                      |                                    |                                   |                   |
|                                  |             |          |                                               |                        | schema: type: "string"              |                                    |                                   |                   |
|                                  |             |          |                                               |                        |                                      |                                    |                                   |                   |
|                                  |             |          |                                               |                        |                                      |                                    |                                   |                   |
|                                  |             |          |                                               |                        |                                      |                                    |                                   |                   |
| /links/purge   | POST        | "links" | "Remove unused/orphaned links."     | "purgeDatabase_1" |                     |                    | 200: "OK"         | oauth2: 0: "admin" |
| /links/{object}             | DELETE      | "links" | "Delete all links that refer to an item or thing." | "removeAllLinksForObject"  |                                      |              | 200: "OK"   | oauth2: 0: "admin" |

### logging

| Endpoint              | Method | Tags     | Summary                            | Operation ID | Parameters                                                                                                         | Responses                                                     |
| --------------------- | ------ | -------- | ---------------------------------- | ------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------ |
| /logging/{loggerName} | GET    | logging  | Get a single logger.               | getLogger    | - name: loggerName<br>  in: path<br>  description: logger name<br>  required: true<br>  schema: {type: "string"} | 200 - OK<br>content: application/json<br>schema: $ref: "#/components/schemas/LoggerInfo"<br>security: 0: oauth2: 0: "admin" |
| /logging/{loggerName} | PUT    | logging  | Modify or add logger               | putLogger    | - name: loggerName<br>  in: path<br>  description: logger name<br>  required: true<br>  schema: {type: "string"} | 200 - OK<br>400 - Payload is invalid.<br>security: 0: oauth2: 0: "admin" |
| /logging/{loggerName} | DELETE | logging  | Remove a single logger.            | removeLogger | - name: loggerName<br>  in: path<br>  description: logger name<br>  required: true<br>  schema: {type: "string"} | 200 - OK<br>security: 0: oauth2: 0: "admin"                   |
| /logging    | GET    | logging  | Get all loggers | getLogger_1   | 200 - OK<br>content: application/json<br>schema: $ref: "#/components/schemas/LoggerBean"<br>security: 0: oauth2: 0: "admin" |


### module-types

| Endpoint              | Method | Tags          | Summary                            | Operation ID   | Parameters                                                                                                                                                       | Responses                                                                                                            |
| --------------------- | ------ | ------------- | ---------------------------------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| /module-types         | GET    | module-types  | Get all available module types.    | getModuleTypes | 0: name: "Accept-Language"<br>   in: "header"<br>   description: "language"<br>   schema: type: "string"<br> 1: name: "tags"<br>   in: "query"<br>   description: "tags for filtering"<br>   schema: type: "string"<br> 2: name: "type"<br>   in: "query"<br>   description: "filtering by action, condition or trigger"<br>   schema: type: "string" | 200 - OK<br>content: application/json<br>schema: type: "array"<br>items: $ref: "#/components/schemas/ModuleTypeDTO" |
| /module-types/{moduleTypeUID}     | GET    | module-types  | Gets a module type corresponding to the given UID. | getModuleTypeById  | 0: name: "Accept-Language"<br>   in: "header"<br>   description: "language"<br>   schema: type: "string"<br> 1: name: "moduleTypeUID"<br>   in: "path"<br>   description: "moduleTypeUID"<br>   required: true<br>   schema: type: "string" | 200 - OK<br>content: application/json<br>schema: {…}<br>404 - Module Type corresponding to the given UID does not found. |


### persistence

| Endpoint                             | HTTP Method | Tags          | Summary                                                 | operationId                            | Parameters                                       | Request Body                   | Responses                            | Security              |
|---------------------------------------|-------------|---------------|---------------------------------------------------------|----------------------------------------|--------------------------------------------------|-------------------------------|--------------------------------------|-----------------------|
| /persistence/items/{itemname}         | GET         | "persistence" | "Gets item persistence data from the persistence service." | "getItemDataFromPersistenceService"   | name: "serviceId"                              |                                | 200: "OK"                            |                       |
|                                     |             |               |                                                         |                                        | in: "query"                                    |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "Id of the persistence service. If not provided the default service will be used" | required: false                |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "string"                        |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | name: "itemname"                              |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "The item name"                  | required: true                |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "string"                        |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | name: "starttime"                             | in: "query"                    |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "Start time of the data to return. Will default to 1 day before endtime. [yyyy-MM-dd'T'HH:mm:ss.SSSZ]" | required: false               |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "string"                        |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | name: "endtime"                               | in: "query"                    |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "End time of the data to return. Will default to current time. [yyyy-MM-dd'T'HH:mm:ss.SSSZ]" | required: false               |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "string"                        |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | name: "page"                                  | in: "query"                    |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "Page number of data to return. This parameter will enable paging." | required: false               |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "integer"                       | format: "int32"                |                                    |                       |
|                                     |             |               |                                                         |                                        | name: "pagelength"                            | in: "query"                    |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "The length of each page."       | required: false               |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "integer"                       | format: "int32"                |                                    |                       |
|                                     |             |               |                                                         |                                        | name: "boundary"                              | in: "query"                    |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "Gets one value before and after the requested period." | required: false               |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "boolean"                       |                                |                                    |                       |
|                                     |             |               |                                                         |                                        |                                      |                                |                                    |                       |
|                                     |             |               |                                                         |                                        |                                      |                                | 200: "OK"                            |                       |
|                                     |             |               |                                                         |                                        | content: application/json                     | schema: {...}                  |                                    |                       |
| /persistence/items/{itemname}         | PUT         | "persistence" | "Stores item persistence data into the persistence service." | "storeItemDataInPersistenceService"   | name: "serviceId"                              |                                | 200: "OK"                            | oauth2: 0: "admin"    |
|                                     |             |               |                                                         |                                        | in: "query"                                    |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "Id of the persistence service. If not provided the default service will be used" | required: false                |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "string"                        |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | name: "itemname"                              |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "The item name."                 | required: true                |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "string"                        |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | name: "time"                                  | in: "query"                    |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "Time of the data to be stored. Will default to current time. [yyyy-MM-dd'T'HH:mm:ss.SSSZ]" | required: true                |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "string"                        |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | name: "state"                                 | in: "query"                    |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "The state to store."            | required: true                |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "string"                        |                                |                                    |                       |
|                                     |             |               |                                                         |                                        |                                      |                                |                                    |                       |
|                                     |             |               |                                                         |                                        |                                      |                                | 200: "OK"                            |                       |
| /persistence/items/{itemname}         | DELETE      | "persistence" | "Deletes item persistence data from a specific persistence service in a given time range." | "deleteItemFromPersistenceService"   | name: "serviceId"                              |                                | 200: "OK"                            | oauth2: 0: "admin"    |
|                                     |             |               |                                                         |                                        | in: "query"                                    |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "Id of the persistence service." | required: true                 |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "string"                        |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | name: "itemname"                              |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "The item name."                 | required: true                |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "string"                        |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | name: "starttime"                             | in: "query"                    |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "Start of the time range to be deleted. [yyyy-MM-dd'T'HH:mm:ss.SSSZ]" | required: true                |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "string"                        |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | name: "endtime"                               | in: "query"                    |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "End of the time range to be deleted. [yyyy-MM-dd'T'HH:mm:ss.SSSZ]" | required: true                |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "string"                        |                                |                                    |                       |
|                                     |             |               |                                                         |                                        |                                      |                                |                                    |                       |
|                                     |             |               |                                                         |                                        |                                      |                                | 200: "OK"                            |                       |
|                                     |             |               |                                                         |                                        | content: application/json                     | schema: {...}                  |                                    |                       |
|                                     |             |               |                                                         |                                        |                                      |                                | 400: "Invalid filter parameters"     |                       |
|                                     |             |               |                                                         |                                        |                                      |                                | 404: "Unknown persistence service" |                       |
| /persistence                         | GET         | "persistence" | "Gets a list of persistence services."                | "getPersistenceServices"              | name: "Accept-Language"                      |                                | 200: "OK"                            |                       |
|                                     |             |               |                                                         |                                        | in: "header"                                  |                                |                                    |                       |
|                                     |             |               |                                                         |                                        | description: "language"                      | required: false               |                                    |                       |
|                                     |             |               |                                                         |                                        | schema: type: "string"                        |                                |                                    |                       |
|                                     |             |               |                                                         |                                        |                                      |                                |                                    |                       |
|                                     |             |               |                                                         |                                        |                                      |                                | 200: "OK"                            |                       |
|                                     |             |               |                                                         |                                        | content: application/json                     | schema: {...}                  |                                    |                       |
|                                     |             |               |                                                         |                                        |                                      |                                |                                    |                       |
|                                     |             |               |                                                         |                                        |                                      |                                |                                    |                       |
|                                     |             |               |                                                         |                                        |                                      |                                |                                    |                       |
|                                     |             |               |                                                         |                                        |                                      |                                |                                    |                       |

### profile-types

| Endpoint                             | HTTP Method | Tags          | Summary                                                 | operationId                            | Parameters                                       | Request Body                   | Responses                            | Security              |
|---------------------------------------|-------------|---------------|---------------------------------------------------------|----------------------------------------|--------------------------------------------------|-------------------------------|--------------------------------------|-----------------------|
| /profile-types                        | GET         | "profile-types" | "Gets all available profile types."                    | "getProfileTypes"                     | name: "Accept-Language"                      |                                | 200: "OK"                            | oauth2: 0: "admin"    |
|                                       |             |               |                                                         |                                        | in: "header"                                |                                |                                      |                       |
|                                       |             |               |                                                         |                                        | description: "language"                    | required: false                |                                      |                       |
|                                       |             |               |                                                         |                                        | schema: type: "string"                      |                                |                                      |                       |
|                                       |             |               |                                                         |                                        | name: "channelTypeUID"                     | in: "query"                                |                                      |                       |
|                                       |             |               |                                                         |                                        | description: "channel type filter"         | required: false                |                                      |                       |
|                                       |             |               |                                                         |                                        | schema: type: "string"                      |                                |                                      |                       |
|                                       |             |               |                                                         |                                        | name: "itemType"                           | in: "query"                                |                                      |                       |
|                                       |             |               |                                                         |                                        | description: "item type filter"            | required: false                |                                      |                       |
|                                       |             |               |                                                         |                                        | schema: type: "string"                      |                                |                                      |                       |
|                                       |             |               |                                                         |                                        |                                          |                                |                                      |                       |
|                                       |             |               |                                                         |                                        |                                          |                                |                                      |                       |

### rules

| Endpoint    | Method | Tags       | Summary                                            | Operation ID | Parameters                                                                                                                                                           | Responses                                                                                                                               |
| ----------- | ------ | ---------- | -------------------------------------------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| /rules      | GET    | rules      | Get available rules, optionally filtered by tags and/or prefix. | getRules     | 0: name: "prefix"<br>   in: "query"<br>   schema: type: "string"<br> 1: name: "tags"<br>   in: "query"<br>   schema: type: "array"<br>   items: type: "string"<br> 2: name: "summary"<br>   in: "query"<br>   description: "summary fields only"<br>   schema: type: "boolean" | 200 - OK<br>content: application/json<br>schema: {…}<br>security: 0: oauth2: 0: "admin"<br>post<br>tags: 0: "rules"<br>summary: "Creates a rule."<br>operationId: "createRule"<br>requestBody: description: "rule data"<br>content: application/json<br>schema: $ref: "#/components/schemas/RuleDTO"<br>required: true<br>201 - Created<br>headers: Location: description: "Newly created Rule"<br>style: "simple"<br>400 - Creation of the rule is refused. Missing required parameter.<br>409 - Creation of the rule is refused. Rule with the same UID already exists.<br>security: 0: oauth2: 0: "admin" |
| /rules/{ruleUID}/enable | POST   | rules   | Sets the rule enabled status.          | enableRule   | 0: name: "ruleUID"<br>   in: "path"<br>   description: "ruleUID"<br>   required: true<br>   schema: type: "string" | 200 - OK<br>404 - Rule corresponding to the given UID does not found.<br>security: 0: oauth2: 0: "admin" |
|                         |        |         |                                      |              | 1: name: "enable"<br>   in: "body"<br>   description: "enable"<br>   required: true<br>   schema: type: "string"  |
| /rules/{ruleUID}/actions | GET    | rules   | Gets the rule actions | getRuleActions  | 0: name: "ruleUID"<br>   in: "path"<br>   description: "ruleUID"<br>   required: true<br>   schema: type: "string"  | 200 - OK<br>404 - Rule corresponding to the given UID does not found.<br>security: 0: oauth2: 0: "admin" |
|                         |        |         |                       |                 |                                                                                                       |                                                                                                      |
| /rules/{ruleUID}   | GET    | rules | Gets the rule corresponding to the given UID      | getRuleById  | 0: name: "ruleUID"<br>   in: "path"<br>   description: "ruleUID"<br>   required: true<br>   schema: type: "string" | 200 - OK<br>content: application/json<br>schema: {…}<br>404 - Rule not found<br>security: 0: oauth2: 0: "admin" |
|                    | PUT    | rules | Updates an existing rule corresponding to the given UID | updateRule   | 0: name: "ruleUID"<br>   in: "path"<br>   description: "ruleUID"<br>   required: true<br>   schema: type: "string"<br>requestBody: description: "rule data"<br>content: application/json<br>schema: $ref: "#/components/schemas/RuleDTO"<br>required: true | 200 - OK<br>404 - Rule corresponding to the given UID does not found.<br>security: 0: oauth2: 0: "admin" |
|                    | DELETE | rules | Removes an existing rule corresponding to the given UID | deleteRule   | 0: name: "ruleUID"<br>   in: "path"<br>   description: "ruleUID"<br>   required: true<br>   schema: type: "string" | 200 - OK<br>404 - Rule corresponding to the given UID does not found.<br>security: 0: oauth2: 0: "admin" |
| /rules/{ruleUID}/conditions | GET    | rules | Gets the rule conditions | getRuleConditions | 0: name: "ruleUID"<br>   in: "path"<br>   description: "ruleUID"<br>   required: true<br>   schema: type: "string" | 200 - OK<br>content: application/json<br>schema: {…}<br>404 - Rule corresponding to the given UID does not found.<br>security: 0: oauth2: 0: "admin" |
| /rules/{ruleUID}/config  | GET    | rules | Gets the rule configuration   | getRuleConfiguration | 0: name: "ruleUID"<br>   in: "path"<br>   description: "ruleUID"<br>   required: true<br>   schema: type: "string" | 200 - OK<br>content: application/json<br>schema: {…}<br>404 - Rule corresponding to the given UID does not found.<br>security: 0: oauth2: 0: "admin" |
| /rules/{ruleUID}/config  | PUT    | rules | Sets the rule configuration   | updateRuleConfiguration | 0: name: "ruleUID"<br>   in: "path"<br>   description: "ruleUID"<br>   required: true<br>   schema: type: "string" | 1: name: "config"<br>   in: "body"<br>   description: "config"<br>   required: true<br>   content: application/json<br>schema: type: "object"<br>additionalProperties: {…}<br>200 - OK<br>404 - Rule corresponding to the given UID does not found.<br>security: 0: oauth2: 0: "admin" |
| /rules/{ruleUID}/{moduleCategory}/{id}        | GET    | rules | Gets the rule's module corresponding to the given Category and ID. | getRuleModuleById  | 0: name: "ruleUID"<br>   in: "path"<br>   description: "ruleUID"<br>   required: true<br>   schema: type: "string"<br>1: name: "moduleCategory"<br>   in: "path"<br>   description: "moduleCategory"<br>   required: true<br>   schema: type: "string"<br>2: name: "id"<br>   in: "path"<br>   description: "id"<br>   required: true<br>   schema: type: "string" | 200 - OK<br>content: application/json<br>schema: $ref: "#/components/schemas/ModuleDTO"<br>404 - Rule corresponding to the given UID does not found or does not have a module with such Category and ID.<br>security: 0: oauth2: 0: "admin" |
| /rules/{ruleUID}/{moduleCategory}/{id}/config        | GET    | rules | Gets the module's configuration.  | getRuleModuleConfig | 0: name: "ruleUID"<br>   in: "path"<br>   description: "ruleUID"<br>   required: true<br>   schema: type: "string"<br>1: name: "moduleCategory"<br>   in: "path"<br>   description: "moduleCategory"<br>   required: true<br>   schema: type: "string"<br>2: name: "id"<br>   in: "path"<br>   description: "id"<br>   required: true<br>   schema: type: "string" | 200 - OK<br>content: application/json<br>schema: type: "string"<br>404 - Rule corresponding to the given UID does not found or does not have a module with such Category and ID.<br>security: 0: oauth2: 0: "admin" |
| /rules/{ruleUID}/{moduleCategory}/{id}/config/{param}         | GET    | rules | Gets the module's configuration parameter. | getRuleModuleConfigParameter | 0: name: "ruleUID"<br>   in: "path"<br>   description: "ruleUID"<br>   required: true<br>   schema: type: "string"<br>1: name: "moduleCategory"<br>   in: "path"<br>   description: "moduleCategory"<br>   required: true<br>   schema: type: "string"<br>2: name: "id"<br>   in: "path"<br>   description: "id"<br>   required: true<br>   schema: type: "string"<br>3: name: "param"<br>   in: "path"<br>   description: "param"<br>   required: true<br>   schema: type: "string" | 200 - OK<br>content: text/plain<br>schema: type: "string"<br>404 - Rule corresponding to the given UID does not found or does not have a module with such Category and ID.<br>security: 0: oauth2: 0: "admin" |
| /rules/{ruleUID}/{moduleCategory}/{id}/config/{param}         | PUT    | rules | Sets the module's configuration parameter value. | setRuleModuleConfigParameter | 0: name: "ruleUID"<br>   in: "path"<br>   description: "ruleUID"<br>   required: true<br>   schema: type: "string"<br>1: name: "moduleCategory"<br>   in: "path"<br>   description: "moduleCategory"<br>   required: true<br>   schema: type: "string"<br>2: name: "id"<br>   in: "path"<br>   description: "id"<br>   required: true<br>   schema: type: "string"<br>3: name: "param"<br>   in: "path"<br>   description: "param"<br>   required: true<br>   schema: type: "string"<br>requestBody: description: "value"<br>content: text/plain<br>schema: type: "string"<br>required: true | 200 - OK<br>404 - Rule corresponding to the given UID does not found or does not have a module with such Category and ID.<br>security: 0: oauth2: 0: "admin" |
| /rules/{ruleUID}/triggers                     | GET    | rules | Gets the rule triggers. | getRuleTriggers   | 0: name: "ruleUID"<br>   in: "path"<br>   description: "ruleUID"<br>   required: true<br>   schema: type: "string" | 200 - OK<br>content: application/json<br>schema: type: "array"<br>items: $ref: "#/components/schemas/TriggerDTO"<br>404 - Rule corresponding to the given UID does not found.<br>security: 0: oauth2: 0: "admin" |
| /rules/{ruleUID}/runnow     | POST   | rules | Executes actions of the rule. | runRuleNow_1   | 0: name: "ruleUID"<br>   in: "path"<br>   description: "ruleUID"<br>   required: true<br>   schema: type: "string" | description: "the context for running this rule"<br>content: application/json<br>schema: type: "object"<br>additionalProperties: type: "object" | 200 - OK<br>404 - Rule corresponding to the given UID does not found.<br>security: 0: oauth2: 0: "admin" |
| /rules/schedule/simulations         | GET    | rules | Simulates the executions of rules filtered by tag 'Schedule' within the given times. | getScheduleRuleSimulations | 0: name: "from"<br>   in: "query"<br>   description: "Start time of the simulated rule executions. Will default to the current time. [yyyy-MM-dd'T'HH:mm:ss.SSSZ]"<br>   schema: type: "string" | 200 - OK<br>content: application/json<br>schema: type: "array"<br>items: $ref: "#/components/schemas/RuleExecution"<br>400 - The max. simulation duration of 180 days is exceeded.<br>security: 0: oauth2: 0: "admin" |
|                                     |        |       |                                                   |                          | 1: name: "until"<br>   in: "query"<br>   description: "End time of the simulated rule executions. Will default to 30 days after the start time. Must be less than 180 days after the given start time. [yyyy-MM-dd'T'HH:mm:ss.SSSZ]"<br>   schema: type: "string" |

### services

| Endpoint                             | HTTP Method | Tags          | Summary                                                 | operationId                            | Parameters                                       | Request Body                   | Responses                            | Security              |
|---------------------------------------|-------------|---------------|---------------------------------------------------------|----------------------------------------|--------------------------------------------------|-------------------------------|--------------------------------------|-----------------------|
| /services/{serviceId}/config          | GET         | "services"    | "Get service configuration for given service ID."       | "getServiceConfig"                     | name: "serviceId"                           |                                | 200: "OK"                            | oauth2: 0: "admin"    |
|                                       |             |               |                                                         |                                        | in: "path"                                  |                                | 500: "Configuration can not be read due to internal error" |                       |
|                                       |             |               |                                                         |                                        |                                             |                                |                                      |                       |
| /services/{serviceId}/config                           | PUT         | "services"    | "Updates a service configuration for given service ID and returns the old configuration." | "updateServiceConfig"                 | name: "Accept-Language"                     |                                | 200: "OK"                            | oauth2: 0: "admin"    |
|                                       |             |               |                                                         |                                        | in: "header"                                |                                | 204: "No old configuration"        |                       |
|                                       |             |               |                                                         |                                        | name: "serviceId"                           | in: "path"                                  | 500: "Configuration can not be updated due to internal error" |                       |
|                                       |             |               |                                                         |                                        | description: "service ID"                   |                                |                                      |                       |
|                                       |             |               |                                                         |                                        | schema: type: "string"                      |                                |                                      |                       |
|                                       |             |               |                                                         |                                        |                                             |                                |                                      |                       |
|                                       |             |               |                                                         |                                        | name: "requestBody"                         | in: "body"                                  |                                      |                       |
|                                       |             |               |                                                         |                                        | content: application/json                   | schema: type: "object"          |                                      |                       |
|                                       |             |               |                                                         |                                        |                additionalProperties: {...}  |                                |                                      |                       |
| /services/{serviceId}/config                           | DELETE      | "services"    | "Deletes a service configuration for given service ID and returns the old configuration." | "deleteServiceConfig"                 | name: "serviceId"                           |                                | 200: "OK"                            | oauth2: 0: "admin"    |
|                                       |             |               |                                                         |                                        | in: "path"                                  |                                | 204: "No old configuration"        |                       |
|                                       |             |               |                                                         |                                        | description: "service ID"                   |                                | 500: "Configuration can not be deleted due to internal error" |                       |
|                                       |             |               |                                                         |                                        | schema: type: "string"                      |                                |                                      |                       |
|                                       |             |               |                                                         |                                        |                                             |                                |                                      |                       |
| /services                            | GET         | "services"    | "Get all configurable services."                       | "getServices"                          | name: "Accept-Language"                     |                                | 200: "OK"                            | oauth2: 0: "admin"    |
|                                       |             |               |                                                         |                                        | in: "header"                                |                                |                                      |                       |
| /services/{serviceId}                | GET         | "services"    | "Get configurable service for given service ID."       | "getServicesById"                     | name: "Accept-Language"                     |                                | 200: "OK"                            | oauth2: 0: "admin"    |
|                                       |             |               |                                                         |                                        | in: "header"                                |                                | 404: "Not found"                   |                       |
|                                       |             |               |                                                         |                                        | name: "serviceId"                           | in: "path"                                  |                                      |                       |
| /services/{serviceId}/contexts       | GET         | "services"    | "Get existing multiple context service configurations for the given factory PID." | "getServiceContext"                | name: "Accept-Language"                     |                                | 200: "OK"                            | oauth2: 0: "admin"    |
|                                       |             |               |                                                         |                                        | in: "header"                                |                                |                                      |                       |
|                                       |             |               |                                                         |                                        | name: "serviceId"                           | in: "path"                                  |                                      |                       |

### sitemaps

| Element               | Details                                  |
|-----------------------|------------------------------------------|
| Endpoint              | /sitemaps/events/subscribe              |
| HTTP Method           | POST                                     |
| Tags                  | "sitemaps"                               |
| Summary               | "Creates a sitemap event subscription."  |
| operationId           | "createSitemapEventSubscription"         |
| Responses             |                                          |
|     201: "Created"    | Subscription created.                    |
|     503:             | Subscriptions limit reached.             |

| Element                  | Details                                                    |
|--------------------------|------------------------------------------------------------|
| Endpoint                 | /sitemaps/{sitemapname}/{pageid}                           |
| HTTP Method              | GET                                                        |
| Tags                     | "sitemaps"                                                 |
| Summary                  | "Polls the data for a sitemap."                            |
| operationId              | "pollDataForSitemap"                                       |
| Parameters               |                                                            |
|     Accept-Language     | Header                                                     |
|     sitemapname         | Path - sitemap name                                        |
|     pageid              | Path - page id                                             |
|     subscriptionid      | Query - subscriptionid                                     |
|     includeHidden       | Query - include hidden widgets (boolean)                  |
| Responses                |                                                            |
|     200: "OK"           | Content - application/json                                 |
|     400:                | Invalid subscription id has been provided.                |
|     404:                | Sitemap with requested name does not exist or page does   |
|                          | not exist, or page refers to a non-linkable widget.        |

| Element                  | Details                                                    |
|--------------------------|------------------------------------------------------------|
| Endpoint                 | /sitemaps/{sitemapname}                                    |
| HTTP Method              | GET                                                        |
| Tags                     | "sitemaps"                                                 |
| Summary                  | "Get sitemap by name."                                     |
| operationId              | "getSitemapByName"                                         |
| Parameters               |                                                            |
|     Accept-Language     | Header                                                     |
|     sitemapname         | Path - sitemap name                                        |
|     type                | Query - type                                               |
|     jsoncallback        | Query - jsoncallback (default: "callback")                |
|     includeHidden       | Query - include hidden widgets (boolean)                  |
| Responses                |                                                            |
|     200: "OK"           | Content - application/json                                 |
|     Schema              | $ref - "#/components/schemas/SitemapDTO"                   |

| Element                  | Details                                                    |
|--------------------------|------------------------------------------------------------|
| Endpoint                 | /sitemaps/events/{subscriptionid}                          |
| HTTP Method              | GET                                                        |
| Tags                     | "sitemaps"                                                 |
| Summary                  | "Get sitemap events."                                      |
| operationId              | "getSitemapEvents"                                         |
| Parameters               |                                                            |
|     subscriptionid      | Path - subscription id                                     |
|     sitemap             | Query - sitemap name                                       |
|     pageid              | Query - page id                                            |
| Responses                |                                                            |
|     200: "OK"           | Content - application/json                                 |
|     400: "Page not linked to the subscription."    |                                                            |
|     404: "Subscription not found."             |                                                            |

| Element                  | Details                                                    |
|--------------------------|------------------------------------------------------------|
| Endpoint                 | /sitemaps                                                  |
| HTTP Method              | GET                                                        |
| Tags                     | "sitemaps"                                                 |
| Summary                  | "Get all available sitemaps."                             |
| operationId              | "getSitemaps"                                              |
| Responses                |                                                            |
|     200: "OK"           | Content - application/json                                 |
|                          | Schema - type: array                                       |
|                          |          items: $ref: "#/components/schemas/SitemapDTO"    |

### systeminfo

| Element        | Details                                        |
|----------------|------------------------------------------------|
| Endpoint       | /systeminfo                                    |
| HTTP Method    | GET                                            |
| Tags           | "systeminfo"                                   |
| Summary        | "Gets information about the system."           |
| operationId    | "getSystemInformation"                         |
| Responses      |                                                |
|     200: "OK"  | OK                                             |
| Content        | application/json                               |
| Schema         | $ref	"#/components/schemas/SystemInfoBean"                                          |
| Security       |                                                |
|     oauth2:    | "admin"                                        |


### templates

| Endpoint             | Method | Tags       | Summary                           | Operation ID   | Parameters                                                                                                        | Responses                                                                                                  |
| -------------------- | ------ | ---------- | --------------------------------- | -------------- | ----------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| /templates           | GET    | templates  | Get all available templates.      | getTemplates   | 0: name: "Accept-Language"<br>   in: "header"<br>   description: "language"<br>   schema: type: "string"         | 200 - OK<br>content: application/json<br>schema: type: "array"<br>items: $ref: "#/components/schemas/Template" |
| /templates/{templateUID} | GET    | templates  | Gets a template corresponding to the given UID. | getTemplateById  | 0: name: "Accept-Language"<br>   in: "header"<br>   description: "language"<br>   schema: type: "string"<br>1: name: "templateUID"<br>   in: "path"<br>   description: "templateUID"<br>   required: true<br>   schema: type: "string" | 200 - OK<br>content: application/json<br>schema: $ref: "#/components/schemas/Template"<br>404 - Template corresponding to the given UID does not found. |

### things

| Element                           | Details                                     | Further                        |
|-----------------------------------|---------------------------------------------|--------------------------------|
| Endpoint                          | /things                                     |                                |
| HTTP Method                       | GET                                         |                                |
| Tags                              | "things"                                    |                                |
| Summary                           | "Get all available things."                |                                |
| operationId                       | "getThings"                                 |                                |
| Parameters                        |                                             |                                |
|                                   | name: "Accept-Language"                    | in: "header"                   |
|                                   |       description: "language"              | required: false                |
|                                   |       schema: type: "string"               |                                |
|                                   |                                             |                                |
|                                   | name: "summary"                            | in: "query"                    |
|                                   |       description: "summary fields only"   | required: false                |
|                                   |       schema: type: "boolean"              |                                |
| Responses                         |                                             |                                |
|       200: "OK"                   | content: application/json                  | schema: {...}                  |
| Security                          |                                             |                                |
|       oauth2:                     |                                             |                                |
|          0: "admin"               |                                             |                                |
|                                   |                                             |                                |
| Endpoint                          | /things                                     |                                |
| HTTP Method                       | POST                                        |                                |
| Tags                              | "things"                                    |                                |
| Summary                           | "Creates a new thing and adds it to the registry." |                            |
| operationId                       | "createThingInRegistry"                    |                                |
| Parameters                        |                                             |                                |
|                                   | name: "Accept-Language"                    | in: "header"                   |
|                                   |       description: "language"              | required: false                |
|                                   |       schema: type: "string"               |                                |
|                                   |                                             |                                |
| Request Body                      |                                             |                                |
|       description: "thing data"   | content: application/json                  | schema: $ref: "#/components/schemas/ThingDTO" |
|       required: true              |                                             |                                |
| Responses                         |                                             |                                |
|       201: "Created"              | content: */*                               | schema: {...}                  |
|       400: "A uid must be provided, if no binding can create a thing of this type." |          |                                |
|       409: "A thing with the same uid already exists." |                              |                                |
| Security                          |                                             |                                |
|       oauth2:                     |                                             |                                |
|          0: "admin"               |                                             |                                |

| Element                           | Details                                    | Further                        |
|-----------------------------------|--------------------------------------------|--------------------------------|
| Endpoint                          | /things/{thingUID}                        |                                |
| HTTP Method                       | GET                                        |                                |
| Tags                              | "things"                                   |                                |
| Summary                           | "Gets thing by UID."                      |                                |
| operationId                       | "getThingById"                            |                                |
| Parameters                        |                                            |                                |
|                                   | name: "Accept-Language"                   | in: "header"                   |
|                                   |       description: "language"             | required: false                |
|                                   |       schema: type: "string"              |                                |
|                                   |                                            |                                |
|                                   | name: "thingUID"                          | in: "path"                     |
|                                   |       description: "thingUID"             | required: true                 |
|                                   |       schema: type: "string"              |                                |
| Responses                         |                                            |                                |
|       200: "OK"                   | content: application/json                 | schema: {...}                  |
|       404: "Thing not found."     |                                            |                                |
| Security                          |                                            |                                |
|       oauth2:                     |                                            |                                |
|          0: "admin"               |                                            |                                |

| Element                           | Details                                      | Further                        |
|-----------------------------------|----------------------------------------------|--------------------------------|
| Endpoint                          | /things/{thingUID}                          |                                |
| HTTP Method                       | GET                                          |                                |
| Tags                              | "things"                                     |                                |
| Summary                           | "Gets thing by UID."                        |                                |
| operationId                       | "getThingById"                               |                                |
| Parameters                        |                                              |                                |
|                                   | name: "Accept-Language"                     | in: "header"                   |
|                                   |       description: "language"               | required: false                |
|                                   |       schema: type: "string"                |                                |
|                                   |                                              |                                |
|                                   | name: "thingUID"                            | in: "path"                     |
|                                   |       description: "thingUID"               | required: true                 |
|                                   |       schema: type: "string"                |                                |
| Responses                         |                                              |                                |
|       200: "OK"                   | content: application/json                   | schema: {...}                  |
|       404: "Thing not found."     |                                              |                                |
| Security                          |                                              |                                |
|       oauth2:                     |                                              |                                |
|          0: "admin"               |                                              |                                |
|                                   |                                              |                                |
| Endpoint                          | /things/{thingUID}                          |                                |
| HTTP Method                       | PUT                                          |                                |
| Tags                              | "things"                                     |                                |
| Summary                           | "Updates a thing."                          |                                |
| operationId                       | "updateThing"                                |                                |
| Parameters                        |                                              |                                |
|                                   | name: "Accept-Language"                     | in: "header"                   |
|                                   |       description: "language"               | required: false                |
|                                   |       schema: type: "string"                |                                |
|                                   |                                              |                                |
|                                   | name: "thingUID"                            | in: "path"                     |
|                                   |       description: "thingUID"               | required: true                 |
|                                   |       schema: type: "string"                |                                |
| Request Body                      |                                              |                                |
|       description: "thing"        | content: application/json                   | schema: $ref: "#/components/schemas/ThingDTO" |
|       required: true              |                                              |                                |
| Responses                         |                                              |                                |
|       200: "OK"                   | content: */*                                | schema: {...}                  |
|       404: "Thing not found."     |                                              |                                |
|       409: "Thing could not be updated as it is not editable." |                          |                                |
| Security                          |                                              |                                |
|       oauth2:                     |                                              |                                |
|          0: "admin"               |                                              |                                |
|                                   |                                              |                                |
| Endpoint                          | /things/{thingUID}                          |                                |
| HTTP Method                       | DELETE                                       |                                |
| Tags                              | "things"                                     |                                |
| Summary                           | "Removes a thing from the registry. Set 'force' to __true__ if you want the thing to be removed immediately." | |
| operationId                       | "removeThingById"                            |                                |
| Parameters                        |                                              |                                |
|                                   | name: "Accept-Language"                     | in: "header"                   |
|                                   |       description: "language"               | required: false                |
|                                   |       schema: type: "string"                |                                |
|                                   |                                              |                                |
|                                   | name: "thingUID"                            | in: "path"                     |
|                                   |       description: "thingUID"               | required: true                 |
|                                   |       schema: type: "string"                |                                |
|                                   |                                              |                                |
|                                   | name: "force"                               | in: "query"                    |
|                                   |       description: "force"                  | required: false                |
|                                   |       schema: type: "boolean"               | default: false                 |
| Responses                         |                                              |                                |
|       200: "OK, was deleted."     | content: application/json                   | schema: {...}                  |
|       202: "ACCEPTED for asynchronous deletion." |                                      |                                |
|       404: "Thing not found."     |                                              |                                |
|       409: "Thing could not be deleted because it's not editable." |                        |                                |
| Security                          |                                              |                                |
|       oauth2:                     |                                              |                                |
|          0: "admin"               |                                              |                                |

| Element                           | Details                                      | Further                        |
|-----------------------------------|----------------------------------------------|--------------------------------|
| Endpoint                          | /things/{thingUID}/config/status            |                                |
| HTTP Method                       | GET                                          |                                |
| Tags                              | "things"                                     |                                |
| Summary                           | "Gets thing config status."                 |                                |
| operationId                       | "getThingConfigStatus"                      |                                |
| Parameters                        |                                              |                                |
|                                   | name: "Accept-Language"                     | in: "header"                   |
|                                   |       description: "language"               | required: false                |
|                                   |       schema: type: "string"                |                                |
|                                   |                                              |                                |
|                                   | name: "thingUID"                            | in: "path"                     |
|                                   |       description: "thing"                  | required: true                 |
|                                   |       schema: type: "string"                |                                |
| Responses                         |                                              |                                |
|       200: "OK"                   | content: application/json                   | schema: {...}                  |
|       404: "Thing not found."     |                                              |                                |
| Security                          |                                              |                                |
|       oauth2:                     |                                              |                                |
|          0: "admin"               |                                              |                                |

| Element                           | Details                                      | Further                        |
|-----------------------------------|----------------------------------------------|--------------------------------|
| Endpoint                          | /things/{thingUID}/firmware/status          |                                |
| HTTP Method                       | GET                                          |                                |
| Tags                              | "things"                                     |                                |
| Summary                           | "Gets thing's firmware status."             |                                |
| operationId                       | "getThingFirmwareStatus"                    |                                |
| Parameters                        |                                              |                                |
|                                   | name: "Accept-Language"                     | in: "header"                   |
|                                   |       description: "language"               | required: false                |
|                                   |       schema: type: "string"                |                                |
|                                   |                                              |                                |
|                                   | name: "thingUID"                            | in: "path"                     |
|                                   |       description: "thing"                  | required: true                 |
|                                   |       schema: type: "string"                |                                |
| Responses                         |                                              |                                |
|       200: "OK"                   | content: */*                                 | schema: {...}                  |
|       204: "No firmware status provided by this Thing." |                                |
| Security                          |                                              |                                |
|       oauth2:                     |                                              |                                |
|          0: "admin"               |                                              |                                |

| Element                           | Details                                            | Further                        |
|-----------------------------------|----------------------------------------------------|--------------------------------|
| Endpoint                          | /things/{thingUID}/firmwares                      |                                |
| HTTP Method                       | GET                                                |                                |
| Tags                              | "things"                                           |                                |
| Summary                           | "Get all available firmwares for provided thing UID" |                            |
| operationId                       | "getAvailableFirmwaresForThing"                   |                                |
| Parameters                        |                                                    |                                |
|                                   | name: "thingUID"                                  | in: "path"                     |
|                                   |       description: "thingUID"                     | required: true                 |
|                                   |       schema: type: "string"                      |                                |
|                                   |                                                    |                                |
|                                   | name: "Accept-Language"                           | in: "header"                   |
|                                   |       description: "language"                     | required: false                |
|                                   |       schema: type: "string"                      |                                |
| Responses                         |                                                    |                                |
|       200: "OK"                   | content: application/json                         | schema: {...}                  |
|       204: "No firmwares found."  |                                                    |                                |
| Security                          |                                                    |                                |
|       oauth2:                     |                                                    |                                |
|          0: "admin"               |                                                    |                                |

| Element                           | Details                          | Further                        |
|-----------------------------------|----------------------------------|--------------------------------|
| Endpoint                          | /things/{thingUID}/status        |                                |
| HTTP Method                       | GET                              |                                |
| Tags                              | "things"                         |                                |
| Summary                           | "Gets thing status."             |                                |
| operationId                       | "getThingStatus"                 |                                |
| Parameters                        |                                  |                                |
|                                   | name: "Accept-Language"         | in: "header"                   |
|                                   |       description: "language"    | required: false                |
|                                   |       schema: type: "string"     |                                |
|                                   |                                  |                                |
|                                   | name: "thingUID"                | in: "path"                     |
|                                   |       description: "thing"       | required: true                 |
|                                   |       schema: type: "string"     |                                |
| Responses                         |                                  |                                |
|       200: "OK"                   | content: application/json       | schema: {...}                  |
|       404: "Thing not found."     |                                  |                                |
| Security                          |                                  |                                |
|       oauth2:                     |                                  |                                |
|          0: "admin"               |                                  |                                |

| Element                           | Details                           | Further                        |
|-----------------------------------|-----------------------------------|--------------------------------|
| Endpoint                          | /things/{thingUID}/enable         |                                |
| HTTP Method                       | PUT                               |                                |
| Tags                              | "things"                          |                                |
| Summary                           | "Sets the thing enabled status."  |                                |
| operationId                       | "enableThing"                     |                                |
| Parameters                        |                                   |                                |
|                                   | name: "Accept-Language"          | in: "header"                   |
|                                   |       description: "language"     | required: false                |
|                                   |       schema: type: "string"      |                                |
|                                   |                                   |                                |
|                                   | name: "thingUID"                 | in: "path"                     |
|                                   |       description: "thing"        | required: true                 |
|                                   |       schema: type: "string"      |                                |
| Request Body                      |                                   |                                |
|                                   | description: "enabled"           |                                |
|                                   | content: text/plain              | schema: type: "string"         |
| Responses                         |                                   |                                |
|       200: "OK"                   | content: */*                     | schema: {...}                  |
|       404: "Thing not found."     |                                   |                                |
| Security                          |                                   |                                |
|       oauth2:                     |                                   |                                |
|          0: "admin"               |                                   |                                |

| Element                           | Details                                 | Further                        |
|-----------------------------------|-----------------------------------------|--------------------------------|
| Endpoint                          | /things/{thingUID}/config              |                                |
| HTTP Method                       | PUT                                     |                                |
| Tags                              | "things"                                |                                |
| Summary                           | "Updates thing's configuration."       |                                |
| operationId                       | "updateThingConfig"                    |                                |
| Parameters                        |                                         |                                |
|                                   | name: "Accept-Language"                | in: "header"                   |
|                                   |       description: "language"           | required: false                |
|                                   |       schema: type: "string"            |                                |
|                                   |                                         |                                |
|                                   | name: "thingUID"                       | in: "path"                     |
|                                   |       description: "thing"              | required: true                 |
|                                   |       schema: type: "string"            |                                |
| Request Body                      |                                         |                                |
|                                   | description: "configuration parameters" |                                |
|                                   | content: application/json              | schema: type: "object"         |
|                                   |         additionalProperties: {...}    |                                |
| Responses                         |                                         |                                |
|       200: "OK"                   | content: */*                           | schema: {...}                  |
|       400: "Configuration of the thing is not valid." |                         |                                |
|       404: "Thing not found"      |                                         |                                |
|       409: "Thing could not be updated as it is not editable." |                 |                                |
| Security                          |                                         |                                |
|       oauth2:                     |                                         |                                |
|          0: "admin"               |                                         |                                |

| Element                           | Details                                 | Further                        |
|-----------------------------------|-----------------------------------------|--------------------------------|
| Endpoint                          | /things/{thingUID}/firmware/{firmwareVersion} |                           |
| HTTP Method                       | PUT                                     |                                |
| Tags                              | "things"                                |                                |
| Summary                           | "Update thing firmware."               |                                |
| operationId                       | "updateThingFirmware"                  |                                |
| Parameters                        |                                         |                                |
|                                   | name: "Accept-Language"                | in: "header"                   |
|                                   |       description: "language"           | required: false                |
|                                   |       schema: type: "string"            |                                |
|                                   |                                         |                                |
|                                   | name: "thingUID"                       | in: "path"                     |
|                                   |       description: "thing"              | required: true                 |
|                                   |       schema: type: "string"            |                                |
|                                   |                                         |                                |
|                                   | name: "firmwareVersion"                | in: "path"                     |
|                                   |       description: "version"            | required: true                 |
|                                   |       schema: type: "string"            |                                |
| Responses                         |                                         |                                |
|       200: "OK"                   |                                         |                                |
|       400: "Firmware update preconditions not satisfied." |                    |                                |
|       404: "Thing not found."     |                                         |                                |
| Security                          |                                         |                                |
|       oauth2:                     |                                         |                                |
|          0: "admin"               |                                         |                                |

### thing-types

| Element          | Details                                                           |
|------------------|-------------------------------------------------------------------|
| Endpoint         | /thing-types                                                      |
| HTTP Method      | GET                                                               |
| Tags             | "thing-types"                                                     |
| Summary          | "Gets all available thing types without config description, channels and properties." |
| operationId      | "getThingTypes"                                                   |
| Parameters       |                                                                   |
|                  | name: "Accept-Language"                                          |
|                  | in: "header"                                                     |
|                  | description: "language"                                          |
|                  | schema:                                                           |
|                  |     type: "string"                                               |
|                  |                                                                   |
|                  | name: "bindingId"                                                |
|                  | in: "query"                                                      |
|                  | description: "filter by binding Id"                               |
|                  | schema:                                                           |
|                  |     type: "string"                                               |
| Responses        |                                                                   |
|     200: "OK"   |                                                                   |
| Content          | application/json                                                  |
| Schema           | uniqueItems: true                                                 |
|                  | type: "array"                                                    |
|                  | items: $ref: "#/components/schemas/StrippedThingTypeDTO"          |

| Element          | Details                                                                          |
|------------------|----------------------------------------------------------------------------------|
| Endpoint         | /thing-types/{thingTypeUID}                                                      |
| HTTP Method      | GET                                                                              |
| Tags             | "thing-types"                                                                    |
| Summary          | "Gets thing type by UID."                                                        |
| operationId      | "getThingTypeById"                                                               |
| Parameters       |                                                                                  |
|                  | name: "thingTypeUID"                                                            |
|                  | in: "path"                                                                      |
|                  | description: "thingTypeUID"                                                     |
|                  | required: true                                                                   |
|                  | schema:                                                                          |
|                  |     type: "string"                                                              |
|                  |                                                                                  |
|                  | name: "Accept-Language"                                                        |
|                  | in: "header"                                                                    |
|                  | description: "language"                                                         |
|                  | schema:                                                                          |
|                  |     type: "string"                                                              |
| Responses        |                                                                                  |
|     200: "OK"    | Thing type with provided thingTypeUID does not exist.                            |
| Content          | application/json                                                                 |
| Schema           | {…}                                                                              |
|     404: "Not found" | No content                                                                     |


### transformations

| Element                         | Details                                                                            |
|---------------------------------|------------------------------------------------------------------------------------|
| Endpoint                        | /transformations/{uid}                                                            |
| HTTP Method                     | GET                                                                                |
| Tags                            | "transformations"                                                                 |
| Summary                         | "Get a single transformation"                                                     |
| operationId                     | "getTransformation"                                                               |
| Parameters                      |                                                                                    |
|     name: "uid"                |                                                                                    |
|     in: "path"                 |                                                                                    |
|     description: "Transformation UID" |                                                                                    |
|     required: true             |                                                                                    |
|     schema:                     |                                                                                    |
|         type: "string"          |                                                                                    |
| Responses                       |                                                                                    |
|     200: "OK"                  |                                                                                    |
|     content:                   |                                                                                    |
|         application/json        |                                                                                    |
|     schema: {…}                |                                                                                    |
|     404: "Not found"           |                                                                                    |
| Security                        |                                                                                    |
|     0: oauth2                  |                                                                                    |
|         0: "admin"             |                                                                                    |
| Endpoint                        | /transformations/{uid}                                                            |
| HTTP Method                     | PUT                                                                                |
| Tags                            | "transformations"                                                                 |
| Summary                         | "Put a single transformation"                                                     |
| operationId                     | "putTransformation"                                                               |
| Parameters                      |                                                                                    |
|     name: "uid"                |                                                                                    |
|     in: "path"                 |                                                                                    |
|     description: "Transformation UID" |                                                                                    |
|     required: true             |                                                                                    |
|     schema:                     |                                                                                    |
|         type: "string"          |                                                                                    |
| Request Body                    |                                                                                    |
|     description: "transformation" |                                                                                    |
|     content:                   |                                                                                    |
|         application/json        |                                                                                    |
|     schema:                     |                                                                                    |
|         $ref: "#/components/schemas/TransformationDTO" |                                                                                    |
|     required: true             |                                                                                    |
| Responses                       |                                                                                    |
|     200: "OK"                  |                                                                                    |
|     400: "Bad Request (content missing or invalid)" |                                                                                    |
|     405: "Transformation not editable" |                                                                                    |
| Security                        |                                                                                    |
|     0: oauth2                  |                                                                                    |
|         0: "admin"             |                                                                                    |
| Endpoint                        | /transformations/{uid}                                                            |
| HTTP Method                     | DELETE                                                                             |
| Tags                            | "transformations"                                                                 |
| Summary                         | "Get a single transformation"                                                     |
| operationId                     | "deleteTransformation"                                                            |
| Parameters                      |                                                                                    |
|     name: "uid"                |                                                                                    |
|     in: "path"                 |                                                                                    |
|     description: "Transformation UID" |                                                                                    |
|     required: true             |                                                                                    |
|     schema:                     |                                                                                    |
|         type: "string"          |                                                                                    |
| Responses                       |                                                                                    |
|     200: "OK"                  |                                                                                    |
|     404: "UID not found"       |                                                                                    |
|     405: "Transformation not editable" |                                                                                    |
| Security                        |                                                                                    |
|     0: oauth2                  |                                                                                    |
|         0: "admin"             |                                                                                    |

| Element            | Details                                               |
|--------------------|-------------------------------------------------------|
| Endpoint           | /transformations                                      |
| HTTP Method        | GET                                                   |
| Tags               | "transformations"                                    |
| Summary            | "Get a list of all transformations"                  |
| operationId        | "getTransformations"                                 |
| Responses          |                                                       |
|     200: "OK"     | Description: "OK"                                    |
|     content:      |                                                       |
|         application/json |                                    |
|     schema:       |                                                       |
|         type: "array"    |                                    |
|         items:     |                                                       |
|             $ref: "#/components/schemas/TransformationDTO" |  |
| Security           |                                                       |
|     0: oauth2     |                                                       |
|         0: "admin" |                                                       |

### ui

| Endpoint                          | HTTP Method | Tags | Summary                                                      | Operation ID                           | Parameters                                     | Responses                                    | Security              |
|-----------------------------------|-------------|------|--------------------------------------------------------------|----------------------------------------|-----------------------------------------------|----------------------------------------------|-----------------------|
| /ui/components/{namespace}        | GET         | ui   | Get all registered UI components in the specified namespace. | getRegisteredUIComponentsInNamespace | - `namespace` (in path, required, type: string) <br> - `summary` (in query, type: boolean, description: summary fields only) | 200 - OK <br> Content: application/json <br> Schema: type: array, items: $ref: "#/components/schemas/RootUIComponent" | oauth2 - admin       |
| /ui/components/{namespace}        | POST        | ui   | Add a UI component in the specified namespace.               | addUIComponentToNamespace            | - `namespace` (in path, required, type: string) <br> - Request Body: Content: application/json <br> Schema: $ref: "#/components/schemas/RootUIComponent" | 200 - OK <br> Content: application/json <br> Schema: $ref: "#/components/schemas/RootUIComponent"   | oauth2 - admin       |
| /ui/components/{namespace}/{componentUID}        | GET         | ui   | Get a specific UI component in the specified namespace. | getUIComponentInNamespace       | - `namespace` (in path, required, type: string) <br> - `componentUID` (in path, required, type: string) | 200 - OK <br> Content: application/json <br> Schema: {…}       | oauth2 - admin       |
| /ui/components/{namespace}/{componentUID}        | PUT         | ui   | Update a specific UI component in the specified namespace. | updateUIComponentInNamespace    | - `namespace` (in path, required, type: string) <br> - `componentUID` (in path, required, type: string) <br> Request Body: Content: application/json <br> Schema: $ref: "#/components/schemas/RootUIComponent" | 200 - OK <br> Content: application/json <br> Schema: {…}       | oauth2 - admin       |
| /ui/components/{namespace}/{componentUID}        | DELETE      | ui   | Remove a specific UI component in the specified namespace. | removeUIComponentFromNamespace | - `namespace` (in path, required, type: string) <br> - `componentUID` (in path, required, type: string) | 200 - OK                                                        | oauth2 - admin       |
| /ui/tiles     | GET         | ui   | Get all registered UI tiles.   | getUITiles   | 200 - OK <br> Content: application/json <br> Schema: type: "array" <br> Items: $ref: "#/components/schemas/TileDTO" |


### uuid

| Endpoint | Method | Tags  | Summary              | Operation ID | Responses                                |
| -------- | ------ | ----- | -------------------- | ------------ | ---------------------------------------- |
| /uuid    | GET    | uuid | A unified unique id. | getUUID      | 200 - OK<br>content: text/plain<br>schema: type: "string" |


### voice

| Endpoint              | HTTP Method | Tags   | Summary               | Operation ID    | Responses                                                                                                      |
|-----------------------|-------------|--------|-----------------------|-----------------|----------------------------------------------------------------------------------------------------------------|
| /voice/defaultvoice   | GET         | voice  | Gets the default voice. | getDefaultVoice | 200 - OK <br> Content: application/json <br> Schema: $ref: "#/components/schemas/VoiceDTO" <br> 404 - No default voice was found. |
| /voice/interpreters/{id}             | GET         | voice  | Gets a single interpreter. | getVoiceInterpreterByUID  | - name: Accept-Language <br> in: header <br> description: language <br> schema: type: string <br> - name: id <br> in: path <br> description: interpreter id <br> required: true <br> schema: type: string | 200 - OK <br> Content: application/json <br> Schema: type: array <br> items: $ref: "#/components/schemas/HumanLanguageInterpreterDTO" <br> 404 - Interpreter not found |
| /voice/interpreters                      | GET    | voice | Get the list of all interpreters.                   | getVoiceInterpreters                   | Accept-Language: header (language)             | 200 - OK<br>Content: application/json<br>Schema: {...} |
| /voice/interpreters                      | POST   | voice | Sends a text to the default human language interpreter. | interpretTextByDefaultInterpreter    | Accept-Language: header (language)<br>text to interpret: body (text/plain) (required) | 200 - OK<br>400 - interpretation exception occurs<br>404 - No human language interpreter was found. |
| /voice/voices  | GET    | voice | Get the list of all voices. | getVoices    | 200 - OK<br>Content: application/json<br>Schema: {type: "array", items: $ref("#/components/schemas/VoiceDTO")} |
| /voice/interpreters/{ids}       | POST   | voice | Sends a text to a given human language interpreter(s). | interpretText   | - name: Accept-Language<br>  in: header<br>  description: language<br>  schema: {type: "string"}<br>- name: ids<br>  in: path<br>  description: comma separated list of interpreter ids<br>  required: true<br>  schema: {type: "array", items: {type: "string"}} | Request Body:<br>- description: text to interpret<br>  content: text/plain<br>  schema: {type: "string"}<br>  required: true | 200 - OK<br>Content: application/json<br>Schema: {type: "object"}<br>400 - interpretation exception occurs<br>Content: application/json<br>Schema: {type: "object"}<br>404 - No human language interpreter was found.<br>Content: application/json<br>Schema: {type: "object"} |
| /voice/listenandanswer | POST   | voice | Executes a simple dialog sequence without keyword spotting for a given audio source. | listenAndAnswer | - name: Accept-Language<br>  in: header<br>  description: language<br>  schema: {type: "string"}<br>- name: sourceId<br>  in: query<br>  description: source ID<br>  schema: {type: "string"}<br>- name: sttId<br>  in: query<br>  description: Speech-to-Text ID<br>  schema: {type: "string"}<br>- name: ttsId<br>  in: query<br>  description: Text-to-Speech ID<br>  schema: {type: "string"}<br>- name: voiceId<br>  in: query<br>  description: voice ID<br>  schema: {type: "string"}<br>- name: hliIds<br>  in: query<br>  description: interpreter IDs<br>  schema: {type: "array", items: {type: "string"}}<br>- name: sinkId<br>  in: query<br>  description: audio sink ID<br>  schema: {type: "string"}<br>- name: listeningItem<br>  in: query<br>  description: listening item<br>  schema: {type: "string"} | 200 - OK<br>Content: application/json<br>Schema: {type: "object"}<br>400 - Services are missing or language is not supported by services or dialog processing is already started for the audio source.<br>Content: application/json<br>Schema: {type: "object"}<br>404 - One of the given ids is wrong.<br>Content: application/json<br>Schema: {type: "object"} |
| /voice/say  | POST   | voice | Speaks a given text with a given voice through the given audio sink. | textToSpeech   | - name: voiceid<br>  in: query<br>  description: voice id<br>  schema: {type: "string"}<br>- name: sinkid<br>  in: query<br>  description: audio sink id<br>  schema: {type: "string"} | Content: text/plain<br>Schema: {type: "string"}<br>Required: true                              | 200 - OK<br>Content: application/json<br>Schema: {type: "object"} |
| /voice/dialog/start  | POST   | voice | Start dialog processing for a given audio source.          | startDialog  | - name: Accept-Language<br>  in: header<br>  description: language<br>  schema: {type: "string"}<br>- name: sourceId<br>  in: query<br>  description: source ID<br>  schema: {type: "string"}<br>... | 200 - OK<br>400 - Services are missing or language is not supported by services or dialog processing is already started for the audio source.<br>404 - One of the given ids is wrong. |
| /voice/dialog/stop | POST   | voice | Stop dialog processing for a given audio source. | stopDialog   | - name: sourceId<br>  in: query<br>  description: source ID<br>  schema: {type: "string"} | 200 - OK<br>400 - No dialog processing is started for the audio source.<br>404 - No audio source was found. |
