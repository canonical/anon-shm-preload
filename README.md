# Use

Add this as a part to your `snapcraft.yaml`:

```yaml
parts:
    anon-shm-preload:
        source: https://github.com/wmww/snapcraft-preload.git
        source-branch: anon-shm
        plugin: cmake
```

And precede your `apps` entry like this:

```yaml
apps:
    app-name:
        command: bin/anon-shm-preload $SNAP/<binary>
```

If you're using the `desktop-launch` launcher from the [ubuntu/snapcraft-desktop-helpers](https://github.com/ubuntu/snapcraft-desktop-helpers), place `anon-shm-preload` _after_ `desktop-launch` in the app command.
