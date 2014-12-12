Ansible Role - MySQL Server
===========================

A MySQL Server role to install and configure MySQL Server


Requirements
------------

Base role from ELAO stack (elao.base)


Role Handlers
-------------

    mysql server restart  # Restart MySQL server


Role Variables
--------------
```
    elao_mysql_users:
      - { name: 'foo', password: 'bar', priv: 'foo.*:ALL', host: '127.0.0.1' }
    elao_mysql_databases:
      - { name: 'foo' }
    elao_mysql_login_user:     root
    elao_mysql_login_password: null
    elao_mysql_login_host:     localhost

    elao_mysql_login_auto: false
```

#### Full configuration

```
elao_mysql_config_globals:
    socket:                 "/var/run/mysqld/mysqld.sock"   # Define client socket
    port:                   3306                            # Define client connectiong port 
    nice:                   0

elao_mysql_config_mysqld_basics:
    user:                   mysql
    pid:                    "/var/run/mysqld/mysqld.pid"
    socket:                 "/var/run/mysqld/mysqld.sock"   # Define server socket
    port:                   3306                            # Define server listening port
    basedir:                "/usr"
    datadir:                "/var/lib/mysql"
    tmpdir:                 "/tmp"
    messages_dir:           "/usr/share/mysql"
    character_set_server:   utf8
    collation_server:       utf8_general_ci
    bind_address:           "127.0.0.1"

elao_mysql_config_mysqld_advanced:
    key_buffer:             "16M"
    max_allowed_packet:     "16M"
    thread_stack:           "192K"
    thread_cache_size:      8
    myisam_recover:         "BACKUP"
    max_connections:        100
    table_cache:            64
    thread_concurrency:     10
    query_cache_limit:      "1M"
    query_cache_size:       "16M"
    read_buffer_size:       "2M"

elao_mysql_config_mysqld_replication:
    server_id:                      2
    report_host:                    "db-1.mydomain.local"
    log_bin:                        "/var/log/mysql/mysql-bin.log"
    relay_log:                      "/var/log/mysql/mysql-relay-bin.log"
    expire_logs_days:               2
    max_binlog_size:                "100M"
    innodb_flush_log_at_trx_commit: 1
    sync_binlog:                    1
    binlog_do_db:                   ~
    binlog_ignore_db:               ~

elao_mysql_config_mysqld_logging:
    log_slow_queries:               "/var/log/mysql/mysql-slow.log"
    long_query_time:                2
    log_queries_not_using_indexes:  Yes
    expire_logs_days:               10
    max_binlog_size:                "100M"
```

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: elao.mysql-server }


License
-------

MIT


Author Information
------------------

http://www.elao.com/
