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
