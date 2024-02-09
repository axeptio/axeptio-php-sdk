# SDK



## How to use Cookies features

To use the Axeptio SDK Cookies properly, you need to use the `Axeptio\SDK\Cookies\AxeptioCookieManager` class.
This class will allow you to define all the necessary cookies and set them.

You got at your disposition builders for each necessary cookie.

For each cookie, the associated builder allow you to set different data required for the cookie.
(expiry, path, secure, httponly, samesite are common data availables for each cookie).

Here is an example :

```php
$cookieManager = new AxeptioCookieManager();
$userPreferences = ['fb-pixel'];

// Define AxeptioCookies
$axeptioCookieBuilder = new AxeptioCookiesBuilder();
$axeptioCookieBuilder->setUserToken('test-user-token');
$axeptioCookieBuilder->setUserPreferences($userPreferences);
$axeptioCookieBuilder->setExpiry(172800);
$axeptioCookie = $axeptioCookieBuilder->create();

// Define AuthorizedVendorCookies
$authorizedVendorCookiesBuilder = new AuthorizedVendorCookiesBuilder();
$authorizedVendorCookiesBuilder->setUserPreferences($userPreferences);
$authorizedVendorCookies = $authorizedVendorCookiesBuilder->create();

// Define AllVendorCookies
$allVendorCookiesBuilder = new AllVendorCookiesBuilder();
$allVendorCookiesBuilder->setVendors(['test', 'test1']);
$allVendorCookies = $allVendorCookiesBuilder->create();

// Use the cookie manager to set the cookies and use the set() method to set them.
// Take note : If one cookie is missing, an UndefinedCookie Exception will be thrown.
$cookieManager->addAxeptioCookies($axeptioCookie);
$cookieManager->addAuthorizedVendorCookies($authorizedVendorCookies);
$cookieManager->addAllVendorCookies($allVendorCookies);
$cookieManager->set();
```
