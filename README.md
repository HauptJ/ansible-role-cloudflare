# ansible-role-cloudflare
Ansible role to configure CloudFlare DNS records
SEE: [Official DNS API Documentation](https://api.cloudflare.com/#dns-records-for-a-zone-properties)

This is a proof of concept, use the [Terraform script](https://github.com/HauptJ/WordPress-CloudFlare-Terraform) to configure DNS records instead.

This role utilizes CloudFlare's API to configure DNS records
New records are created by sending `POST` requests containing hostname and IP.
Existing records are updated by sending `PUT` requests containing hostname, IP and
record ID.

## Requirements

- Ansible 2.3+
- Any Linux or BSD distribution

## Installation
1. Fork this repository
2. git submodule add <git host> roles/ansible-role-cloudflare
    - [submodule reference](https://chrisjean.com/git-submodules-adding-using-removing-and-updating/)

## Variables

### CloudFlare

| Name 						                  | Default 							                    | Description 										        |
|-----------------------------------|-------------------------------------------|-----------------------------------------|
| cf_email                          | cf@example.com                            | CloudFlare account Email address        |
| cf_key                            | your_api_key                              | CloudFlare account API key              |
| cf_new_record                     | true                                      | true: create new records; false: update existing records |
| server_hostname                   | example.com                               | server DNS name to be **_proxied_** with CloudFlare      |
| cf_bypass_name                    | srv.example.com                           | **_non proxied_** DNS name              |
| ipv4_addr                         | 54.39.111.111                             | server IPv4 address                     |
| nginx_ipv6                        | 2607:5300:201:2100::5:1111                | server IPv6 address                     |
| cf_zone_id                        | your_zone_id                              | CloudFlare zone ID                      |
| cf_A_id                           | your_A_id                                 | CloudFlare **EXISTING _non proxied_** A (IPv4) record ID     |
| cf_AAAA_id                        | your_AAAA_id                              | CloudFlare **EXISTING _non proxied_** AAAA (IPv6) record ID  |
| cf_proxied_AAAA_id                | your_proxied_AAAA_id                      | CloudFlare **EXISTING _proxied_** AAAA (IPv6) record ID      |
