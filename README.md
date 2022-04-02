# PKGBUILD for Msys2 LV2 SDK

Currently, Msys2 doesn't provide LV2 SDK. If you need to develop LV2 plugins under Microsoft Windows, you have to build by yourself.

Now, this PKGBUILD will help you out. It generates a Pacman package, making LV2 SDK portable, manageable. Better than simply running `waf install`.

**UPDATE:** Now (by 2022/4/2) Msys2 has official LV2 package. Simply install it by Pacman: 

```
pacman -Sy
pacman -S mingw-w64-x86_64-lv2 
```

Thanks [Alexandros Theodotou](https://github.com/alex-tee).

## Usage

1. Run Msys2 **MinGW64 shell**. 

   **DO NOT USE MSYS SHELL!** It uses Msys's POSIX-compatible compilers, which are incompatible with native Win32 environment.

2. Clone this repo. Make sure that you won't put other files in `PKGBUILD`'s directory.

3. Run `makepkg`:

   ```bash
   makepkg -f
   ```

4. Finally you will get a package file naming like `mingw-w64-x86_64-lv2-1.18.2-4-x86_64.pkg.tar.zst`. Install it via:

   ```bash
   pacman -U mingw-w64-x86_64-lv2-1.18.2-4-x86_64.pkg.tar.zst
   ```

SDK will be installed into `/mingw64`, and LV2 bundles will be put into `/opt/LV2`. You may need to copy the whole `/opt/LV2` into `C:\Program Files\Common Files\`.

## Notice

- Only `x86_64` is supported. Make sure that you have a 64-bit DAW or host.

