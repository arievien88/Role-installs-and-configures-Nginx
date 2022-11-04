Nginx
=====

This role installs and configures nginx, using [community](http://nginx.org/en/linux_packages.html) packages or [openresty](http://openresty.org/en/installation.html) source code.

Role Variables
--------------

- `nginx_source`: Which source to use: 'community' or 'openresty' (default: 'community')
- `nginx_init_system`: OS init system. Docker phusion/baseimage uses 'runit'. (default 'upstart')
- `nginx_keep_default_sites`: Keep default sites or not (default: False)
- `nginx_user`: User nginx will run as (default: 'www-data')
- `nginx_group`: Group php-fpm will run as (default: nginx_user)
- `nginx_worker_processes`: Number of worker processes (default: '1')
- `nginx_worker_connections`: Maximum number of simultaneous connections that can be opened by a worker process (default: '1024')
- `nginx_sendfile`: Enables or disables the use of sendfile() (default: 'on')
- `nginx_tcp_nopush`: Enables or disables the use of the TCP_NOPUSH socket option on FreeBSD or the TCP_CORK socket option on Linux (default: 'on')
- `nginx_tcp_nodelay`: Enables or disables the use of the TCP_NODELAY option (default: 'on')
- `nginx_keepalive_timeout`: Sets a timeout during which a keep-alive client connection will stay open on the server side (default: '65')
- `nginx_types_hash_max_size`: Sets the maximum size of the types hash tables (default: '2048')
- `nginx_default_type`: Sets default mime type (default: 'application/octet-stream')
- `nginx_access_log`: Path to access log (default: 'off')
- `nginx_error_log`: Path to error log (default: '/var/log/nginx/error.log')
- `nginx_gzip`: Enable compression or not (default: True)
- `nginx_custom_directives`: Dict with custom directives (directive: value) to apply (Ex: nginx_custom_directives:{client_max_body_size:'20M'})
- `nginx_sites`: List of sites to enable (default: empty list)
- `nginx_confs`: List of custom confs to enable (default: empty list)
- `nginx_community_version`: Community version, currently only 'stable' or 'mainline', to install (default: 'stable')
- `nginx_openresty_version`: Openresty version to install (default: '1.9.15.1')
- `nginx_openresty_configure_options`: Configure options to compile nginx-openresty (default: ['--with-pcre-jit','--with-ipv6'])

Example Playbook
----------------

    - hosts: servers
      roles:
        - {
          role: nginx,
          nginx_source: 'community',
          nginx_community_version: 'mainline',
          nginx_init_system: 'runit',
          nginx_keep_default_sites: True
        }

License
-------

MIT

[![Build Status](https://travis-ci.org/dpujadas/ansible-role-nginx.svg?branch=master)](https://travis-ci.org/dpujadas/ansible-role-nginx)
