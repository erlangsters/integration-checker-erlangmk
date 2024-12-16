# Integration with Erlang.mk checker

The sole purpose of this repository is to check if all Erlangsters projects
integrates well with the Erlang.mk build system.

All projects it's checking.

- Term Validator
- Spawn Mode
- OTPless Worker
- OTPless Orchestrator
- OTPless Reactor

Instead of a thorough check for all platforms, all architectures and all
Erlang versions, it only checks using the latest stable 'erlang' image on Linux
as we assume that backward compatibility is maintained and we're mostly
interested in detecting issues early with the latest version of Erlang/OTP and
Erlang.mk build system.

## Checking a project

To check if a project integrates well, create a Makefile out of the Makefile.in
by replacing the `@project_name` and `@project_repo` with the values of the
project you want to check.

```sh
sed \
    -e 's/@project_name/etv/g' \
    -e 's/@project_repo/term-validator/g' \
    Makefile.in > Makefile
```

Then run `make`.

```sh
make
```

If it completes successfully, the project integrates well.

## Updating Erlang.mk periodically

Periodically, Erlang.mk must be updated to the latest version. To do that, run
this.

```bash
make erlang-mk
```

Then do a re-check of all projects.
