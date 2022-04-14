`shm_open()` often doesn't play nice with snaps, this library (similar to [snapcraft-preload](https://github.com/sergiusens/snapcraft-preload)) overrides `shm_open()` using `memfd_create()` to make a shared memory fd without an associated file path.

# To use

Add this as a part to your `snapcraft.yaml`:

```yaml
parts:
    anon-shm-preload:
        source: https://github.com/MirServer/anon-shm-preload.git
        plugin: cmake
```

And append to your `apps.command-chain` entry like this:

```yaml
apps:
    app-name:
      command-chain:
        // ...
        - bin/anon-shm-preload
    command: <app-binary>
```

If you're using the `desktop-launch` launcher from the [ubuntu/snapcraft-desktop-helpers](https://github.com/ubuntu/snapcraft-desktop-helpers), place `anon-shm-preload` _after_ `desktop-launch` in the app command.
