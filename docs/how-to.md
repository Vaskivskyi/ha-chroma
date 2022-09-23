# How-to

This section describes how to use different parts of the integration in the best possible way.

## Services

### Send Message

The Send Message service is used for symbol-to-symbol displaying of information on the keyboards with per-key RGB.

#### Parameters

- `message` - *(required)* a string of symbols to be displayed. Please, refer to the `message formatting` sections for more details.
- `spacing` - a time delay between symbols in seconds. The minimum spacing cannot be less than `0.05` s (50 ms). The default value is `0.5` s
- `color` - *(required)* an RGB color of an active symbol in the message.
- `background` - an RGB color of inactive symbols (background). The default value is black (`[0, 0, 0]`).
- `brightness` - a brightness of all the symbols (including active and inactive ones) in range from `0` to `255`. The default value is `255`.
- `tail` - length of the tail of a message. In case this value is above `0`, when a new symbol becomes active, the `tail` number of symbols are kept active as well and only `tail + 1` symbol is turned inactive. This feature is useful for the animations. The default value is `0`.
- `repeats` - number of times message should repeat. The default value is `1`.
- `sleep` - time between repeats of the message in seconds. Can be set to `0` for smooth cycled animations. Minimum step size is `0.05` s and maximum value is `10` s. The default value is `0.5` s.

#### Message formating

The `message` value of the service can except:
- any alpha-numeric symbol (`a-z`, `A-Z`, `0-9`) written directly.
- all symbols, accecible with or without use of `Shift` (e.g. `!@#$%^&*()-_=+\|/.,<>?`) written directly.
- any other key-name, including Numpad keys, written via their name in brackets `{}` (e.g. `{Shift}`, `{RCtrl}`, `{Num8}`).

#### Examples

**Simple string**

Any simple text messages can be send directly as a string:

```
A Lazy Fox came here and left this note for the Rabbit #3.
```

In this case, all the small letters, `3` and spaces will be shown as a single-key. For displaying of `A`, `L`, `F`, `R` and `#` a double-key will be used: `{Shift}` (the left one) and a correcponding small letter or `3`.

**Other buttons**

Other keys can be activated by adding their names to the `message` string. Known key names include:

- `{Esc}`, `{Tab}`, `{CapsLock}`, `{Shift}`, `{Ctrl}`, `{Win}`, `{Alt}`, `{Space}`, `{RAlt}`, `{Fn}`, `{Menu}`, `{RCtrl}`, `{RShift}`, `{Enter}`, `{Backspace}`
- `{PrtSc}`, `{ScrLk}`, `{Pause}`, `{Ins}`, `{Home}`, `{PgUp}`, `{Del}`, `{End}`, `{PgDn}`
- `{Up}`, `{Left}`, `{Down}`, `{Right}`
- `{Multi}` (multimedia keys), `{Volume}`,
- `{NumLock}`, `{Num/}`, `{Num*}`, `{Num-}`, `{Num+}`, `{NumEnter}`, `{Num.}`
- `{Num0}`, `{Num1}`, `{Num2}`, `{Num3}`, `{Num4}`, `{Num5}`, `{Num6}`, `{Num7}`, `{Num8}`, `{Num9}`
- `{F1}` - `{F12}`
