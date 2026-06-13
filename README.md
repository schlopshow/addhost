```bash
sudo cp addhost /usr/local/bin/addhost
sudo chmod +x /usr/local/bin/addhost
sudo chown root:root /usr/local/bin/addhost
sudo chmod 755 /usr/local/bin/addhost
```

**Usage:**
```bash
htbhosts add  10.129.12.68 editorial.htb          # add manually
htbhosts add  10.129.12.68 editorial.htb dev.editorial.htb  # multiple hostnames
htbhosts auto 10.129.12.68                         # detect hostname automatically
htbhosts rm   editorial.htb                        # remove by hostname
htbhosts rm   10.129.12.68                         # or by IP
htbhosts list                                      # show all non-default entries
```

**What `auto` checks (in order):**
1. HTTP redirect `Location:` header
2. HTTPS redirect `Location:` header
3. SSL certificate CN / SAN fields
4. HTML body links pointing to a non-IP hostname

It also **deduplicates** on `add` — if the IP already exists it removes the old line first, so you never end up with stale entries when a box resets to a new IP.
