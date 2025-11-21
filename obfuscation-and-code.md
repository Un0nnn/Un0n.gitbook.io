# Obfuscation & Code

Automated tools can simplify moderately obfuscated code, but heavily obfuscated or custom-encoded code becomes much harder to clean up. In such cases, manual reverse engineering is needed to understand the obfuscation and the code’s functionality.

#### [Direct link to heading](obfuscation-and-code.md#encoding-decoding) Encoding/Decoding

[**Direct link to heading**](obfuscation-and-code.md#base64) **Base64**

Converts any input (text/binary) into alphanumeric characters + `+` and `/` to reduce special characters. Only alphanumeric + `+`/`/` and padded with `=` to make length a multiple of 4.

Copy

```
echo "https://www.base64encoding.org/" | base64 # Encode
echo "kalGILjdp99HD7kWyuti55lpk/sfeev" | base64 -d # Decode
```

[**Direct link to heading**](obfuscation-and-code.md#hex) **Hex**

Converts each character to its ASCII hex code (e.g., `a = 61`, `b = 62`). Only hex characters `0-9` and `a-f`.

Copy

```
echo "https://www.hackthebox.eu/" | xxd -p # Encode
echo "8485sf848svmy37if939999kfo4fsj888sdc" | xxd -p -r # Decode
```

[**Direct link to heading**](obfuscation-and-code.md#caesar-cipher-rot13) **Caesar Cipher / Rot13**

Shifts letters by a fixed number (common: 13 for rot13). Text looks scrambled but has consistent letter mapping.

Copy

```
echo "https://example.com/page" | tr 'A-Za-z' 'N-ZA-Mn-za-m' # uggcf://rknzcyr.pbz/cntr
echo "uggcf://rknzcyr.pbz/cntr" | tr 'A-Za-z' 'N-ZA-Mn-za-m' # https://example.com/page
```

Hundreds of other encoding methods exist. First, identify the encoding type, then use online tools or Linux commands to decode. [Cipher Identifier](https://www.boxentriq.com/code-breaking/cipher-identifier) can automatically detect many encoding types.

[PreviousCommon Services & Protocols](common-services-and-protocols.md) [NextJavaScript](javascript.md)

Last updated 10 days ago
