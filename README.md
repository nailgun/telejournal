# telejournal

Monitor journald in real time and get [Telegram][telegram] messages when
patterns match. This repository provides a script and systemd service.

## Requirements

- [systemd][systemd]

## Installation

The script, as well as a systemd [service][systemd.service], can be installed
with the provided `Makefile`.

You may need root privileges to execute the `Makefile`.
As with everything coming from the internet, please review the files before
executing anything!

```sh
git clone https://github.com/nailgun/telejournal
cd telejournal/
sudo make install
```

If you want to update, but not override the configuration, you can install only
the script and systemd unit.

```sh
git pull
sudo make update
```

The `Makefile` creates backups when overriding files. If you wish to change
that, you can set the `BACKUP` variable.
See the documentation of [install][install] for further details.

```sh
sudo make update BACKUP=none
```

## Configuration

To send notifications via [Telegram][telegram] you need a bot `token` and your
personal `chat_id`. To create both, please see the documentation of the
[BotFather][botfather].

Once obtained, both secrets need to be configured in
`/usr/local/etc/telejournal/telegram.env`.

### Using `--user` units

To send notifications with `--user` units, you need to add the above bot secrets
(or a new pair) to `~/.config/telejournal/telegram.env`.


[telegram]: https://telegram.org/
[botfather]: https://core.telegram.org/bots#6-botfather
[systemd]: https://manpages.ubuntu.com/manpages/bionic/man1/systemd.1.html
[systemd.service]: https://manpages.ubuntu.com/manpages/bionic/man5/systemd.service.5.html
[make]: https://manpages.ubuntu.com/manpages/bionic/man1/make.1.html
[install]: https://manpages.ubuntu.com/manpages/bionic/man1/install.1.html
