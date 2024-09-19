# Meterpreter Scripts and Modules (TODO)

https://github.com/rapid7/metasploit-framework/tree/master/documentation (refer to this)

## Windows Gather Modules


run post/windows/manage/powershell/load_script

run post/windows/manage/powershell/build_net_code



run post/windows/gather/memory_grep (find specific strings in the process ID)

run post/windows/gather/outlook (https://github.com/rapid7/metasploit-framework/blob/master/data/post/powershell/outlook.ps1)

run post/windows/gather/exchange (https://github.com/rapid7/metasploit-framework/blob/master/data/post/powershell/exchange.ps1 && https://news.sophos.com/en-us/2021/03/09/sophoslabs-offensive-security-releases-post-exploitation-tool-for-exchange/ && https://github.com/sophoslabs/metasploit_gather_exchange)

=========

run dumplinks (dump shortcut lnk files)

run post/windows/gather/dumplinks (dump shortcut lnk files) && https://github.com/rapid7/metasploit-framework/blob/master/documentation/modules/post/windows/gather/dumplinks.md

=========

run post/windows/escalate/droplnk



run post/windows/gather/enum_av_excluded (find exclusions in Windows Defender and other few AVs)

run post/windows/gather/enum_artifacts (detect malware)

run post/multi/gather/check_malware

======================

run post/windows/gather/ad_to_sqlite

run post/windows/gather/credentials/wsftp_client

run post/windows/gather/avast_memory_dump

run post/windows/gather/credentials/xshell_xftp_password

run post/windows/gather/bitlocker_fvek

run post/windows/gather/dnscache_dump

run post/windows/gather/credentials/aim

run post/windows/gather/credentials/avira_password

run post/windows/gather/credentials/bulletproof_ftp

run post/windows/gather/credentials/comodo

run post/windows/gather/credentials/coolnovo

run post/windows/gather/credentials/coreftp

run post/windows/gather/credentials/digsby

run post/windows/gather/credentials/dynazip_log

run post/windows/gather/credentials/dyndns

run post/windows/gather/credentials/enum_cred_store

run post/windows/gather/enum_db

run post/windows/gather/credentials/enum_picasa_pwds

run post/windows/gather/credentials/epo_sql

run post/windows/gather/credentials/filezilla_server

run post/windows/gather/credentials/flashfxp

run post/windows/gather/credentials/flock



run post/windows/gather/credentials/ftpnavigator



run post/windows/gather/credentials/ftpx

run post/windows/gather/enum_emet

run post/windows/gather/credentials/gadugadu


run post/windows/gather/enum_hostfile

run post/windows/gather/credentials/heidisql

run post/windows/gather/enum_hyperv_vms

run post/windows/gather/credentials/icq

run post/windows/gather/enum_ie

run post/windows/gather/credentials/idm

run post/windows/gather/credentials/ie

run post/windows/gather/enum_ms_product_keys

run post/windows/gather/credentials/imail

run post/windows/gather/enum_muicache

run post/windows/gather/credentials/imvu



run post/windows/gather/credentials/incredimail

run post/windows/gather/credentials/kakaotalk

run post/windows/gather/credentials/kmeleon

run post/windows/gather/enum_prefetch

run post/windows/gather/credentials/viber (instant messenger)

run post/windows/gather/credentials/line (instant messenger)



run post/windows/gather/credentials/maxthon

run post/windows/gather/credentials/mcafee_vse_hashdump

run post/windows/gather/credentials/mdaemon_cred_collector

run post/windows/gather/credentials/meebo



run post/windows/gather/credentials/miranda



run post/windows/gather/credentials/mremote

run post/windows/gather/credentials/mssql_local_hashdump



run post/windows/gather/credentials/nimbuzz

run post/windows/gather/enum_trusted_locations



run post/windows/gather/credentials/postbox



run post/windows/gather/forensics/duqu_check


run post/windows/gather/credentials/qq

run post/windows/gather/forensics/fanny_bmp_check

run post/windows/gather/credentials/razer_synapse

run post/windows/gather/forensics/imager

run post/windows/gather/credentials/razorsql

run post/windows/gather/forensics/nbd_server

run post/windows/gather/credentials/rdc_manager_creds


run post/windows/gather/credentials/seamonkey

run post/windows/gather/local_admin_search_enum

run post/windows/gather/credentials/securecrt

run post/windows/gather/make_csv_orgchart

run post/windows/gather/credentials/smartermail

run post/windows/gather/credentials/smartftp

run post/windows/gather/credentials/spark_im

run post/windows/gather/netlm_downgrade

run post/windows/gather/credentials/srware



run post/windows/gather/credentials/steam (steam)

run post/windows/gather/credentials/tango

run post/windows/gather/credentials/teamviewer_passwords

run post/windows/gather/resolve_sid

run post/windows/gather/credentials/tlen



run post/windows/gather/credentials/tortoisesvn

run post/windows/gather/credentials/total_commander

run post/windows/gather/credentials/trillian

run post/windows/gather/tcpnetstat



run post/windows/gather/credentials/windows_sam_hivenightmare

run post/windows/gather/word_unc_injector

## Windows Manage Modules

run post/windows/manage/archmigrate

run post/windows/manage/remove_host

run post/windows/manage/rid_hijack

run post/windows/manage/clone_proxy_settings

run post/windows/manage/mssql_local_auth_bypass

run post/windows/manage/rpcapd_start

run post/windows/manage/dell_memory_protect



run post/windows/manage/nbd_server





run post/windows/manage/enable_support_account








run post/windows/manage/forward_pageant



run post/windows/manage/hashcarve

run post/windows/manage/pptp_tunnel



run post/windows/manage/ie_proxypac

run post/windows/manage/priv_migrate

run post/windows/manage/webcam

run post/windows/manage/pxeexploit

run post/windows/manage/reflective_dll_inject

## Multi Modules

run post/multi/gather/aws_ec2_instance_metadata

run post/multi/escalate/aws_create_iam_user

run post/multi/gather/aws_keys

run post/multi/gather/jboss_gather

run post/multi/manage/open

run post/multi/general/close

run post/multi/escalate/cups_root_file_read



run post/multi/general/execute

run post/multi/gather/lastpass_creds

run post/multi/general/wall

run post/multi/gather/apple_ios_backup

run post/multi/gather/maven_creds



run post/multi/manage/dbvis_add_db_admin



run post/multi/gather/netrc_creds

run post/multi/manage/dbvis_query


run post/multi/gather/chrome_cookies

run post/multi/gather/pgpass_creds

run post/multi/manage/hsts_eraser

run post/multi/gather/dbvis_enum

run post/multi/gather/pidgin_cred



run post/multi/gather/dns_bruteforce







run post/multi/gather/dns_srv_lookup



run post/multi/manage/record_mic

run post/multi/gather/docker_creds

run post/multi/gather/rsyncd_creds



run post/multi/gather/rubygems_api_key



run post/multi/gather/saltstack_salt



run post/multi/manage/sudo

run post/multi/gather/fetchmailrc_creds

run post/multi/gather/filezilla_client_cred



run post/multi/manage/zip



run post/multi/gather/ubiquiti_unifi_backup


run post/multi/recon/multiport_egress_traffic


run post/multi/sap/smdagent_get_properties

## Linux Modules

run post/linux/busybox/enum_connections



run post/linux/busybox/enum_hosts





run post/linux/busybox/jailbreak





run post/linux/busybox/ping_net

run post/linux/gather/enum_nagios_xi



run post/linux/busybox/set_dmz

run post/linux/gather/pptpd_chap_secrets

run post/linux/busybox/set_dns



run post/linux/gather/tor_hiddenservices

run post/linux/busybox/smb_share_root



run post/linux/manage/dns_spoofing

run post/linux/busybox/wget_exec

run post/linux/dos/xen_420_dos

run post/linux/manage/geutebruck_post_exp



run post/linux/gather/gnome_commander_creds

run post/linux/gather/gnome_keyring_dump

run post/linux/gather/ecryptfs_creds

run post/linux/gather/haserl_read

run post/linux/manage/sshkey_persistence

## OSX Modules



run post/osx/gather/enum_chicken_vnc_profile

run post/osx/gather/safari_lastsession



run post/osx/gather/enum_colloquy

run post/osx/gather/vnc_password_osx



run post/osx/gather/enum_keychain



run post/osx/escalate/tccbypass

run post/osx/gather/enum_messages



run post/osx/gather/apfs_encrypted_volume_passwd



run post/osx/gather/autologin_password

run post/osx/gather/gitignore



run post/osx/gather/enum_adium





run post/osx/gather/enum_airport

run post/osx/gather/password_prompt_spoof

## Others

run domain_list_gen

run duplicate

run enum_putty

run enum_vmware

run event_manager

run scraper



https://www.hackers-arise.com/ultimate-list-of-meterpreter-scripts