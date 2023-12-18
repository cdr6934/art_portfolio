---
weight: 1
images:
-  https://live.staticflickr.com/65535/53334387487_1ed63b42ca_b_d.jpg
title: Generative Corals
date: 2023-09-10
tags:
- archive # all posts
- work
- generative 
---

This has been an interest of mine for a while. I've started on this but there is yet much to be done and a continuation of a process that I'd like to refine in the next year or so. 

I used [OpenSCAD](https://openscad.org/) and found that it was quite easy to make some of these images. 


```
module arm(r, marg) {
union() {
    for(i = [0:1:20])
    {
        translate([rands(-5,5,1)[0],rands(-5,5,1)[0],i*r*marg]) {
            sphere(r);
        }
    } 
    }
}

module branch() {
union() {
    arm(5,0.8); 
    arm(2,0.8); 
    arm(3,0.8); 
}
}

branch(); 
for(i=[0:1:10])
    {
    ang = rands(-45,45,1)[0]; 
    dis = rands(-30,30,1)[0];
    translate([0,0,dis]) {
        rotate([ang,ang,ang]) {
        branch(); 
        }
    }
}
```