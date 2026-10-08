# FNSBASE

FNSBASE is a database of fission-neutron spectrum information used by the [AUTOTALYS](https://github.com/arjankoning1/autotalys) system for automated nuclear-data evaluation and processing. Its primary purpose is to provide prompt fission neutron spectra and associated data organized by nuclide.

This repository contains nuclear-data files and calculation inputs and results, rather than a standalone application.

## Repository structure

The top-level directories are named after individual nuclides, for example `U235` and `Pu239`. Metastable nuclides are identified with an `m` suffix where applicable.

An example for uranium-235 is:

```text
fnsbase/
└── U235/
    ├── input/
    │   ├── tanes.inp
    │   └── tanes.out
    ├── files/
    │   ├── n-U235.mf5
    │   ├── n-U235.delayed.mf5
    │   └── n-U235.mf35
    └── random/
        ├── n-U235.mf5.0000
        ├── n-U235.mf5.0001
        ├── n-U235.delayed.mf5.0000
        └── ...
```

The precise files present may vary between nuclides.

- **`input/`** contains calculation input and output files. For `U235`, these include `tanes.inp` and `tanes.out`.
- **`files/`** contains spectrum-related data components using ENDF-style file naming. For `U235`, `mf5` and `delayed.mf5` files are present, together with `mf35` covariance information. ENDF MF5 describes energy distributions of emitted particles, while MF35 is used for energy-spectrum covariances.
- **`random/`** contains numbered variants of the data files, suitable for workflows using sampled spectrum realizations.

Although the repository is centered on prompt fission neutron spectra, the U-235 directory also includes a file explicitly named for delayed-neutron spectral data. Interpret individual files according to the producing and consuming codes, rather than assuming that every file contains prompt-spectrum information.

## Obtaining the database

Clone the repository using Git:

```bash
git clone https://github.com/arjankoning1/fnsbase.git
```

To update an existing clone:

```bash
cd fnsbase
git pull
```

Alternatively, download a source archive from the repository's GitHub page.

## Use with AUTOTALYS

FNSBASE is a data resource for the broader AUTOTALYS workflow. It should be placed where the installed AUTOTALYS tools expect to find the fission neutron spectrum database. The installation location is not required to be under the user's home directory; it depends on the AUTOTALYS setup.

## Data provenance and updates

Fission neutron spectra and their uncertainties can depend on the underlying evaluation and model assumptions. When using or updating data, retain source attribution, document changes, and take care to distinguish reference files from numbered sampled variants.

## Related repositories

- [AUTOTALYS](https://github.com/arjankoning1/autotalys) — bootstrap scripts for the complete system
- [RESBASE](https://github.com/arjankoning1/resbase) — resonance-parameter database
- [NUBARBASE](https://github.com/arjankoning1/nubarbase) — average neutron multiplicity database
- [TALYS](https://github.com/arjankoning1/talys) — nuclear reaction modelling
- [TEFAL](https://github.com/arjankoning1/tefal) — evaluated nuclear-data file processing
- [TASMAN](https://github.com/arjankoning1/tasman) — sensitivity and uncertainty analysis

## License

Refer to the repository's `LICENSE` file for applicable terms, if provided. The rights to any third-party source data remain subject to their respective conditions.

## Author

Arjan Koning
