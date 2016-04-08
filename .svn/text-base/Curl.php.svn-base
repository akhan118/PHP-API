<?php

/*
 * A library that calls PrincePDF 
 * Author: Ahmad Khan
 * Date: May 20- 2014
 * 
 * 
 */

/// this must be trun off and set to 0 for the PDF to generate;
error_reporting(0);


/*
 * Example of use
 * 
 */

//$princeAPI = new princeAPI();
//$princeAPI->convert_string_to_passthru('This is Ahmad - test PDF output');





class princeAPI {
    /*
     * Properity- Holds the API key 
     */

    private $api_key = 'a7ce4938e76c447cadfcee0b90d9fd63';

    /*
     * Properity- Holds the URI for the API
     */
    public $URI = "https://ultra.perfpro-hrnonline-beta.com/api/prince/v1/";

    /*
     * Properity- An array to hold Methods
     */
    public $methods = array();

    /*
     * Constructor- set all the relative headers so 
     * the browser  can know it's a PDF.
     * 
     * @Return Void
     */

    public function __construct() {

        header("Pragma: ");
        header("Cache-Control: ");
        header('Content-Type: application/pdf');
        header('Content-Disposition: attachment; filename="PDF"');
    }

    /*
     * Function: Convert a string to PDF.
     * add all CSS to the PDF string and pass it ot
     * 
     * @Returns- Raw PDF data for the browser to turn into a PDF
     */

    public function convert_string_to_passthru($html) {

        $html = mb_convert_encoding($html, 'UTF-8');
        $this->methods[__FUNCTION__] = $html;
        $data = $this->build_post_array();
        $this->Curl($data, $this->URI);
    }

    /*
     * Function- build an array for the CURL function
     * 
     * @returns an array
     */

    private function build_post_array() {
        $post_data = array(
            "apikey" => $this->api_key,
            "methods" => $this->methods,);
        return $post_data;
    }

    /*
     * Function- Makes a CURL call to Prince API
     * 
     * @ returns PDF ouput in Raw data, browser convert it to PDF by setting the headers
     * in the constroctor 
     */

    private function Curl($data, $URI) {
        $ch = curl_init();
        $post_data = http_build_query($data);
        curl_setopt($ch, CURLOPT_URL, $URI);
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
        curl_setopt($ch, CURLOPT_POST, 1);
        curl_setopt($ch, CURLOPT_POSTFIELDS, $post_data);
        curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, ( $ssl_verify === false ) ? 2 : false);
        $output = curl_exec($ch);
        curl_close($ch);
        echo $output;
        
        /*
         * incase the PDF file need to be save locally on the server
         * comment out the echo statment above at line 104 and uncomment
         * the following lines below.
         */
        //$path = '/Applications/MAMP/htdocs/test.pdf';
       // file_put_contents( $path, $output );
    }

}
