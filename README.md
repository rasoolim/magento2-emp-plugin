eMerchantPay Gateway Module for Magento 2 CE
=============================

This is a Payment Module for Magento 2 Community Edition, that gives you the ability to process payments through eMerchantPay's Payment Gateway - Genesis.

Requirements
------------

* Magento 2 Community Edition 2.x (Tested upto __2.1.3__)
* [GenesisPHP v1.4.x](https://github.com/GenesisGateway/genesis_php) - (Integrated in Module)
* PCI-certified server in order to use ```eMerchantPay Direct```

*Note:* This module has been tested only with Magento 2 __Community Edition__, it may not work
as intended with Magento 2 __Enterprise Edition__

Installation (composer)
---------------------
* Install __Composer__ - [Composer Download Instructions](https://getcomposer.org/doc/00-intro.md)

* Install __eMerchantPay Payment Gateway__

    * Install Payment Module

        ```sh
        $ composer require emerchantpay/magento2-emp-plugin
        ```

    * Enable Payment Module 
        
        ```sh
        $ php bin/magento module:enable EMerchantPay_Genesis --clear-static-content
        ```

        ```sh
        $ php bin/magento setup:upgrade
        ```

    * Deploy Magento Static Content (__Execute If needed__)
        ```sh
        $ php bin/magento setup:static-content:deploy
        ```

Installation (manual)
---------------------

* Upload the contents of the folder (excluding ```README.md```) to a new folder ```<root>/app/code/EMerchantPay/Genesis/``` of your Magento 2 installation
* Install GenesisGateway Client Library
    
    ```sh
    $ composer require genesisgateway/genesis_php:1.4.3@stable
    ```

* Enable Payment Module 

    ```sh
    $ php bin/magento module:enable EMerchantPay_Genesis --clear-static-content
    ```

    ```sh
    $ php bin/magento setup:upgrade
    ```

* Deploy Magento Static Content (__Execute If needed__)
    ```sh
    $ php bin/magento setup:static-content:deploy
    ```

Configuration
---------------------

* Login inside the __Admin Panel__ and go to ```Stores``` -> ```Configuration``` -> ```Sales``` -> ```Payment Methods```
* If the Payment Module Panel ```eMerchantPay``` is not visible in the list of available Payment Methods, 
  go to  ```System``` -> ```Cache Management``` and clear Magento Cache by clicking on ```Flush Magento Cache```
* Go back to ```Payment Methods``` and click the button ```Configure``` under the payment method ```eMerchantPay Checkout``` or ```eMerchantPay Direct``` to expand the available settings
* Set ```Enabled``` to ```Yes```, set the correct credentials, select your prefered transaction types and additional settings and click ```Save config```

Configure Magento over secured HTTPS Connection
---------------------
This configuration is needed for ```eMerchantPay Direct``` Method to be usable.

Steps:
* Ensure you have installed a valid SSL Certificate on your Web Server & you have configured your Virtual Host correctly.
* Login to Magento 2 Admin Panel
* Navigate to ```Stores``` -> ```Configuration``` -> ```General``` -> ```Web``` 
* Expand Tab ```Base URLs (Secure)``` and set ```Use Secure URLs on Storefront``` and ```Use Secure URLs in Admin``` to **Yes**
* Set your ```Secure Base URL``` and click ```Save Config```
* It is recommended to add a **Rewrite Rule** from ```http``` to ```https``` or to configure a **Permanent Redirect** to ```https``` in your virtual host

GenesisPHP Requirements
------------

* PHP version 5.3.2 or newer
* PHP Extensions:
    * [BCMath](https://php.net/bcmath)
    * [CURL](https://php.net/curl) (required, only if you use the curl network interface)
    * [Filter](https://php.net/filter)
    * [Hash](https://php.net/hash)
    * [XMLReader](https://php.net/xmlreader)
    * [XMLWriter](https://php.net/xmlwriter)

_Note_: If you have trouble with your credentials or terminal configuration, get in touch with our [support] team

You're now ready to process payments through our gateway.

[support]: mailto:tech-support@emerchantpay.net
