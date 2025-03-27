<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a id="readme-top"></a>

<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->




<!-- PROJECT LOGO -->
<br />
<div align="center">
  </a>

  <h3 align="center">Wilson Project</h3>

  <p align="center">
    The pain and suffering behind taking an AI generated 3D model and making it funtional
    <br />
    <br />
    <br />
    <a href="https://astroanimation.me">Isabel Whelchel</a>
    &middot;
    <a href="https://sites.google.com/view/viza626/home">VIZA 626</a>
  </p>
</div>

[![4-comma][images-fig1]](https://astroanimation.me)

Figure 1. Unfortunately I did not have the patience nor frankly the time to keep finessing and tweaking this horribly made 3D mesh. I probably would have needed to just build on top of the mesh by using the quad draw tool, but at this point it's safe to say that just starting over using a polygon cube would have taken less time.

<!-- Abstract -->
## Abstract
Currently I am seeing what it takes to take an AI generated mesh and make it usable for the animation pipeline. My process began by uploading an image of my plush R2-D2, which I have lovingly nicknamed Wilson after the film Castaway. This image clearly shows Wilson’s body floating in a swimming pool.

[![4-comma][images-fig2]](https://astroanimation.me)

Figure 2. This is the image of Wilson used to generate the mesh. I chose it because it seemed fairly easy to interpret. It has a blank background and a clear subject. 

<!-- Introduction and Related Works -->
## Introduction and Related Works

After uploading the image to Meshy.ai, I was given 4 different meshes, only one of which vaguely resembled the plush. I was then offered the ability to texture the model, so I allowed it to do so. The finished texture was very messy and blurry, pulling elements from Wilson’s body but not actually stitching them together coherently.
I then downloaded the model to see what needed to be fixed in Maya with the initial expectation that only minor modeling needs to be done to correct the visual issues. I was not prepared for the nearly 35,000 faces it had put on such a simple model. My first attempt to reduce the faces with maya’s reduce tool failed as the software instructed me to clean up the geometry from non-manifold faces. After this was completed, I had to first reduce the initial model by 80%, then take the reduced model and reduce that by 80% again, and then once more with this new model reduce the mesh by 80%. 

[![4-comma][images-fig3]](https://astroanimation.me)

Figure 3. Meshy.ai produced these models from the previous image. I'm unsure how it came to the conclusion that the subject in the image needed more appendages or random floating artifacts. I did not want to spend additonal tokens to re-render the result, so I am unsure if anything different would have occured if I had.

[![4-comma][images-fig4]](https://astroanimation.me)

Figure 4. I had Meshy.ai create the texture for the model as well as UV unwrap it. Again, I'm not sure why it chose this strange approach to applying the texture to the model. Normally I would expect it to find the front of the model and place the origninal image there, and fill in the rest with what it thinks should be the rest of the image.

## Methodology

Once this process was finished, I decided to take a glance at the UV map just to see what was waiting on me for the future. To my horror, the AI had unwrapped the mesh in such a way that individual faces were littered throughout the map haphazardly rather than unwrapping the mesh in one clean UV shell. I then began the process of removing the legs from the main body in order to begin modeling them properly. After deleting the connecting faces from the legs to the body, I then separated the mesh from the body expecting to now have 3 meshes; the body, left leg and right leg. Instead I found that the mesh had again separated itself into individual faces rather than one continuous mesh, so I had to collect all the correct faces and combine them again using the merge vertices tool.
I then struggled to get the vertices to merge normally, and upon further inspection I found that there were faces on top of faces, and even smaller faces under that. I then began the process of using the cleanup tool,  retopologize tool, smooth mesh tool and the merge vertices tool to try and fix this issue without having to go in and individually delete faces. Unfortunately this was never successful, and after separating the mesh again, I found that there were even more faces that were not attached to each other, so I took advantage of this and deleted those faces accepting my fate; I would have to manually rebuild the holes in the mesh.

[![4-comma][images-fig5]](https://astroanimation.me)

Figure 5. These 3 models were the results of trying to reduce the polygon count to something reasonable. After 3 attempts it began punching holes into the model, so I deceided to try and reduce the mesh myself with the tools I knew how to use.

[![4-comma][images-fig6]](https://astroanimation.me)

Figure 6. This is the UV map of the model. It is a complete catastrophe. If I were able to finish the main model properly, I would have to use the auto-unwrap tool to overwrite the current UV's and then proceed from there.

## Result and Future Work
Sadly, there comes a time in a project where you must accept that the effort is not worth the time and pain, and this is one of those moments. The amount of effort needed to make this nightmare of a mesh functional is far beyond anything reasonable, and I have a hard time believing that this is supposed to be a “time saving” alternative to just building your own character, or even learning the tools needed to build your own mesh. This isn’t even getting into the UV and texturing side of things, this is just an attempt to make the mesh itself functional.

[![4-comma][images-fig7]](https://astroanimation.me)

Figure 7. For some unknown reason, not all of the faces on the model were attached to the main mesh. This made things like using the fill hole tool and the bridge tool impossible to use. I had to go through at least 3 times and separate and delete these faces from the main mesh. 

## Conclusion
In conclusion,  I suppose if all you were doing was just placing this mesh in a static scene it might be useable, but even then the amount of faces and vertices would make render times outrageous. While fun to experiment with, AI at this time is not capable of creating a time-saving alternative to manually modeling.

[![4-comma][images-fig8]](https://astroanimation.me)

Figure 8. This was the point at which I was begining to give up. Underneath some of the faces on the mesh were additional, very small faces interfering with the topology of the model. These were scattered about randomly throughout the mesh. After deleting these faces I then began the long process of rebuilding all of the holes it had left behind.

<!-- Bibliography -->
<!-- ## References

[1] Craig B Caldwell. 2024. Breaking the Story Formula. In SIGGRAPH Asia 2024 Courses. 1–11.

[2] Bart de Smit. 2005. The Droste-effect and the exponential transform. In Renaissance Banff: Mathematics, Music, Art,
Culture. 169–178.



<!-- CONTACT -->
## Contact

Isabel Whelchel - astroanimation@yahoo.com

Portfolio Website: [astroanimation.me](https://astroanimation.me)




<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

To Wilson, my silent partner in crime. And to anyone who has ever felt discouraged at the idea of AI replacing them, it's going to be a hot minute let me assure you :)

This work is submitted as part of Assignment 2 for the VIZA 626 course at Texas A&M University, under the instruction of Professor You-Jin Kim, during the Spring 2025 semester.

VIZA 626 Class Website: [https://sites.google.com/view/viza626/](https://sites.google.com/view/viza626/home)

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=for-the-badge
[contributors-url]: https://github.com/othneildrew/Best-README-Template/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=for-the-badge
[forks-url]: https://github.com/othneildrew/Best-README-Template/network/members
[stars-shield]: https://img.shields.io/github/stars/othneildrew/Best-README-Template.svg?style=for-the-badge
[stars-url]: https://github.com/othneildrew/Best-README-Template/stargazers
[issues-shield]: https://img.shields.io/github/issues/othneildrew/Best-README-Template.svg?style=for-the-badge
[issues-url]: https://github.com/othneildrew/Best-README-Template/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=for-the-badge
[license-url]: https://github.com/othneildrew/Best-README-Template/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/othneildrew
[product-screenshot]: images/screenshot.png
[images-fig1]: Fig1.png
[images-fig2]: Fig2.JPG
[images-fig3]: Fig3.png
[images-fig4]: Fig4.png
[images-fig5]: Fig5.png
[images-fig6]: Fig6.png
[images-fig7]: Fig7.png
[images-fig8]: Fig8.png
[Next.js]: https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white
[Next-url]: https://nextjs.org/
[React.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[React-url]: https://reactjs.org/
[Vue.js]: https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D
[Vue-url]: https://vuejs.org/
[Angular.io]: https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white
[Angular-url]: https://angular.io/
[Svelte.dev]: https://img.shields.io/badge/Svelte-4A4A55?style=for-the-badge&logo=svelte&logoColor=FF3E00
[Svelte-url]: https://svelte.dev/
[Laravel.com]: https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white
[Laravel-url]: https://laravel.com
[Bootstrap.com]: https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white
[Bootstrap-url]: https://getbootstrap.com
[JQuery.com]: https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white
[JQuery-url]: https://jquery.com 
