# Theme for AvoRed E commerce

* [Theme Createtion](theme-create.md#create-theme)
  * [Folder Structure](theme-create.md#themes-folder-structure)
  * [register.yaml](theme-create.md#themes-register-file)
  * [assets](theme-create.md#themes-assets)
  * [views](theme-create.md#themes-views)

## Create Theme

Theme development is one of the key component in enhancement of AvoRed E commerce frontend.

## Folder Strucuture

* themes
  * vendor-name \(avored\) 
    * theme-name
      * assets
        * js
          * css 
          * fonts
          * images
          * views
          * register.yaml

## Register Yaml File

Register.yaml file the key to register most related path and information about the theme. Things that needs to be careful here is your identifier neeeds to be unique.

```text
identifier: avored-material
asset_folder_name: assets
lang_folder_name: lang
```

Once you have an theme register and files setup then you can go to admin=&gt;system=&gt;themes and Activate theme publish all the css/js/images into public/vendor/theme-identifier folder for you.

## Theme Assets \(Using and css/js\) into layout files

Once you have theme activate and moved all your css/js/images into public folder then you can simply just it.

How to add Css into layout files.

How to add Javascript into layout files.

