# Web utilities for the gaia-2 testnet

## Set up Gaia CLI for gaia-2

First backup your `.cosmos-gaia-2-cli` directory if there is one. You want to keep your `.cosmos-gaia-2-cli/keys` where your existing account keys are stored.

Initialize your `gaia client` utility to the testnet.

```
gaia client init --chain-id=gaia-2 --node=tcp://gaia-2-node0.testnets.interblock.io:46657 --home=/home/user/.cosmos-gaia-2-cli
```

You can now copy back your old keys into `.cosmos-gaia-2-cli/keys` or create new ones. Some of those accounts should have a lot of coins to give out.

```
$ gaia client keys new mytest
Enter a passphrase:test123
Repeat the passphrase:test123
mytest		F75D0...2
**Important** write this seed phrase in a safe place.
It is the only way to recover your account if you ever forget your password.

$ gaia client keys list
All keys:
mytest		F75D0...2
```

---

## Deploy the PHP script

Fix the variables based on your system setup. Get your Google ReCaptcha credentials here: https://www.google.com/recaptcha/intro/.

```
  $home_dir = "/home/myuser";
  $go_path = "/home/myuser/go/bin";
  $from_acct = "mytest";
  $from_pass = "thepassword";

  $recaptcha_secret = "google_recaptcha_secret";
  $recaptcha_key = "google_recaptcha_key";
```

Run Apache as the user who installed `gaia`. In the `httpd.conf` file, change the following, and restart the server.

```
User myuser
Group mygroup
```

Disable SELinux

```
sudo setenforce 0
```
