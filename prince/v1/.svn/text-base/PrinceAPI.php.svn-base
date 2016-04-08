<?php

/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */



require_once '../../API.abstract.php';
require '../../../tools/prince.php';

//# PrinceXML PDF GENERATOR  Executable Path
//define('PDF_GENERATOR_PATH','/usr/local/bin/prince');
//
//#PrinceXML PDF GENERATOR LOG PATH
//define('PDF_GENERATOR_LOG_PATH', '/private/log/prince.log');

define('PDF_GENERATOR_PATH', '/hrn/usr/bin/prince');
define('PDF_GENERATOR_LOG_PATH', '/hrn/future/private/log/prince.log');

class PrinceAPI extends API {

    protected $user;
    public $prince;
    private $phrase = "Damn It Feels Good To Be A Gangsta";

    function __construct($request, $server) {
        parent::__construct($request, $server);

        $this->prince = new Prince(PDF_GENERATOR_PATH);
        $this->process_pdf();
    }

    function process_pdf() {

        if ($this->Authorize_user()) {

            $this->validate_methods();
        }
    }

    function Authorize_user() {

        if ($this->Generated_API_KEY() === $this->apikey) {
            return TRUE;
        } else {
            print ('API KEY NOT AUTHORIZED');
            return FALSE;
        }
    }

    function Generated_API_KEY() {
        return $ApiKey = md5($this->phrase);
    }

    function validate_methods() {


        foreach ($this->methods as $key => $value) {

            if (method_exists($this, $key)) {


                $this->$key($value);
            } else {
                exit('Method does not exists');
            }
        }
    }

    private function _requestStatus($code) {
        $status = array(
            200 => 'OK',
            404 => 'Not Found',
            405 => 'Method Not Allowed',
            500 => 'Internal Server Error',
            666 => 'API KEY NOT AUTHORIZED'
        );
        return ($status[$code]) ? $status[$code] : $status[500];
    }

    public function convert_string_to_passthru($xmlString) {

        $this->prince->setJavaScript(TRUE);
        $this->prince->convert_string_to_passthru($xmlString);
    }

}
