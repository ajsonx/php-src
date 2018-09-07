cmake_minimum_required(VERSION 3.7)
project(curl)

set(CMAKE_CXX_STANDARD 11)

set(SOURCE_FILES
        ext/curl/curl_file.c)

add_executable(curl ${SOURCE_FILES})

#定义php源码路径，这里根据自己的真实路径来更改
set(PHP_SOURCE /Users/hexi/Develop/php-src)
#引入php需要的扩展源码，这里也是根据自己需要的来更改
include_directories(${PHP_SOURCE}/main)
include_directories(${PHP_SOURCE}/Zend)
include_directories(${PHP_SOURCE}/sapi)
include_directories(${PHP_SOURCE}/pear)
include_directories(${PHP_SOURCE})

#add_custom_target(makefile COMMAND sudo /usr/local/phpdebug/bin/phpize && ./configure --with-php-config=/usr/local/phpdebug/bin/php-config &&  make
#        WORKING_DIRECTORY ${PROJECT_SOURCE_DIR})