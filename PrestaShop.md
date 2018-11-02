# Prestashop Plugin for BTCPay server, an opensource Payment processor

Warning this is a Beta version. Use it at your own risk.

## Description

A bitcoin payment plugin for PrestaShop using BTCPay server.
BTCPay Server is a free and open source server for merchants wanting to accept Bitcoin for their business.
The API is compatible with Bitpay service to allow seamless migration.

BTCPay is design to be easy to deploy on container hosting platform like Azure.
and if you want, some companies provide hosting services.

# Using the BTCPay plugin for Prestashop

## Prerequisites
You must have a BTCPay merchant account to use this plugin.
If you want to test in test mode, just paste an other btcpayserver url with testing port.

## Making a release
* add Bitpay https://github.com/btcpayserver/php-bitpay-client/tree/master/src/Bitpay into modules/bitpay/lib
* zip btcpay directory into btcpay.zip
* add bitcoin icon into Order state configuration / icon !

## Server Requirements

+ PrestaShop 1.7
+ PHP 5+
+ Curl PHP Extension
+ JSON PHP Extension

## Plugin Configuration

### For Prestashop versions 1.7:
1. Download the latest release from https://github.com/adapp-tech/prestashop-plugin/releases
2. Go to your PrestaShop administration. Under "Modules and services" select "Upload a module" (v1.7)
3. Go to your "installed modules" -> "BTCPay" and click [Configure]<br />
4. Go on your BTCPay server, in your store and display access tokens.
5. Click on "Create a new token API", select your store and then approve
6. You will see: "Server initiated pairing code: XXXX". Go back to prestashop and enter your pairing code.
7. Validate.
8. Test a payment.

# Support

## Tested successfully
* Prestashop 1.7.x
* BTCPay server v1.0.1 and v1.0.2

## Contribute

To contribute to this project, please fork and submit a pull request.
* [GitHub Issues](https://github.com/adapptech/prestashop-plugin/issues)

## PrestaShop Support

* [Homepage](http://www.prestashop.com)
* [Documentation](http://doc.prestashop.com/)
* [Support Forums](http://www.prestashop.com/forums/)
