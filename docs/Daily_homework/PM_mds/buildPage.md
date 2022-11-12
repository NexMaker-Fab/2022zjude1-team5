# STEP 1: Github+Docsify

Refere to [this tutorial](https://www.nexmaker.com/doc/1projectmanage/github&docsify.html)

## Tips

1. We use **3.2 Docsifymethod** to build the structure
2. DO NOT close the cmd window while running localhost:3000
3. DO NOT forget the "\_" sign before \_sidebar.md & \_navbar.md

# STEP 2: Set Image Uploader Service

You can refere to [this tutorial](https://www.nexmaker.com/doc/1projectmanage/imageuploadservice.html) if you're using a MAC. Since this group's builder was using a Win PC and failed to use Gitlab as image uploader, here we use Github as Picbed, click [here](https://blog.csdn.net/qq_43367829/article/details/104882071) for tutorial

## Tips

1. **Remember to copy the token at once**, or you'll never get the chance to see it again. If you do lose the chance, delete the token and generate a new one
2. Different from the PicGo+Github tutorial, we use **PicGo 2.3.0** version, as it was the latest formal version when we build the page

# STEP 3 (IMPORTANT): Change the Source

You may wonder why the pages you built with docsify did not show up as expected when you visit your site link, like this:

![](<https://raw.githubusercontent.com/Juniper1106/docsify/main/img/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE(213).png>)

Without changing some certain settings, you'll only see a blank page showing things in your README.md instead of what you really want to see.
Here's what to do:

1. Back to the page where you get your site link (in Github, settings->Pages), move to Build and deployment-Source (as below)

   ![](https://raw.githubusercontent.com/Juniper1106/docsify/main/img/githubactions.png)

2. Change from "Github Actions" to "Deploy from a branch", and a new sub-topic: Branch will appear

   ![](https://raw.githubusercontent.com/Juniper1106/docsify/main/img/changeSrc.png)

   ![](https://raw.githubusercontent.com/Juniper1106/docsify/main/img/branch.png)

3. Now change from "/(root)" to **"/docs"**, and **save** the change
4. Wait several minutes and visit your link, if it remains the README.md page, just wait for another several minutes or check your web connection.

# STEP 4: Add Some Contents

Do as you like ^^

## Make Sidebar Collapsible

We need a plugin to realize this function, [here](https://www.npmjs.com/package/docsify-sidebar-collapse) is what we use. Make sure npm is installed and functions normally on your computer.

### Steps

1. use VSCode to open your file locally.
2. Open the terminal within VSCode, on Windows, you can use the shortcut "Ctrl + `(the key under esc)", or you can find the entry on the topbar.

<div align=center>
   <img src="https://raw.githubusercontent.com/Juniper1106/docsify/main/img/where%20is%20terminal.jpg"></img>
</div>

3. Paste `npm i docsify-sidebar-collapse` in the terminal, press Enter to run the command.

![](https://raw.githubusercontent.com/Juniper1106/docsify/main/img/run-collapsible-npm.png)

4. After succesfully installing the plugin, we should include it in the html file (index.html).
5. in Body section, we added some scripts before, below is our original code (if you haven't made any modification):

```html
<script>
  window.$docsify = {
    name: "Your Name",
    repo: "",
    loadSidebar: true, //prepare for sidebar
    loadNavbar: true, //prepare for navbar
  };
</script>

<!-- Docsify v4 -->
<script src="//cdn.jsdelivr.net/npm/docsify@4"></script>
```

We made changes here, and below is the final code.  
p.s.: We deleted the `subMaxLevel: 3` attributes in the original tutorial^ ^

```html
<script>
  window.$docsify = {
    name: "Your Name",
    repo: "",
    loadSidebar: true, //prepare for sidebar
    loadNavbar: true, //prepare for navbar
    alias: {
      "/.*/_sidebar.md": "/_sidebar.md",
    },
    sidebarDisplayLevel: 1,
  };
</script>

<!-- Docsify v4 -->
<script src="//cdn.jsdelivr.net/npm/docsify@4"></script>

<!-- plugins -->
<script src="//cdn.jsdelivr.net/npm/docsify-sidebar-collapse/dist/docsify-sidebar-collapse.min.js"></script>
```

6. Now we can click to collape sub items in sidebar! To make its collapsible feature more straightfoward, we can add some style. The original tutorial offered 2 types of style (arrow and folder), we can include the stylesheet you like in the head section of the html file.
<div align=center>
   <img src="https://raw.githubusercontent.com/Juniper1106/docsify/main/img/without%20arrow.gif"></img>
   <img src="https://raw.githubusercontent.com/Juniper1106/docsify/main/img/with%20arrow.gif"></img>
</div>

# STEP 5: Beautify

Add a style.css file and include it in the index.html file (if you know basic knwledge about css & html)

## Tips

1. In case you want to align your picture center:
   change from Markdown language `![](https://yourpic.link)`
   to html (as below)

```html
<div align=center>
   <img src="https://yourpic.link"></img>
</div>
```

2. Open the Project in VSCode
   On windows, you can directly drag and drop the local file to VSCode icon to quickly open the file.

![](<https://raw.githubusercontent.com/Juniper1106/docsify/main/img/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE(214).png>)
