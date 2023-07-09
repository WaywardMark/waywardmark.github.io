---
layout: post
title: Supercharge Your Jekyll Website with Stunning Photo Galleries
subtitle: An image gallery in Jekyll without plugins
thumbnail-img: /assets/img/photo_gallery.png
tags: [how-to, jekyll]
---

Jekyll is a static web site generator built using Ruby, providing a dynamic way to construct websites using a combination of markdown, templates, and HTML. It utilizes Liquid, a templating language, to generate HTML content using predefined templates, employing double curly braces (e.g., {{ variable }}) to output content that can be combined with regular HTML to construct web pages. When combined with CSS, Jekyll becomes a versatile tool for creating various web page layouts. This site is developed using Jekyll and hosted on GitHub Pages for free. Prior familiarity with Jekyll is recommended before delving into this topic.

#### Galleries
Jekyll allows you to add image galleries to your website, usually with the help of plugins. However, in this example, we won't use any plugins so that it can work on platforms like GitHub Pages, which have limited plugin support. Instead, you can create views in the _includes folder of your Jekyll site and use them on different pages.

#### Set variables in _config.yml
In the Jekyll configuration file, we can define variables that will be available within the template. These variables store the names of our image folders and thumbnail folders. To ensure they work together, the image file names in both folders should be identical.

```imagesurl: "/mysite/img/"```  
```thumbsurl: "/mysite/thumbs/"```

For creating thumbnails from images, I recommend using tools like ImageMagick or GraphicsMagick. These tools have a command-line interface and can help you resize and generate thumbnails easily. They are widely used, well-documented, and supported by a helpful community, making them reliable options for creating thumbnails efficiently.
For example using imagemajick: mogrify -path thumbs -resize 20% images/*


#### CSS
The following css formats the div elements that make the gallery. It can be included inline in the view or in the assets/css folder. The ‘.img-gallery’ style is to keep the images the same square shape as they appear in the div block.
```css
   /*! div style */
  .image-gallery {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(auto-fill,minmax(200px, 1fr));
    justify-content: center;
    padding: 4px;
  }

  .box {
      flex-basis: 25%;
      width: 100%;
      padding: 10px;
      margin: 2px;
  }

  .img-gallery {
	width: 100%;
  height: 200px;
	object-fit: cover;
  transform: scale(1);
  transition: all 0.3s ease-in-out;
  &:hover {
    transform: scale(1.05);
  }
  }
```
HTML view
Templates that are called ‘partial views’ are usually placed in the _includes folder. include.folder is the variable name passed to the include statement when we embed this view. This code iterates over the site files and if they are in the target folder and are png files, they are displayed. Each image is a div element inside a larger div. Note that the image shown is a thumbnail linked to the real image. It assumes the thumb filename matches the real one. We save this as `_includes\my-gallery.html` or whatever you wish.

```liquid
  <div class="image-gallery">
    { % assign sorted = site.static_files | sort: 'date' | reverse %}
    { % for file in sorted %}
     { % assign include_folder = '/mysite/thumbs/' %}   
      { % if file.path contains include_folder %}
       { % if file.extname == '.jpg' %}
           { % assign filenameparts = file.path | split: "/" %}
           { % assign filename = filenameparts | last | replace: file.extname, "" %}
           { % assign img_path = '/mysite/img/' | append: filename | append: ".jpg" %}
           <div class="box">                
               <a href="{{ img_path | relative_url }}" title="{{ filename }}">
               <img src="{{ site.baseurl }}{{ include_folder }}{{ file.name }}" alt="{{ filename }}" class="img-gallery" />
               </a>
            </div>
        { % endif %}
      { % endif %}
    { % endfor %}
   </div>

   Note: In the above code I had to place a space after each { to keep the webpage from running the Liquid code.  To use the above code remove space.
```

We then insert this view into any page using:


```plaintext
{ % include my-gallery.html folder="myfolder" %}
```

When the above code is processed and rendered by Jekyll, it generates an image gallery on the webpage. The gallery displays thumbnail images with links to their corresponding full-size images, creating an interactive and visually appealing image browsing experience.


View my [Photography](/photo) page for an example.


In Jekyll, there are multiple approaches to accomplish a particular objective. While this method is straightforward, it lacks certain features such as pagination.