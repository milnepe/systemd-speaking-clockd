# systemd-speaking-clockd
Speaking clock daemon for testing **time-sync.target**

Units needing to start after system time has synchronised should be able to start After=time-sync.target - this is supposed to block until the system time as synchronised. It is not working in systemd prior to version xxx due to the following [bug - 5097](https://github.com/systemd/systemd/issues/5097)

**speaking-clockd** - simple daemon script that outputs timedatectl to stdout

**speaking-clock.service** - service unit for speaking-clock daemon which should start after system clock is synchronised due to *After=time-sync.target*

A work around is available [systemd-timesyncd-wait](https://github.com/LukeShu/systemd-timesyncd-wait) giving proper time-sync.target support for systemd-timesyncd

 > Notice: The latest versions of systemd in git (after v238) have
 > systemd-time-wait-sync.service; presumably it will be present in
 > systemd-239.  If you have systemd v239 or greater, you should use
 > systemd-time-sync-wait instead.

