# ESP32-CAM-HTTPS
Simple HTTPS web server with Basic-Auth for ESP32-CAM

The HTTPS part is based on: https://github.com/espressif/esp-idf/tree/master/examples/protocols/https_server/simple

The Basic-Auth is based on:  https://github.com/abobija/esp-httpd-basic-auth

## Install

Please install ESP-IDF in order to build and flash this project 

- Add the work of @abobija in your components folder

```
cd IDF-PATH/components
git clone --recursive https://github.com/abobija/esp-httpd-basic-auth.git httpd_basic_auth
```

- use menuconfig to config WiFi

according to esp-idf exemple:

You will need to approve a security exception in your browser. This is because of a self signed
certificate; this will be always the case, unless you preload the CA root into your browser/system
as trusted.

You can generate a new certificate using the OpenSSL command line tool:

```
openssl req -newkey rsa:2048 -nodes -keyout prvtkey.pem -x509 -days 3650 -out cacert.pem -subj "/CN=ESP32 HTTPS server example"
```
>the certificate and the private key need to be placed in `src/main/certs`

It is *strongly recommended* to not reuse the example certificate in your application; it is included only for demonstration.

Once the project build and flash you can acces the flux at `https://login:password@<esp_32_ip>/`