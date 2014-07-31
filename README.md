# node-eventbrite

A node.js library for the eventbrite API(further details: https://developer.eventbrite.com)

_node-eventbrite_ exposes the following features of the eventbrite API to your node.js application:

**Version v3**
  * user-details


## Installation

Installing using npm (node package manager):

    npm install node-eventbrite

If you don't have npm installed or don't want to use it:

    cd ~/.node_libraries
    git clone git@github.com:Datahero/node-eventbrite.git

Please note that parts of _node-eventbrite_ depend on [request](http://github.com/mikeal/request) by [Mikeal Rogers](http://github.com/mikeal). This library needs to be installed for the API to work. Additionally [node-querystring](http://github.com/visionmedia/node-querystring) is required. If you are using npm all dependencies should be automagically resolved for you.

## Usage

Information on how to use the eventbrite APIs can be found below. Further information on the API methods available can be found at [https://developer.eventbrite.com](https://developer.eventbrite.com). You can also find further information on how to obtain an API key, and/or OAuth2 in your eventbrite account and much more on the eventbrite API pages.

### eventbrite API

_eventbriteAPI_ takes an options object, The only required option for version3 of the api is an oAuth token.

http://developer.eventbrite.com/docs/auth/
> All API requests must be authenticated with a valid OAuth token. Tokens are tied to user accounts; if you’re just using the API for a single user or organizer, then follow ‘Personal Tokens’ if you’re using the API for many Eventbrite users, then follow ‘OAuth Token Flow’.
which you can find in your eventbrite Account. The second argument is an options object which can contain the following options:

**required options:**
* `token`

**available options**
* `version` The API version to use. Defaults to v3.
* `userAgent` Custom User-Agent description to use in the request header.
* `contentType`  defaults to `application/json` and currently the api only supports json

The callback function for each API method gets two arguments, an error and results object.

The error object is null when no error occured. The results object contains all information retrieved as long as no error occurred.

Example:

```javascript
var eventbriteAPI = require('eventbrite');

var token = 'a users eventbrite API token';

try {
    var api = eventbriteAPI({
      token: token,
      version : 'v3'
    });
} catch (error) {
    console.log(error.message); // the options are missing, this function throws an error.
}

api.owned_events({ user_id: 30 }, function (error, data) {
    if (error)
        console.log(error.message);
    else
        console.log(JSON.stringify(data)); // Do something with your data!
});

```


#### Events
[http://developer.eventbrite.com/docs/event-search/](Event Search) TODO

[http://developer.eventbrite.com/docs/event-categories/](Event Categories) TODO

[http://developer.eventbrite.com/docs/event-details/](Event Details)

[http://developer.eventbrite.com/docs/event-attendees](Event Attendees)

[http://developer.eventbrite.com/docs/event-attendees-detail](Event Attendees’ Detail)

[http://developer.eventbrite.com/docs/event-orders](Event Orders)

[http://developer.eventbrite.com/docs/event-discounts](Event Discounts)

[http://developer.eventbrite.com/docs/event-access-codes](Event Access Codes)

[http://developer.eventbrite.com/docs/event-transfers](Event Transfers)

[http://developer.eventbrite.com/docs/event-teams](Event Teams)

[http://developer.eventbrite.com/docs/event-teams-details](Event Teams’ Details)

[http://developer.eventbrite.com/docs/event-teams-attendees](Event Teams’ Attendees)

#### Users
[http://developer.eventbrite.com/docs/user-details/](User Details)

[http://developer.eventbrite.com/docs/user-orders/](User Orders)

[http://developer.eventbrite.com/docs/user-owned-events/](User Owned Events)

[http://developer.eventbrite.com/docs/user-owned-events-orders/](User Owned Events’ Orders)

[http://developer.eventbrite.com/docs/user-owned-events-attendees/](User Owned Events’ Attendees)

[http://developer.eventbrite.com/docs/user-venues/](User Venues)

[http://developer.eventbrite.com/docs/user-organizers/](User Organizers)

#### Orders
[http://developer.eventbrite.com/docs/order-details/](Order Details)

#### Contact Lists
[http://developer.eventbrite.com/docs/contact-lists/](Contact Lists)

[http://developer.eventbrite.com/docs/contact-list-details/](Contact List Details)

## License

_node-eventbrite_ is licensed under the MIT License. (See LICENSE)


## [Contributors](https://github.com/Datahero/node-eventbrite/graphs/contributors)
