<?php

/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */

abstract class API {

    /**
     * Property:Method
     * The HTTP Method the request is carrying
     */
    public $request;
    public $apikey;
    public $methods;
    public $server;

    /**
     * endpoint
     * 
     */
    public function __construct($request, $server) {
        header("Access-Control-Allow-Orgin: *");
        header("Access-Control-Allow-Methods: *");
        header("Content-Type: application/json");

        $this->request = $request;
        $this->server = $server;
        $this->assign_request($request);
    }

    private function assign_request($request) {

        if (array_key_exists('apikey', $request)) {

            $this->apikey = $request['apikey'];
        }


        if (array_key_exists('methods', $request)) {
            $this->methods = $request['methods'];
        }
    }

}
