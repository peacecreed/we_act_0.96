# WeAct 0.96" image / monitor cycle (for turing-smart-screen-python)

Small add-on for [turing-smart-screen-python](https://github.com/mathoudebine/turing-smart-screen-python)
that alternates the system monitor with a full-screen image, e.g. 15 s monitor, then 5 s image, then back.
Includes the `TM_0.96_Cyberpunk_V9_fixed` theme (80x160 portrait, WeAct 0.96").

## Files

| File | Change |
|------|--------|
| `main.py` | starts the cycle (one line) |
| `library/display.py` | new `display_fullscreen_image()` (stretch or letterbox, optional black bars) |
| `library/scheduler.py` | the cycle job; pauses stat updates while the image is shown, then redraws everything |
| `res/themes/TM_0.96_Cyberpunk_V9_fixed/` | theme + `special.jpeg` + `slideshow:` settings |

## Install

1. Back up your copies of `main.py`, `library/display.py`, `library/scheduler.py`.
2. Copy the files from this archive over the same paths in your turing-smart-screen-python folder
   (the theme folder goes in `res/themes/`).
3. In **your own** `config.yaml` set:
   ```yaml
   THEME: TM_0.96_Cyberpunk_V9_fixed
   REVISION: WEACT_B        # as used here; set what matches your screen
   COM_PORT: AUTO           # or your port, e.g. /dev/ttyACM0 or COM3
   ```
4. Run `python main.py`.

On Linux your user needs access to the serial port (e.g. the `dialout` group).

## Settings (`theme.yaml`)

```yaml
slideshow:
  IMAGE: special.jpeg      # image inside the theme folder
  FIT: stretch             # stretch = fill screen, letterbox = keep ratio with black bars
  BAR_HEIGHT: 3            # black bar (px) top and bottom when FIT is stretch
  IMAGE_SECONDS: 5
  MONITOR_SECONDS: 15
```

Remove the `slideshow:` block to disable the cycle. Themes without it behave exactly as before.
Weather and ping are not force-refreshed after each image; this theme uses neither.


