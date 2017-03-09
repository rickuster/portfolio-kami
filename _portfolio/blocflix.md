---
layout: post
title: Bloc Jams
thumbnail-path: "img/blocjams.png"
short-description: Bloc Jams is a website for streaming music any time, any where and on any platform. 

---

{:.center}
![]({{ site.baseurl }}/img/blocjams2.png)

## Explanation

Bloc Jams is a music player website I developed with guidance from Bloc. The goal was to come up with a responsive website that allow users to play streaming music on any platform. 

## Problem

We wanted to design a website that is able to adapt to the user's device whether they are on PC, mobile or tablet. The interface also have to be easy to use and responsive to user inputs. 

## Solution

To have the website adapt to the user's operating environment we put checks in the code to detect the user's resolution and scale the page accordingly.

{% highlight javascript %}
/* Medium and small screens (640px) */
 @media (min-width: 640px) 
 {
   /* Style information will go here */
     html{
         font-size:112%; 
     }
     
     .column {
         float: left;
         padding-left: 1rem;
         padding-right: 1rem;
     }
     
     .column.full { width: 100%; }
     .column.two-thirds { width: 66.7%; }
     .column.half { width: 50%; }
     .column.third { width: 33.3%; }
     .column.fourth { width: 25%; }
     .column.flow-opposite { float: right; }  
     
 }
 
 /* Large screens (1024px) */
 @media (min-width: 1024px) {
   /* Style information will go here */
     html {
         font-size: 120%;
     }
 }
{% endhighlight %}

We also implement responsive element such as scroll detection, onhover, offhover and click listener. 

{% highlight javascript %}
//scroll detection
 $(window).load(function() {
    if ($(window).Height > 950) {
         animatePoints(pointsArray);
    }
    var scrollDistance = $('.selling-points').offset().top - $(window).height() + 200;
    $(window).scroll(function(event) {
        if ($(window).scrollTop() >= scrollDistance) {
            animatePoints();
        }         
     });
 });
{% endhighlight %}

The user can play the music by hovering over the song number. 

{% highlight javascript %}
   var onHover = function(event) {
        var songNumberCell = $(this).find('.song-item-number');
        var songNumber = parseInt(songNumberCell.attr('data-song-number'));

        if (songNumber !== currentlyPlayingSongNumber) {
            songNumberCell.html(playButtonTemplate);
        }
    };

    var offHover = function(event) {
        var songNumberCell = $(this).find('.song-item-number');
        var songNumber = parseInt(songNumberCell.attr('data-song-number'));

        if (songNumber !== currentlyPlayingSongNumber) {
            songNumberCell.html(songNumber);
        }
    };
{% endhighlight %}

There are also secondary controls to select play/pause, next/previous, seek and volume. 

{% highlight javascript %}
<section class="player-bar">
            <div class="container">
                <div class="control-group main-controls">
                                         <a class="previous">
                         <span class="ion-skip-backward"></span>
                     </a>
                     <a class="play-pause">
                         <span class="ion-play"></span>
                     </a>
                     <a class="next">
                         <span class="ion-skip-forward"></span>
                     </a>
                </div>
                <div class="control-group currently-playing">
                    <h2 class="song-name"></h2>
                    <div class="seek-control">
                         <div class="seek-bar">
                             <div class="fill"></div>
                             <div class="thumb"></div>
                         </div>
                         <div class="current-time">2:30</div>
                         <div class="total-time">4:45</div>
                     </div>
                     <h2 class="artist-song-mobile"></h2>
                     <h3 class="artist-name"></h3>
                </div>
                <div class="control-group volume">
                    <span class="ion-volume-high icon"></span>
                     <div class="seek-bar">
                         <div class="fill"></div>
                         <div class="thumb"></div>
                     </div>
                </div>
            </div>
        </section>
{% endhighlight %}

## Results

Webpage scaling to user's resolution:
{:.center}
![]({{ site.baseurl }}/img/blocjams3.png)

Responsive, dynamic elements:
{:.center}
![]({{ site.baseurl }}/img/blocjams4.png)

Simple, easy to use control:
{:.center}
![]({{ site.baseurl }}/img/blocjams5.png)

## Conclusion

Bloc Jams was a fun project and shows the potential of what a simple but responsive website can do. 