# Changelog

## 2.0.0

Fork of `diablomedia/zendframework1-filter`, published as `gizmocraft/zendframework1-filter`.

### Breaking changes

- Requires PHP `>=8.5`. Tested on PHP 8.5 and 8.6.
- Package renamed from `diablomedia/zendframework1-filter` to `gizmocraft/zendframework1-filter`. It now requires `gizmocraft/zendframework1-exception`, `-loader`, `-crypt`, `-date` and `-locale` (all `^2.0.0`) and `-config` `^3.0.0`.

### Deprecated

- `Zend_Filter_Encrypt_Mcrypt` is kept and marked `@deprecated`. `ext-mcrypt` was removed from PHP in 7.2 and exists only as an unmaintained PECL extension; the adapter throws `Zend_Filter_Exception` when the extension is missing. Use `Zend_Filter_Encrypt_Openssl`. Its tests stay skipped, as upstream.

### Other changes

- No public signature changes.
- The compress adapters (`Bz2`, `Gz`, `Rar`, `Tar`, `Zip`) no longer pass strings containing NUL bytes to `file_exists()`, which throws `ValueError` on current PHP versions; binary content is now compressed or decompressed as data.
- `Zend_Filter_Encrypt_Openssl` still uses RC4, which OpenSSL 3 and later only provide with the legacy provider. Tests that need RC4 are skipped when it is missing (previously they were skipped on every OpenSSL 3 build). One assertion of `testInvalidDecryption` is skipped on OpenSSL with RSA implicit rejection (3.2+).
- Dev dependencies upgraded (PHPUnit 13, PHPStan 2.3, php-cs-fixer 3.95, GrumPHP 2.27). Dropped `composer-require-checker`, which has no release for PHP 8.6.
- Tests migrated to PHPUnit 13 attributes; a test that leaked an error handler now restores it. CI runs PHP 8.5 and 8.6.
