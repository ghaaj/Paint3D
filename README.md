# Paint3D
R.I.P. Paint 3D 🕊

## Install
### Download from this repository
Download the version of the package you want to install from the [packages directory](packages) and then double-click to install the `.appxbundle` package. (`.BlockMap` files are not needed.)

Version 2023.2310.24037.0 or earlier is recommended because later versions have [the problem that the "Open with" context menu is missing/broken](https://answers.microsoft.com/en-us/windows/forum/all/how-do-i-add-paint-3d-to-the-open-with-menu/14ad161e-a11c-4566-a4af-154f8e543ce0).

### Download directly from dl.delivery.mp.microsoft.com
1. Clone this repository and clean up the `packages` directory

   ```sh
    git clone https://github.com/ghaaj/Paint3D.git
    cd Paint3D
    rm packages/*
    ```
3. Install dependencies
    
    - [Amber](https://docs.amber-lang.com/getting_started/installation)
    - [jq](https://jqlang.github.io/jq/download)
    - [hq](https://github.com/orf/html-query/?tab=readme-ov-file#install)

4. Start the FlareSolverr server

    ```sh
    export FLARESOLVERR_PORT=8191
    docker run -d --rm \
      --name=flaresolverr \
      -p $FLARESOLVERR_PORT:8191 \
      -e LOG_LEVEL=info \
      --restart unless-stopped \
      ghcr.io/flaresolverr/flaresolverr:latest
    ```
5. Compile and run `fetch-packages.ab`

    You can edit `requests.json` to customize the packages to download.
    ```sh
    amber ./fetch-packages.ab ./fetch-packages.sh
    ./fetch-packages.sh ./requests.json
    ```

## Dependencies
- [Online link generator for Microsoft Store](https://store.rg-adguard.net)
- [amber-lang/amber](https://github.com/amber-lang/amber)
- [FlareSolverr/FlareSolverr](https://github.com/FlareSolverr/FlareSolverr)
- [orf/html-query](https://github.com/orf/html-query)
- [jqlang/jq](https://github.com/jqlang/jq)

## Additional information
- The `.appxbundle` file is a ZIP archive
- The `.BlockMap` file is a CAB archive
