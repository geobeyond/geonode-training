# Programmatically Customize the Look-and-Feel
In this section we will change the look and feel of GeoNode, in particular we will do some customization to help understanding how the template inheritance works and how to add new stuff to your GeoNode. The changes will include the home page, the top menu, the footer and a generic GeoNode page.

## Homepage
GeoNode provides some predefined templates to change the home page and the general site content.

In the `/opt/geonode/geonode/templates/` directory we can edit the `index.html`.

Try to edit the content of the `jumbotron box` in the page, save and refresh your browser to see the changes.

```shell
vim geonode/templates/index.html
```

```diff
diff --git a/geonode/templates/index.html b/geonode/templates/index.html
index 59de01808..bd13da2b2 100644
--- a/geonode/templates/index.html
+++ b/geonode/templates/index.html
@@ -19,7 +19,7 @@
 {% if custom_theme.welcome_theme == 'JUMBOTRON_BG' or not slides %}
 <div class="jumbotron">
   <div class="container gn-container">
-      {% with jumbotron_welcome_title=custom_theme.jumbotron_welcome_title|default:"Welcome"|template_trans %}
+      {% with jumbotron_welcome_title=custom_theme.jumbotron_welcome_title|default:"GeoNode is awsome!!"|template_trans %}
       <h1>{% trans jumbotron_welcome_title %}</h1>
       {% endwith %}
       <p></p>
```

![image](https://user-images.githubusercontent.com/1278021/132378649-0dbba09c-9593-4184-9387-8cf04d7d4c90.png)

## Main Theme
To change the main theme of GeoNode we can act on the `base.css` file available in the `/opt/geonode/geonode/static/geonode/css/` folder.

**IMPORTANT**: Remember to put the rules at the end of the file, otherwise they could be overridden by some previous `CSS` rules

**WARNING**: In order to correctly persist the rules, once you are happy with the `CSS`, you will need to transform them into `LESS` and update the `/opt/geonode/geonode/static/geonode/less/base.less` file accordingly. There are plenty of online resources around the will help you doing this.

For example, if we want to change the background of the `jumbotron`, in this file we can add the following rule:

```css
.home .jumbotron { background: red }
```
Adding the `.home` class prefix is necessary in order to let the rule have priority over the GeoNode’s ones.

We can see this by inspecting the element in the developer console.

Once we refresh the browser, we should see the change as follows

![image](https://user-images.githubusercontent.com/1278021/132380023-ae8a9a06-5e7f-47eb-85db-f1a61f9c0ab1.png)



#### [Next Section: Programmatically Customize the Look-and-Feel](LANDF_SIMPLE.md)