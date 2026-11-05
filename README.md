# Name edit fix for Open77 client running on proton

example instructions for my install using "Proton - Experimental" running through steam, you may need to target your own proton version and I can't promise this will work for your system

1. get the ncrypt.dll file out of this repo

2. backup your existing ncrypt.dll file
`mv ~/.local/share/Steam/steamapps/common/Proton\ -\ Experimental/files/lib/wine/x86_64-windows/ncrypt{.dll,.dll.bak}`

3. copy in the updated ncrypt.dll file
`cp ncrypt.dll ~/.local/share/Steam/steamapps/common/Proton\ -\ Experimental/files/lib/wine/x86_64-windows/ncrypt.dll`

4. the launcher should now allow you to update your name and save it



when steam updates, it will overwrite this ncrypt.dll file and you will lose the ability to save your name again.


## Misc Notes

If this doesn't work for you, just rename the ncrypt.dll.bak back to ncrypt.dll

This was built against the valve proton bleeding-edge branch on 2026-11-04 but I tested it with other proton versions and they worked fine for me

I'm running the Open77 launcher through steam, with compatibility set to `Proton Experimental` and the following launch options:
`STEAM_COMPAT_DATA_PATH=/home/<MY USERNAME HERE>/.local/share/Steam/steamapps/compatdata/1091500 %command%`

The change was to land this commit and other ncrypt updates from the upstream wine https://gitlab.winehq.org/wine/wine/-/commit/f0d380f2ba0b4811668320fa90aae106ab12e24b#line_54f07b1af_158 to add support for BCRYPT_ECDSA_PRIVATE_P256_MAGIC
