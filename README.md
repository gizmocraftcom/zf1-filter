# Zend Framework 1 - Filter

[![Build](https://github.com/gizmocraftcom/zf1-filter/workflows/Build/badge.svg?event=push)](https://github.com/gizmocraftcom/zf1-filter/actions?query=workflow%3ABuild+event%3Apush)
[![Latest Stable Version](https://poser.pugx.org/gizmocraft/zendframework1-filter/v/stable)](https://packagist.org/packages/gizmocraft/zendframework1-filter)
[![Total Downloads](https://poser.pugx.org/gizmocraft/zendframework1-filter/downloads)](https://packagist.org/packages/gizmocraft/zendframework1-filter)
[![License](https://poser.pugx.org/gizmocraft/zendframework1-filter/license)](https://packagist.org/packages/gizmocraft/zendframework1-filter)


This is just the Zend_Filter component extracted from our fork of the Zend Framework 1 repo (https://github.com/gizmocraftcom/zf1).

Forked from https://github.com/diablomedia/zf1-filter, adapted for PHP 8.5 and 8.6.

## Notes on optional extensions

- `Zend_Filter_Encrypt_Mcrypt` (and the `mcrypt` option of `Zend_Filter_Encrypt`) needs `ext-mcrypt`, which was removed from PHP core in 7.2 and is only available as an unmaintained PECL extension. The adapter is kept and marked `@deprecated`; without the extension it throws `Zend_Filter_Exception`. Use `Zend_Filter_Encrypt_Openssl` instead.
- `Zend_Filter_Encrypt_Openssl` seals with the RC4 cipher, which OpenSSL 3 and later only offers when the legacy provider is enabled (OpenSSL 1.1 builds have it by default). Without RC4, `encrypt()` throws `Zend_Filter_Exception`. The cipher is unchanged to stay compatible with existing encrypted data. Newer OpenSSL versions (3.2+) also reject invalid RSA envelope keys implicitly: `decrypt()` returns garbage instead of throwing.
- The compress adapters (`Bz2`, `Gz`, `Lzf`, `Rar`, `Tar`, `Zip`) are unchanged and need their respective extensions (`bz2`, `zlib`, `lzf`, `rar`, `zip`, `pear/archive_tar`).

Originally forked from the upstream repository https://github.com/diablomedia/zf1-filter. Copyright and license of the original authors are kept in LICENSE.txt.
