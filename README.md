Add the `heroku-buildpack-apt` buildpack to your project:

```
heroku buildpacks:add --index 1 https://github.com/heroku/heroku-buildpack-apt.git
```

Add our LibreOffice buildpack to your project:

```
heroku buildpacks:add --index 2 https://github.com/gwendalbrossard/buildpack-libreoffice.git
```

Optionally, add the following buildpack, which provides a handy combination of fonts for LibreOffice to use:

```
heroku buildpacks:add --index 3 https://github.com/debitoor/heroku-buildpack-converter-fonts.git
```

Create an `Aptfile` file in your project root with the following content (do **not** include libreoffice here):

```
libsm6
libice6
libxinerama1
libdbus-glib-1-2
libharfbuzz0b
libharfbuzz-icu0
libx11-xcb1
libxcb1
```

Optionally, create a `LibreOfficeAppImage` file in your application repository to change the installed version to something other than the latest `fresh`.
The file should contain only the full URL of a LibreOffice AppImage, from the [official links found here](https://libreoffice.soluzioniopen.com/).
For example the latest `still` can be installed with:

```
https://libreoffice.soluzioniopen.com/stable/still/LibreOffice-still.basic-x86_64.AppImage
```

Redeploy your project after committing the above, et voilà...!
