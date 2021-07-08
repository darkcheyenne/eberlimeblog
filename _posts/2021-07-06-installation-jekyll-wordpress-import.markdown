---
layout: post
title:  "Installation von Jekyll Wordpress Import auf Ubuntu 20.04"
date:   2021-07-06 11:55:00 +0100
categories: jekyll wordpress
---
Update des Repositories und der Pakete
    apt-get update & apt-get upgrade

Installation von Devel-Tools:
    apt-get install ubuntu-dev-tools ruby-dev ruby

Installation von Jekyll Import:
    gem install jekyll-import
    
Start von Import:
    ruby -r rubygems -e 'require "jekyll-import";
    JekyllImport::Importers::WordpressDotCom.run({
    "source" => "wordpress.xml",
    "no_fetch_images" => false,
    "assets_folder" => "assets"
    })'