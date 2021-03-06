## OpenResty基础
- OpenResty版本号
	-  OpenResty 的版本号是跟着它所使用的 Nginx 来确定的，比如 OpenResty 的 1.15.8.1，使用的 Nginx 版本号就是 1.15.8，最后的 1 是 OpenResty 自己的小版本号
- 启动与关闭
	- 指定配置文件
	
    		$ openresty -p `pwd` -c conf/nginx.conf
	- 关闭 
	
    		$ openresty -s stop
	- 重启
	
    		$ openresty -s reload
- 查看openresty版本信息和编译参数
``` shell
$ openresty -v
nginx version: openresty/1.15.8.1
$ openresty -V
nginx version: openresty/1.15.8.1
built by clang 8.0.0 (clang-800.0.42.1)
built with OpenSSL 1.1.0j  20 Nov 2018
TLS SNI support enabled
configure arguments: --prefix=/usr/local/Homebrew/Cellar/openresty/1.15.8.1/nginx --with-cc-opt='-O2 -I/usr/local/Homebrew/include -I/usr/local/Homebrew/opt/pcre/include -I/usr/local/Homebrew/opt/openresty-openssl/include' --add-module=../ngx_devel_kit-0.3.1rc1 --add-module=../echo-nginx-module-0.61 --add-module=../xss-nginx-module-0.06 --add-module=../ngx_coolkit-0.2 --add-module=../set-misc-nginx-module-0.32 --add-module=../form-input-nginx-module-0.12 --add-module=../encrypted-session-nginx-module-0.08 --add-module=../srcache-nginx-module-0.31 --add-module=../ngx_lua-0.10.15 --add-module=../ngx_lua_upstream-0.07 --add-module=../headers-more-nginx-module-0.33 --add-module=../array-var-nginx-module-0.05 --add-module=../memc-nginx-module-0.19 --add-module=../redis2-nginx-module-0.15 --add-module=../redis-nginx-module-0.3.7 --add-module=../ngx_stream_lua-0.0.7 --with-ld-opt='-Wl,-rpath,/usr/local/Homebrew/Cellar/openresty/1.15.8.1/luajit/lib -L/usr/local/Homebrew/lib -L/usr/local/Homebrew/opt/pcre/lib -L/usr/local/Homebrew/opt/openresty-openssl/lib' --pid-path=/usr/local/Homebrew/var/run/openresty.pid --lock-path=/usr/local/Homebrew/var/run/openresty.lock --conf-path=/usr/local/Homebrew/etc/openresty/nginx.conf --http-log-path=/usr/local/Homebrew/var/log/nginx/access.log --error-log-path=/usr/local/Homebrew/var/log/nginx/error.log --with-pcre-jit --with-ipv6 --with-stream --with-stream_ssl_module --with-stream_ssl_preread_module --with-http_v2_module --without-mail_pop3_module --without-mail_imap_module --without-mail_smtp_module --with-http_stub_status_module --with-http_realip_module --with-http_addition_module --with-http_auth_request_module --with-http_secure_link_module --with-http_random_index_module --with-http_geoip_module --with-http_gzip_static_module --with-http_sub_module --with-http_dav_module --with-http_flv_module --with-http_mp4_module --with-http_gunzip_module --with-threads --with-dtrace-probes --with-stream --with-stream_ssl_preread_module --with-http_ssl_module
```
- openresty命令帮助
``` shell
$ openresty -h
nginx version: openresty/1.15.8.1
Usage: nginx [-?hvVtTq] [-s signal] [-c filename] [-p prefix] [-g directives]

Options:
  -?,-h         : this help
  -v            : show version and exit
  -V            : show version and configure options then exit
  -t            : test configuration and exit
  -T            : test configuration, dump it and exit
  -q            : suppress non-error messages during configuration testing
  -s signal     : send signal to a master process: stop, quit, reopen, reload
  -p prefix     : set prefix path (default: /usr/local/Homebrew/Cellar/openresty/1.15.8.1/nginx/)
  -c filename   : set configuration file (default: /usr/local/Homebrew/etc/openresty/nginx.conf)
  -g directives : set global directives out of configuration file
```
PS:可以看到默认加载的配置文件位置
- `restydoc` 帮助查看命令
``` shell
$ restydoc -s ngx.say
ngx_lua-0.10.15(7)              ngx_lua-0.10.15             ngx_lua-0.10.15(7)

   ngx.say
       syntax: ok, err = ngx.say(...)

       context: rewrite_by_lua*, access_by_lua*, content_by_lua*

       Just as ngx.print but also emit a trailing newline.



OpenResty                         2019-06-02                ngx_lua-0.10.15(7)
(END)
```
- OpenResty 的 CLI：`resty`

        $ which resty
        /usr/local/Homebrew/bin/resty
        $ resty -e "ngx.say('hello world')"
        hello world
        $ resty -h
        resty [options] [lua-file [args]]

        Options:
            -c NUM              Set maximal connection count (default: 64).
            -e PROG             Run the inlined Lua code in "prog".

            --errlog-level LEVEL
                                Set nginx error_log level.
                                Can be debug, info, notice, warn, error, crit, alert,
                                or emerg.

            --gdb               Use GDB to run the underlying nginx C process.

            --gdb-opts OPTS     Pass extra command-line options to GDB.

            --help              Print this help.

            --http-conf CONF    Specifies nginx.conf snippet inserted into the http {}
                                configuration block (multiple instances are supported).

            --http-include PATH Include the specified file in the nginx http
                                configuration block (multiple instances are supported).

            -I DIR              Add dir to the search paths for Lua libraries.

            -j dump             Use LuaJIT's jit.dump module to output detailed info of
                                the traces generated by the JIT compiler.

            -j off              Turn off the LuaJIT JIT compiler.

            -j v                Use LuaJIT's jit.v module to output brief info of the
                                traces generated by the JIT compiler.

            -l LIB              Require library "lib".

            --main-conf CONF    Specifies nginx.conf snippet inserted into the nginx
                                main {} configuration block (multiple instances are
                                supported).

            --main-include PATH Include the specified file in the nginx main
                                configuration block (multiple instances are supported).

            --nginx             Specify the nginx path (this option might be removed
                                in the future).

            --ns IP             Specify a custom name server (multiple instances are
                                supported).

            --resolve-ipv6      Make the nginx resolver lookup both IPv4 and IPv6
                                addresses.

            --rr                Use Mozilla rr to record the execution of the
                                underlying nginx C process.

            --shdict 'NAME SIZE'
                                Create the specified lua shared dicts in the http
                                configuration block (multiple instances are supported).

            --stap
                                Use sysetmtap to run the underlying nginx C process.

            --stap-opts OPTS
                                Pass extra systemtap command line options.

            -V                  Print version numbers and nginx configurations.

            --valgrind          Use valgrind to run nginx.

            --valgrind-opts OPTS
                                Pass extra options to valgrind.

        For bug reporting instructions, please see:

            <https://openresty.org/en/community.html>

        Copyright (C) Yichun Zhang (agentzh). All rights reserved.

