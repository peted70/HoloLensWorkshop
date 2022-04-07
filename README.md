# HoloLens Workshop 😀

(🕙Required time: 60 mins)

## Pre-requisites

There are a few steps that you'll need to complete before the workshop starts: 

- [Create a free **GitHub** account](https://docs.github.com/en/get-started/signing-up-for-github/signing-up-for-a-new-github-account), if you don't have one already. GitHub is a code hosting platform that lets you and others work together on projects from anywhere.

- [Download **Visual Studio Code**](https://code.visualstudio.com/download). Visual Studio Code is a lightweight but powerful source code editor which runs on your desktop and is available for Windows, macOS and Linux.

- Make sure that you are connected to the internet during the workshop.

> Note: If you can't install Visual Studio Code, the workshop can still be completed using a standard text editor.

## Introduction

In this workshop we will create a simple, immersive and interactive 3D experience which we can view with a browser, mobile phone, virtual reality headset or even a  [HoloLens 2](https://www.microsoft.com/en-gb/hololens/) mixed reality headset! 

![Person wearing a HoloLens 2 headset](https://img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/RWGGUE)

We will be using standard web technologies such as **HTML**, **JavaScript** and **CSS**. We will see how to use a new standard called **[WebXR](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/javascript/webxr-overview)** which allows 3D experiences to be created on the web and then used on different devices. The 3D graphics can be viewed within any compatible web browser without the use of plug-ins, thanks to **WebGL** (Web Graphics Library). There are a number of frameworks that we can use to make writing a WebGL app easier, such as **[Babylon.js](https://doc.babylonjs.com/)** and **[A-Frame](https://aframe.io/)**.

**Don't worry** - you do not need to have any previous experience with these technologies to complete the workshop! It is easy to follow - each step is explained below and we will walk through them during the workshop.

![boom box](./.content/boombox.jpg)

To create our 3D experience, we will need to complete three tasks:

1. Get a 3D model
2. Create a web page to display the 3D model
3. Publish content via GitHub

**Let's get started...**

**First**: create a new folder somewhere on your computer to store your workshop files. You can call the folder whatever you like. For example, `C:\HLWorkshop`. We will refer to that folder as the `working folder`.

## Task 1: Get a 3D model

Your 3D experience needs something you can experience in 3D! Our first task is to get a simple (non-animated) 3D model, which needs to be in the .glb file format. 

You can choose **either** to create your own 3D model, **or** download an existing model.

**If you want to try creating your own 3D model**, it's easy using an app like [Paint 3D](https://www.microsoft.com/en-gb/p/paint-3d/9nblggh5fv99?activetab=pivot:overviewtab) (on Windows):
1. Open Paint 3D (it might already be on your Windows start menu, or you can [install it](https://www.microsoft.com/en-gb/p/paint-3d/9nblggh5fv99?activetab=pivot:overviewtab))
2. In Paint 3D, click **New**
3. Click on the **3D library** tab, and find a 3D model that you like from the gallery (see the picture below).
4. _Optional:_ Once you've got a 3D model in Paint 3D, try customizing it by applying some fun **[Stickers](https://support.microsoft.com/en-gb/windows/use-stickers-in-paint-3d-53dd7adf-c332-c7b8-9693-b214c10d0a6f)** using the Stickers tab!
5. When you're happy with your masterpiece, make sure to save it into your `working folder` as a .glb file: click **Menu | Save as | 3D model | Save as type: .glb**

![paint3d](./.content/paint3d.png)

**Alternatively, you can download a 3D model** from [this Github repo](https://github.com/peted70/HoloLensWorkshop/tree/main/3d-models). To download, first click on one of the models:

![model link](./.content/model-link.png)

and then click on the **Download** button on the right of the page:

![download model](./.content/download-model.png)

> Tip: There are also lots of other sites on the web that offer 3D models for free - for example: https://sketchfab.com/

Make sure that you save your 3D model (.glb file) into your `working folder`. (If you're not sure where it downloaded to, check your **Downloads** folder)

## Task 2: Create a web page to display the 3D model

Open Visual Studio Code in a new folder on your computer

![vscode open file](./.content/vscode-newfile.png)

name it `index.html`

From within the file content type `doc` and hit the `Tab` key on your keyoboard and the contents of an html page should be created.

![emmett](./.content/emmett.png)

Resulting in:

![html](./.content/html.pnh.png)

> If this doesn't work in your environment then copy the code below into the index.html file and save it.

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

Change the text `Document` to a name of your choosing.

Add a script tag for the `A-Frame` library into the head section of your html page:

```html
<script src="https://aframe.io/releases/1.3.0/aframe.min.js"></script>
```

and copy the following html and place in the `body` section of you index.html page:

```html
<a-scene background="#00000000">
    <a-assets>
        <a-asset-item id="model" src="my-model-name.glb" response-type="arraybuffer"></a-asset-item>
    </a-assets>
    
    <a-entity gltf-model="#model" scale = "15 15 15" position="0 0 -10"></a-entity>  
        <a-camera>
            <a-cursor material="color: #FFF; shader: flat;"></a-cursor>
        </a-camera>
</a-scene>
```

Being careful to change `my-model-name.glb` for the filename of your 3D model.

Your `index.html` file should now look like this:

```html
<html lang="en">
<head>
    <script src="https://aframe.io/releases/1.3.0/aframe.min.js"></script>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My 3D Model Viewer</title>
</head>
<body>
    <a-scene background="#00000000">
        <a-assets>
            <a-asset-item id="model" src="sun.glb" response-type="arraybuffer"></a-asset-item>
        </a-assets>
        
        <a-entity gltf-model="#sun" scale = "15 15 15" position="0 0 -10"></a-entity>  
            <a-camera>
                <a-cursor material="color: #FFF; shader: flat;"></a-cursor>
            </a-camera>
    </a-scene>
</body>
</html>
```

## Task 3: Publish content via Github

First we need to create a new repository on Github and copy the index.html and model.glb file to it.

To create a repository:

![github repo](./.content/new-repo.png)

then,

![create repo](./.content/create-repo.png)

then,

![upload repo](./.content/upload-repo.png)

then drag and drop your files...

![drag files](./.content/drag-files.png)

Commit the changes...

![commit changes](./.content/commit-changes.png)

Your repo should now look like this:

![repo](./.content/repo.png)


Now we will use Guthub Pages to host the html page.

Go to the settings page:

![settings](./.content/settings.png)

Then the Pages page:

![pages](./.content/pages.png)

Now set your main branch as the source for your page and Save:

![main](./.content/main.png)

You will then see a page link like the following:

![page link](./.content/page-link.png)

Clicking on the link will open the index.html page in your browser:

![github page](./.content/github-page.png)

But notice that in my case the model is being rendered very small but we can fix this by editing the html and changing the scale value for the model:

![edit html](./.content/edit-html.png)

Change the values.

![change scale](./.content/scale-model.png)

And then commit the changes...

![commit](./.content/commit.png)

Wait for a while ☕☕☕☕☕

Then reload the page...

![final page](./.content/final-page.png)

Notice the `VR` button at the bottom right of the page. If you navigate to this page from within a VR headset then activate the VR button you will enter a fully 3d, immersive experience viewing your 3D model.

We can do the same in a HoloLens2 where your model will be combined with the real-world.

You can try the one I made [here](https://peted70.github.io/HoloLensWorkshop/)

> You can use your mouse and arrow keys to navigate around the 3D model if you open this on a desktop or your finger if you are using a mobile phone.

And here it is running on a HoloLens2:

![HL2](./.content/HL2workshop.gif)

## Further Learning Resources

[WebXR Development with Javascript](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/javascript/webxr-overview)

[VR Hello World using Babylon.js](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-helloworld/introduction-01)

[Build a piano in WebXR with Babylon.js](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/introduction-01)
