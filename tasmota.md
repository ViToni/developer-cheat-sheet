# Tasmota cheat sheet

[Tasmota](https://github.com/arendst/Tasmota) is great to "free" ESP8266-based smart plugs which have not so smart software.

[Tasmota documentation](https://tasmota.github.io/docs/#/Home)

## Connect UART interface

[Connecting UART](https://esphome.io/devices/sonoff_s20.html#step-2-connecting-uart)

## Configure LEDs

### Use LED only to show powerstate

```{r, engine='bash', count_lines}
LedState 1
```

See: [LedState](https://tasmota.github.io/docs/#/Commands?id=ledstate)

### Do not show WiFi / MQTT state using LED

```{r, engine='bash', count_lines}
SetOption31 1
```

See: [SetOption31](https://tasmota.github.io/docs/#/Commands?id=setoption31)

## Network

### Activate mDNS service announcement

```{r, engine='bash', count_lines}
SetOption55 1
```

See: [SetOption55](https://tasmota.github.io/docs/#/Commands?id=setoption55)

### Select WiFi with strongest signal on restart

```{r, engine='bash', count_lines}
SetOption56 1
```

See: [SetOption56](https://tasmota.github.io/docs/#/Commands?id=setoption56)
