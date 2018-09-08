cmake_minimum_required(VERSION 3.7)
project(php)

set(CMAKE_CXX_STANDARD 11)

set(SOURCE_FILES
        sapi/fpm/fpm/fpm.c
        sapi/fpm/fpm/fpm_children.c
        sapi/fpm/fpm/fpm_cleanup.c
        sapi/fpm/fpm/fpm_clock.c
        sapi/fpm/fpm/fpm_conf.c
        sapi/fpm/fpm/fpm_env.c
        sapi/fpm/fpm/fpm_events.c
        sapi/fpm/fpm/fpm_log.c
        sapi/fpm/fpm/fpm_main.c
        sapi/fpm/fpm/fpm_php.c
        sapi/fpm/fpm/fpm_php_trace.c
        sapi/fpm/fpm/fpm_process_ctl.c
        sapi/fpm/fpm/fpm_request.c
        sapi/fpm/fpm/fpm_scoreboard.c
        sapi/fpm/fpm/fpm_shm.c
        sapi/fpm/fpm/fpm_signals.c
        sapi/fpm/fpm/fpm_sockets.c
        #sapi/fpm/fpm/fpm_status.c
        sapi/fpm/fpm/fpm_stdio.c
        sapi/fpm/fpm/fpm_systemd.c
        sapi/fpm/fpm/fpm_trace.c
        sapi/fpm/fpm/fpm_trace_mach.c
        sapi/fpm/fpm/fpm_trace_pread.c
        sapi/fpm/fpm/fpm_trace_ptrace.c
        sapi/fpm/fpm/fpm_unix.c
        sapi/fpm/fpm/fpm_worker_pool.c
        sapi/fpm/fpm/zlog.c
        )

add_executable(php ${SOURCE_FILES})

#定义php源码路径，这里根据自己的真实路径来更改
set(PHP_SOURCE /Users/hexi/Develop/php-src)
#引入php需要的扩展源码，这里也是根据自己需要的来更改
include_directories(${PHP_SOURCE}/main)
include_directories(${PHP_SOURCE}/Zend)
include_directories(${PHP_SOURCE}/sapi)
include_directories(${PHP_SOURCE}/sapi/fpm)
include_directories(${PHP_SOURCE}/pear)
include_directories(${PHP_SOURCE}/TSRM)
include_directories(${PHP_SOURCE})

#add_custom_target(makefile COMMAND sudo /usr/local/phpdebug/bin/phpize && ./configure --with-php-config=/usr/local/phpdebug/bin/php-config &&  make
#        WORKING_DIRECTORY ${PROJECT_SOURCE_DIR})