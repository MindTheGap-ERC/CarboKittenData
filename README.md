# CarboKittenData
Auxiliary data files for use with CarboKitten.

The [CarboKitten](https://MindTheGap-ERC.github.io/CarboKitten.jl) packge has convenience functions to load external data sets like eustatic sea level and insolation curves. These files are stored in this separate repository for use with [Julia's `Artifact` API](https://pkgdocs.julialang.org/v1/artifacts/#The-Pkg.Artifacts-API).

Contents:

- Cenozoic sea-level curve by [Miller 2020](https://doi.org/10.1594/PANGAEA.923126).
- Sea-level curve for reproducing [Bosscher & Schlager 1992](https://doi.org/10.1111/j.1365-3091.1992.tb02130.x) (including subsidence), extracted from a plot in that paper.

## Artifacts in Julia
The CarboKitten package references specific versions of this data, so that runs are always reproducible. We need hashes of the contents of this repository. From Julia's documentation:

```julia
using Tar, Inflate, SHA

filename = "CarboKittenData.tar.gz"
println("sha256: ", bytes2hex(open(sha256, filename)))
println("git-tree-sha1: ", Tar.tree_hash(IOBuffer(inflate_gzip(filename))))
```

## Adding new data

1. Add the data to this repository.
2. Create a new release of `CarboKittenData`.
3. Refer to the newly released dataset in CarboKitten's `Artifact.toml`.
4. Create a new release of `CarboKitten.jl`.

## Todo
Integrate with Zenodo.
