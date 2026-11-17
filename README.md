# trebol-es

The rules of a Spanish form for [Trebol](https://github.com/acasadom/trebol): NIF, DNI, NIE, CIF and
postal codes.

```sh
npm install trebol-es
```

A program that imports the package writes the rules after its fields, as it writes `email`:

```trebol
import 'trebol-es

view [
    form [
        field id "NIF" required nif
        field company "CIF" cif
        field cp "Código postal" postal-code
        submit "Save" [toast "Saved"]
    ]
]
```

| Rule          | Function        | What it takes                                                             |
| ------------- | --------------- | ------------------------------------------------------------------------- |
| `dni`         | `dni?`          | eight digits and their letter: `12345678Z`                                |
| `nie`         | `nie?`          | X, Y or Z, seven digits and their letter: `X1234567L`                     |
| `cif`         | `cif?`          | the NIF of a company or other body: its kind, seven digits and the check |
| `nif`         | `nif?`          | any of them, and the NIF that starts with K, L or M                       |
| `postal-code` | `postal-code?`  | five digits, the first two a province from 01 to 52                       |

Spaces, dots and dashes are fine, and small letters: `12.345.678-z` is a DNI. The rules check that the
number is well made, not that it belongs to someone. Each message is in English and Spanish, and an app may
change it in `i18n/ui`, as any other: `poke i18n/ui 'nif #(es: "Ese NIF no es correcto")`.

The functions work without forms too: `nif? "X1234567L"` is true.

## Tests

```sh
npm test
```
