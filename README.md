# KronosCrypt-Public
This repo shows the performance and capabilities of the script without revealing the code.

<br>

#### Here is an example of encryption
```python
d_message = "Hello World !"

encryption = True
crypt = KronosCrypt(message=d_message)

print('----------------')
print(f"{Fore.YELLOW}- - {crypt.getKey()} - -{Fore.RESET}")
print(crypt.getEncryption())
print(f"{Fore.GREEN}Temps d'execution : {crypt.getDuration()}ns ({crypt.getDuration()/1e+6}ms){Fore.RESET}")
print('----------------')
```

```text
----------------
- - q.0.?.~ - -
$$")+@@@1A+j"m@<g*j`Z@<g*j`Z@3i0=KI $EE2aJa@3i0=KI@Beq>1c@<g*j`Z@#m<g== %iaFF0?       <-- le message crypter
Temps d'execution : 60135ns (0.060135ms)
----------------
```

#### Here is an example of decryption

```python
c_message = "$$\")+@@@1A+j\"m@<g*j`Z@<g*j`Z@3i0=KI $EE2aJa@3i0=KI@Beq>1c@<g*j`Z@#m<g== %iaFF0?"

encryption = False
crypt = KronosCrypt(message=c_message)

print('----------------')
print(f"{Fore.YELLOW}- - {crypt.getKey()} - -{Fore.RESET}")
print(crypt.getDecryption())
print(f"{Fore.GREEN}Temps d'execution : {crypt.getDuration()}ns ({crypt.getDuration()/1e+6}ms){Fore.RESET}")
print('----------------')
```

```text
----------------
- - q.0.?.~ - -
Hello World !       <-- le message decrypter
Temps d'execution : 694592ns (0.694592ms)
----------------
```

The encrypted result can be compressed via zlib.

## Perfomances
> *Each result is the mean of 100 iterations.*
> 
> 🟢: between 0 ns and 10 000 ns, 🟠: between 10 001 ns and 50 000 ns, 🔴: over 50 001 ns

<br>

```python
"Hello World!"
```

| fn                                                      |     time     |
| ------------------------------------------------------- | :----------: |
| encryption v1                                           | 🔴 52 418 ns  |
| encryption v2 + cache                                   | 🟠 41 080 ns  |
| encryption v2.1                                         | 🟠 35 393 ns  |
| encryption v2.1 + cache                                 | 🟢  2 609 ns  |
| encryption v2.1 + cache (cache flush at each iteration) | 🟠 27 546 ns  |
|                                                         |              |
| decryption v1                                           | 🔴 872 269 ns |
| decryption v2 + cache                                   | 🟠 16 567 ns  |
| decryption v2.1                                         | 🔴 372 245 ns |
| decryption v2.1 + cache                                 | 🟠 12 767 ns  |
| decryption v2.1 + cache (cache flush at each iteration) | 🟠 13 977 ns  |

<br>

```python
"""Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas pretium nibh libero, quis efficitur nulla rhoncus ac. Morbi quis sagittis mi, eget cursus nunc. Curabitur tincidunt elit velit, at euismod dui consequat at. Praesent sagittis sem ante, porttitor tincidunt est tempor id. Morbi ornare ut urna id efficitur. Vivamus ut quam sit amet magna vulputate malesuada. Aliquam risus lorem, faucibus non vestibulum quis, eleifend in libero. Mauris consectetur pharetra eleifend. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia curae; Nullam efficitur viverra nunc pulvinar aliquet.

Pellentesque semper lobortis lacus nec aliquam. Maecenas convallis euismod orci, a mollis massa ultrices euismod. Aenean vel magna risus. Curabitur vitae ligula euismod, tincidunt felis vitae, feugiat diam. Suspendisse in facilisis nulla, et tincidunt tellus. Praesent interdum nisl non sagittis placerat. Lorem ipsum dolor sit amet, consectetur adipiscing elit.

Praesent euismod, nibh non hendrerit blandit, arcu arcu aliquet arcu, vel placerat lorem mi id velit. Aenean id mauris risus. Donec nec elementum augue. Integer dapibus ultrices scelerisque. Vestibulum at eros a est porta rhoncus ut aliquet orci. Curabitur et rutrum ante, venenatis sagittis ante. Cras aliquam odio at tempor sollicitudin.

Nunc ultrices metus a fringilla euismod. Phasellus at tempor nisi, eu blandit velit. Nulla placerat massa at ipsum mollis tempus. Maecenas viverra facilisis sagittis. Praesent a rhoncus lectus. Suspendisse finibus nisi in accumsan vestibulum. Maecenas ultricies, lacus vitae tincidunt congue, mi quam hendrerit quam, ac venenatis velit eros euismod ante.

Suspendisse potenti. Nam at neque quis dui bibendum mollis. Fusce venenatis nunc vel tempor dignissim. Cras efficitur diam condimentum accumsan hendrerit. Nunc vestibulum vel augue quis tristique. In tincidunt sagittis urna vel ullamcorper. Donec tristique ex mollis, tincidunt lacus eget, pharetra sapien."""
```

> *encryption and decryption v1, not support `\n or \t`*
> 
> 🟢: between 0 ns and 250 000 ns, 🟠: between 250 001 ns and 1 000 000 ns, 🔴: over 1 000 001 ns

<br>

| fn                                                      |      time       |
| ------------------------------------------------------- | :-------------: |
| encryption v2 + cache                                   | 🟠   300 583 ns  |
| encryption v2.1                                         | 🔴 5 030 673 ns  |
| encryption v2.1 + cache                                 | 🟢   220 408 ns  |
| encryption v2.1 + cache (cache flush at each iteration) | 🟠   322 574 ns  |
|                                                         |                 |
| decryption v2 + cache                                   | 🔴 1 481 509 ns  |
| decryption v2.1                                         | 🔴 63 397 358 ns |
| decryption v2.1 + cache                                 | 🔴 1 399 248 ns  |
| decryption v2.1 + cache (cache flush at each iteration) | 🔴 1 498 498 ns  |
