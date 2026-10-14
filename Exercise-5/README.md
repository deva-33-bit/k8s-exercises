# Exercise 5: Docker Security with AppArmor and Python

Apply an AppArmor profile to a Flask container using the Docker SDK for Python, then test that restricted actions are blocked.

## Files

| File | Purpose |
|---|---|
| `app.py` | Flask app on port 5000 |
| `Dockerfile` | Builds the `flask-apparmor` image |
| `my-apparmor-profile` | AppArmor profile (deny /etc/passwd, /var writes, exec in /bin and /usr/bin) |
| `apply_apparmor.py` | Builds, runs with the profile and prints `HostConfig.SecurityOpt` |
| `test_restricted_actions.py` | Tries `cat /etc/passwd` and `/bin/bash` inside the container |

## Steps (Linux host with AppArmor)

1. Load the profile: `sudo apparmor_parser -r my-apparmor-profile`
2. Build: `docker build -t flask-apparmor .`
3. Run: `docker run --security-opt="apparmor=my-apparmor-profile" -p 5000:5000 flask-apparmor`
4. SDK: `pip install docker` then `python apply_apparmor.py`
5. Test: `python test_restricted_actions.py`

## What I ran on Windows

- Built the image and ran the app with Docker Desktop.
- Ran `apply_apparmor.py`, which printed `AppArmor profile applied: ['apparmor=my-apparmor-profile']`.
- `docker info` on this machine shows only `seccomp`, so AppArmor is not active. That output shows the profile was requested, not that it was enforced. The blocked-action test needs a Linux host with AppArmor (not run here).

## Questions and answers

1. **Purpose of AppArmor with Docker:** it confines a container to a limited set of files, networks and capabilities, adding a layer beyond namespaces.
2. **How profiles help:** they define what the process may read, write, execute and which capabilities it can use.
3. **Why restrict /etc and /var:** they hold system configuration, credentials and logs. Blocking them limits damage if the app is compromised.
4. **Other restrictions:** network access, file writes, execution of binaries and capabilities such as `sys_admin`.
5. **Verifying:** `docker inspect` shows `HostConfig.SecurityOpt`, and `aa-status` on the host lists the loaded profile.
