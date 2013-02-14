TWIG helpers
======================

TWIG helpers have been implemented in the project to provide easy access to user permissions restrictions.

Helpers list :

- secure.anchor
- is_accessible

secure.anchor
-------------

This is an URL generation helper that shows a link if the user has access to a route, shows nothing otherwise.

It is used in twig templates with the following code:

    {{ secure.anchor(link_text, _route, _route_values, _link_attributes) }}

- link_text (string): the content of the <a> tag and the actual content to be transformed into a link. Can be html code.
- _route (string): the project's route to be used when generating the url.
- _route_values (array): a list of the project's route parameters to be used when generating the url.
- _link_attributes (array): a list of attributes to be set when creating the <a> tag. ie: class, style, etc.

is_accessible
-------------

This is a twig function that returns true if a url path is accessible to the connected user, false otherwise.

It is used in twig templates with the following code:

    {{ is_accessible( _route, _route_values ) }}

- _route (string): the project's route to be used when generating the url.
- _route_values (array): a list of the project's route parameters to be used when generating the url.

Connexion Restrictions Service
==============================

The Connexion Restrictions Service adds support functions to retrieve access restrictions for a given user.

Features list :

- Get Perimeter for connected user
- Get Subdomain for connected user
- Get Delegation for connected user

Calling the service
-------------------

The class in question is `pxCore\CentralBundle\Services\SecurityToken` and is defined as a service with the id `pxcore.token`, hence it can be instantiated in a controller through :

    $service = $this->get('pxcore.token')

Get Perimeter for connected user
--------------------------------

This can be achieved by calling the `getPerimeter()` function which takes no arguments.

    $perimeter = $service->getPerimeter();

This function returns :

- if Perimeter is defined, an array with two keys :
 - client: containing the user's client perimeter
 - shop: containing an array with the user's shops perimeter
- else, false

Get Subdomain for connected user
--------------------------------
This can be achieved by calling the `getSubdomain()` function which takes no arguments.

    $perimeter = $service->getSubdomain();

This function returns :

- the subdomain id which is also the client's reference, if a subdomain is defined
- false otherwise

Get Delegation for connected user
---------------------------------
This can be achieved by calling the `getDelegation()` function which takes no arguments.

    $perimeter = $service->getDelegation();

This function returns true if the user is connected with a delegated account, false otherwise
