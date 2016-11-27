Ansible Role: rTorrent
======================

Ansible role to configure rTorrent.

Role Variables
--------------

```yaml
rtorrent_rc_path: "/var/lib/rtorrent/.rtorrent.rc"

# ----- bandwidth settings -----
rtorrent_min_peers: 40
rtorrent_max_peers: 100
rtorrent_min_peers_seed: 10
rtorrent_max_peers_seed: 50
rtorrent_max_uploads: 15
rtorrent_max_global_downloads: 300
rtorrent_max_global_uploads: 300
rtorrent_download_rate: 0
rtorrent_upload_rate: 0
rtorrent_numwant: -1

# ----- directory settings -----
rtorrent_directory_download: ~/rtorrent/download
rtorrent_directory_session: ~/rtorrent/.session
rtorrent_directory_watch: ~/rtorrent/watch

# ----- network settings -----
rtorrent_port_range: 49164-49164
rtorrent_port_random: "no"
rtorrent_ssl_verify_peer: 0
rtorrent_max_open_sockets: 999
rtorrent_max_open_files: 1024
rtorrent_max_open_http: 32
rtorrent_receive_buffer_size: 0
rtorrent_send_buffer_size: 0
rtorrent_dns_cache_timeout: 60
rtorrent_xmlrpc_size_limit: 524288

# ----- schedule settings -----
rtorrent_schedule_watch_directory: "watch_directory,5,5,load_start={{ rtorrent_directory_watch }}/*.torrent"
rtorrent_schedule_untied_directory: "untied_directory,5,5,stop_untied="

# ----- torrent settings -----
rtorrent_check_hash: "no"
rtorrent_use_udp_trackers: "yes"
rtorrent_tracker_numwant: -1
rtorrent_encryption: "allow_incoming,enable_retry,prefer_plaintext"
rtorrent_dht: "off"
rtorrent_dht_port: 6881
rtorrent_peer_exchange: "yes"

# ----- memory and pieces buffers -----
rtorrent_max_memory_usage: "1024M"
rtorrent_pieces_preload_type: 0
rtorrent_pieces_preload_min_size: 262144
rtorrent_pieces_preload_min_rate: 5120

# ----- other settings -----
#  (can break rtorrent when misconfigured)
rtorrent_file_allocate: 0
# Delete data of erased torrents
rtorrent_delete_erased: false
rtorrent_other_settings: []
# Example
#    - scgi_port = 127.0.0.1:5000
```

Dependencies
------------

None

Example Playbook
-------------------------

1) Configure rTorrent with default settings

```yaml
- hosts: servers-torrent
  roles:
    - role: Anthony25.rTorrent
```

2) Install rTorrent with custom settings

```yaml
- hosts: servers-torrent
  roles:
    - role: Anthony25.rTorrent
      rtorrent_min_peers: 0
      rtorrent_max_peers: 1000
```

License
-------

BSD

Author Information
------------------

Anthony25 <Anthony Ruhier>
Forked of the Prescott Chris's work
