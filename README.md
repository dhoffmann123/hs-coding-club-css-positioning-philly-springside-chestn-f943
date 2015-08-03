# iPhone Organizer 

<img src="https://s3.amazonaws.com/after-school-assets/iphone-correct.png" alt="correct iphone" align="right" height="300" hspace="10">

Everyone always has specific places where they like their apps to go on their phone. It's muscle memory to get to them, and we take that layout for granted. But how confused would you be if someone rearranged your apps?

Fortunately for us, we can use CSS positioning to put our apps back in their original spots, just like in the image below!

If you look at the site in the browser, you'll notice the icons are all clumped together to the left of the iPhone. They're not even on the screen! Our job is to move the icons to their appropriate spots, just like in this image to the right.

## Let's Get Started

### Absolute Positioning

#### Step 1:

Open this lesson in Nitrous, by clicking the `Open In Nitrous` button in learn.

<img src="https://s3.amazonaws.com/after-school-assets/open-in-nitrous.png">

#### Step 2:

Open `index.html` in the browser by running in terminal `python -m SimpleHTTPServer 3000`. 

Once you have the server running, select `preview` and then `port 3000`.

<img src="https://s3.amazonaws.com/after-school-assets/nitrous-preview.png" alt="nitrous preview">

Make sure your broswer is the full width of your computer screen, and not minimized at all.

You're going to code your solution in `css/absolute.css` and `css/relative.css`. Go ahead and open that file in Nitrous, as well as `index.html`. You'll want to familiarize yourself with the code there. 

#### Step 3:

Take a look at the code in `index.html`. You should notice several things:

+ The app icons are grouped into threes

+ Each icon group is in their own `div`

+ The three divs are also in a single `div` with the id `iphone`

If you look at the site in the browser, you'll notice the icons are all clumped together to the left of the iPhone. They're not even on the screen! Our job is to move the icons to their appropriate spots.

### Step 4:

Let's start with the first group of images. First, we need to move the group, and then we can space each image individually.

In our `css/absolute.css`, copy and paste the code below.

```css
#first-three{
  position: absolute;
  top: 300px;
  left: 620px;

}
```

We use `#first-three` as our CSS selector, which is a `div` that contains three images - the app icons we're moving (SnapChat, Weather, and Angry Birds). 

The first property we set is `position`. This property can have several different values, but the most important two are `absolute` and `relative`. 

`absolute` means that an element's position is defined specifically. It's like telling someone, go stand in the top left corner of the room, 10 feet from the left wall, and ten feet from the top wall. No matter the size of the room, you always have to stay 10 feet from the top and the left. 

`relative` means that the placement of an element is relative to other elements. It's like saying stand 10% of the length of the room away from the top, and 15% of the width of the room away from the left of the wall. If the room shrinks, so do those percentages and thus your placement.

We set `position: absolute;` for now, which means the position of this `div` containing the three icons is never going to move. We the set `top: 300px`, meaning the images are going to be 300 pixels away from the top of the page. We also set `left: 620px;` meaning the images are going to be 620 pixels from the left side of the page.

#### Step 4: 

We want to go ahead and use the same CSS for the other two divs of images. Copy and paste the following code in `css/absolute.css`:

```css
#second-three{
  position: absolute;
  top: 400px;
  left: 620px;
}

#third-three{
  position: absolute;
  top: 500px;
  left: 620px;
}
```

You'll notice the distance from the left side of the page stays the same, but the distance from the top increases by 100 pixels for each one. If we want the second set of icons to be below the first set, they need to be farther from the top.

#### Step 5: 

Now we need to space the icons away from them appropriately. You'll remember from the box model, that `margin` governs the space between elements. We can set `margin-left` and `margin-right`:

```css

#snapchat {
  margin-right: 20px;
}

#weather {
 margin-right: 20px;
 margin-left: 20px;

}

#angry-bird {
  margin-left: 20px;
}

```

We already have Snapchat where we want it on the left, we just need space on the right, so we set `margin-right: 20px`. The Weather app needs space on both the left and the right, so we set both `margin-left` and `margin-right`.Angry Bird only needs margin on the left, `margin-left: 20px`.

Save and refresh in the browser!

#### Step 6:

Let's fix the last 6 icons. Copy and paste the following into your `css/style.css`:

```css
#facebook {
  margin-right: 20px;
}

#mail {
 margin-right: 20px;
 margin-left: 20px;

}

#spotify {
  margin-left: 20px;
}
#twitter{
  margin-right: 20px;
}

#vsco {
 margin-right: 20px;
 margin-left: 20px;

}

#youtube {
  margin-left: 20px;
}
```

#### Step 7:

Save, refresh in the browser and see your perfectly laid out icons! But now try and shrink the browser. What happens? Your site might look something like this: 

<img src="https://s3.amazonaws.com/after-school-assets/absolute-bad.png" alt="dangers of absolute positioning" align="right" height="300" hspace="10">
>

### Relative Positioning

This is where relative positioning becomes really powerful, without setting absolute locations for our HTML elements, our page can become responsive, which means it will look good no matter the size of our webpage.

#### Step 1:

The first thing that we need to do is define each `div` of icons to only take up 1/3 of the height of it's parent, which is the `div` with the id `images`, which will create our rows of icons. Copy and paste the following code into `css/relative.css`:

```css
.one-third {
  position: relative;
  height: 33.3333333%;
  width: 100%;
}
```

We use the class `one-third` and assign the `position` property to `relative`. This means that the width and height of these rows will be relative to the height of the parent div (the div with the id iphone). We set `height: 33.3333333%;`, which means each row will take up 33.3333333% of it's parent.

#### Step 2:

Now that we have our three rows, we need to absolutely position our icons inside those relative rows. This way, as the iPhone scales in size, the icons slide with them. Let's take the first row (Snapchat, Weather, and Angry Bird)

Copy and paste into `css/relative.css`:

```css
#snapchat {
  position: absolute;
  margin-top: 30%;
  margin-left: 30%;
  height: 32px;
}

#weather {
  position: absolute;
  margin-top: 30%;
  margin-left: 45%;
  height: 32px;
}

#angry-bird {
  position: absolute;
  margin-top: 30%;
  margin-left: 60%;
  height: 32px;
}
```

On all three images, we're using the id as our CSS selector. From there, we're setting `postion: absolute;` And then we're setting the `margin-top` and `margin-left`, as well as the image `height`.

Save and refresh in the browser. Go ahead and try to shrink your browser window.

#### Step 3:

Now let's do the other two rows! Copy and paste the following into `css/relative.css`:

```css 
#facebook {
  position: absolute;
  margin-top: 30%;
  margin-left: 30%;
  height: 32px;
}

#mail {
  position: absolute;
  margin-top: 30%;
  margin-left: 45%;
  height: 32px;

}

#spotify {
  position: absolute;
  margin-top: 30%;
  margin-left: 60%;
  height: 32px;
}
#twitter{
  position: absolute;
  margin-top: 30%;
  margin-left: 30%;
  height: 32px;
}

#vsco {
  position: absolute;
  margin-top: 30%;
  margin-left: 45%;
  height: 32px;

}

#youtube {
  position: absolute;
  margin-top: 30%;
  margin-left: 60%;
  height: 32px;
}
```

And DONE!

