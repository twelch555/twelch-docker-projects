#Email settings
Based on https://gist.github.com/franz-josef-kaiser/5840282 *Note: wpmail_exceptions.php can also be added and Wordpress Debug enabled for troubleshooting.

Copy below to plugin wpmail_smtp.php:
~~~~
<?php
defined( 'ABSPATH' ) OR exit;
/**
 * Plugin Name: (WCM) PHPMailer SMTP Settings
 * Description: Enables SMTP servers, SSL/TSL authentication and SMTP settings.
 */

add_action( 'phpmailer_init', 'phpmailerSMTP' );
function phpmailerSMTP( $phpmailer )
{
        $phpmailer->IsSMTP();
        $phpmailer->SMTPAuth    = false;  // Authentication
        $phpmailer->Host        = ''; // site url
        # $phpmailer->Username    = '';
        # $phpmailer->Password    = '';
        # $phpmailer->SMTPSecure  ='ssl'; // enable if required, 'tls' is another possible value
        $phpmailer->Host        = '';    // SMTP Host
        $phpmailer->Port        = 25;    // SMTP Port
        $phpmailer->From        = '';    // SMTP Port
        $phpmailer->FromName    = '';    // SMTP Port
}
~~~~