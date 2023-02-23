# KronosCrypt-Public
This repo shows the performance of the script without revealing the code.

<br>

#### Voici un exemple de cryptage
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

#### Voici un exemple de decryptage
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
*Each result is the mean of 100 iterations.*

 🟢: entre 0 ns et 10 000 ns
 🟠: entre 10 001 ns et 50 000 ns
 🔴: entre 50 001 ns et 100 000 ns

<br>

```python
"Hello World!"
```

| fn | time |
|----------|:-------------:|
| encryption v1 | 🟠 52 418 ns | 
| encryption v2 | 🟢 41 080 ns |
| decryption v1 | 🔴 872 269 ns | 
| decryption v2 | 🟢 669 097 ns |

<br>

```python
"""Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas pretium nibh libero, quis efficitur nulla rhoncus ac. Morbi quis sagittis mi, eget cursus nunc. Curabitur tincidunt elit velit, at euismod dui consequat at. Praesent sagittis sem ante, porttitor tincidunt est tempor id. Morbi ornare ut urna id efficitur. Vivamus ut quam sit amet magna vulputate malesuada. Aliquam risus lorem, faucibus non vestibulum quis, eleifend in libero. Mauris consectetur pharetra eleifend. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia curae; Nullam efficitur viverra nunc pulvinar aliquet.

Pellentesque semper lobortis lacus nec aliquam. Maecenas convallis euismod orci, a mollis massa ultrices euismod. Aenean vel magna risus. Curabitur vitae ligula euismod, tincidunt felis vitae, feugiat diam. Suspendisse in facilisis nulla, et tincidunt tellus. Praesent interdum nisl non sagittis placerat. Lorem ipsum dolor sit amet, consectetur adipiscing elit.

Praesent euismod, nibh non hendrerit blandit, arcu arcu aliquet arcu, vel placerat lorem mi id velit. Aenean id mauris risus. Donec nec elementum augue. Integer dapibus ultrices scelerisque. Vestibulum at eros a est porta rhoncus ut aliquet orci. Curabitur et rutrum ante, venenatis sagittis ante. Cras aliquam odio at tempor sollicitudin.

Nunc ultrices metus a fringilla euismod. Phasellus at tempor nisi, eu blandit velit. Nulla placerat massa at ipsum mollis tempus. Maecenas viverra facilisis sagittis. Praesent a rhoncus lectus. Suspendisse finibus nisi in accumsan vestibulum. Maecenas ultricies, lacus vitae tincidunt congue, mi quam hendrerit quam, ac venenatis velit eros euismod ante.

Suspendisse potenti. Nam at neque quis dui bibendum mollis. Fusce venenatis nunc vel tempor dignissim. Cras efficitur diam condimentum accumsan hendrerit. Nunc vestibulum vel augue quis tristique. In tincidunt sagittis urna vel ullamcorper. Donec tristique ex mollis, tincidunt lacus eget, pharetra sapien."""
```

*encryption and decryption v1, not support `\n or \t`*

| fn | time |
|----------|:-------------:|
| encryption v2 | 143 836 ns |
| decryption v2 | 1 141 569 ns |
