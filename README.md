# TinymceBundle

Bundle for connecting WYSIWYG editor TinyMCE to your Symfony2 project.
By analogy with the bundle https://github.com/ihqs/WysiwygBundle

## Installation

    git submodule add git://github.com/stfalcon/TinymceBundle.git vendor/bundles/Stfalcon/Bundle

Modify your autoloader if you didn't installer another Stfalcon Bundle yet.
Register namespace :

    // app/autoload.php
    $loader->registerNamespaces(array(
        // ...
        'Stfalcon'                       => __DIR__.'/../vendor/bundles',
    ));

Instantiate Bundle in your app/AppKernel.hpp file

    public function registerBundles()
    {
        $bundles = array(
            // ...
            new Stfalcon\Bundle\TinymceBundle\StfalconTinymceBundle(),
        );
    }

## Configuration

Configure your application

    // app/config.yml
    stfalcon_tinymce:
        theme:
            simple:
                mode: "textareas"
                theme: "advanced"
                theme_advanced_buttons1: "mylistbox,mysplitbutton,bold,italic,underline,separator,strikethrough,justifyleft,justifycenter,justifyright,justifyfull,bullist,numlist,undo,redo,link,unlink"
                theme_advanced_buttons2: ""
                theme_advanced_buttons3: ""
                theme_advanced_toolbar_location: "top"
                theme_advanced_toolbar_align: "left"
                theme_advanced_statusbar_location: "bottom"
                plugins: "fullscreen"
                theme_advanced_buttons1_add: "fullscreen"
            advanced:
                theme: "advanced"
                plugins: "pagebreak,style,layer,table,save,advhr,advimage,advlink,emotions,iespell,inlinepopups,insertdatetime,preview,media,searchreplace,print,contextmenu,paste,directionality,fullscreen,noneditable,visualchars,nonbreaking,xhtmlxtras,template"
                theme_advanced_buttons1: "save,newdocument,|,bold,italic,underline,strikethrough,|,justifyleft,justifycenter,justifyright,justifyfull,styleselect,formatselect,fontselect,fontsizeselect"
                theme_advanced_buttons2: "cut,copy,paste,pastetext,pasteword,|,search,replace,|,bullist,numlist,|,outdent,indent,blockquote,|,undo,redo,|,link,unlink,anchor,image,cleanup,help,code,|,insertdate,inserttime,preview,|,forecolor,backcolor"
                theme_advanced_buttons3: "tablecontrols,|,hr,removeformat,visualaid,|,sub,sup,|,charmap,emotions,iespell,media,advhr,|,print,|,ltr,rtl,|,fullscreen"
                theme_advanced_buttons4: "insertlayer,moveforward,movebackward,absolute,|,styleprops,|,cite,abbr,acronym,del,ins,attribs,|,visualchars,nonbreaking,template,pagebreak"
                theme_advanced_toolbar_location: "top"
                theme_advanced_toolbar_align: "left"
                theme_advanced_statusbar_location: "bottom"
                theme_advanced_resizing: true

run the command

    php app/console assets:install web/

to copy the resources to the projects web directory"

Add class "timymce" into textarea field to initialize TinyMCE.

    <textarea  class="tinymce"></textarea>

If, you want to change theme from "advanced" to "simple" you need to add tinymce attribute and configurate it.

    <textarea  class="tinymce" tinymce='{"theme":"simple"}'></textarea>  //Note the double quotes!

Add script to your templates/layout at the bottom of your page (for faster page display).

    {{ tinymce_init() }}