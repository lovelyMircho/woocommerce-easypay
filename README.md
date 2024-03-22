# Woocommerce Easypay Plugin

Telenor Easypay Payment Gateway Plugin for Woocommerce

This plugin adds Telenor Easypay payment gateway to Woocommerce. You will need to get an Easypay merchant account from Telenor to be able to use this plugin. This plugin supports the sandbox mode provided by Easypay as well.

Installation

1. Upload the plugin files to the `/wp-content/plugins/plugin-name` directory, or install the plugin through the WordPress plugins screen directly.
2. Activate the plugin through the 'Plugins' screen in WordPress
3. Go to Woocommerce -> Settings -> Checkout -> Pay via Easypay to configure.
4. You will also need to configure IPN URL in Easypay Merchant Portal. The IPN URL should be https://yoursite.com/wc-api/WC_Gateway_Easypay (note the lack of trailing slash).

Frequently Asked Questions

Q. Are you affiliated with Telenor?
A. No.

Q. Have you used this plugin in production?
A. Yes.

Q. Can I hold you responsible if something goes wrong?
A. No.

Q. Which currencies are supported by Easypay?
A. Easypay only supports PKR at the moment. If you are using another currency or multiple currencies, then you should use some method of disabling this gateway when another currency is in use.

I use something like this in my functions.php:

```
function gateway_disable_by_currency( $available_gateways ) {
    global $woocommerce;
    
    if ( isset( $available_gateways['easypay'] ) && !<<insert a function here which checks your currenct currency and returns true if PKR is in use>> ) {
        unset(  $available_gateways['easypay'] );
    }
    return $available_gateways;
}

add_filter( 'woocommerce_available_payment_gateways', 'gateway_avilable_by_currency' );
```
