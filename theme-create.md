# Theme for AvoRed E commerce

- [Theme Createtion](#create-theme)
    - [Folder Structure](#themes-folder-structure)
    - [register.yaml](#themes-register-file)
    - [assets](#themes-assets)
    - [views](#themes-views)

<a name="create-theme"></a>
### Create Theme
Theme development is one of the key component in enhancement of AvoRed E commerce frontend.

<a name="themes-folder-structure"></a>

### Folder Strucuture

- themes
  - vendor-name (avored) 
      - theme-name
           - assets
               - js
             - css 
             - fonts
         - images
        - views
        - register.yaml
              

<a name="themes-register-file"></a>    
### Register Yaml File                  
 
Register.yaml file the key to register most related path and information about the theme. Things that needs to be careful here is your identifier neeeds to be unique.

    identifier: avored-material
    asset_folder_name: assets
    lang_folder_name: lang
 
Once you have an theme register and files setup then you can go to admin=>system=>themes and Activate theme publish all the css/js/images into public/vendor/theme-identifier folder for you. 

<a name="themes-assets"></a>   

### Theme Assets (Using and css/js) into layout files

Once you have theme activate and moved all your css/js/images into public folder then you can simply just it.

How to add Css into layout files.

    <link href="{{ asset('vendor/avored-material/css/bootstrap.min.css') }}" rel="stylesheet">
    
How to add Javascript into layout files.

    <script src="{{ asset('/vendor/avored-material/js/jquery-3.2.1.slim.min.js') }}"></script>
    
