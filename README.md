<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a name="readme-top"></a>
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]


<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/Sentientplatypus/handarea">
    <img src="logo.png" alt="Logo">
  </a>

![Alt text](res/GENE.png)

<h3 align="center">Calculating the Area of a hand</h3>

  <p align="center">
    Using OpenCV, we can calculate the Area of a hand. This is for Mr Deppe's AP Calculus BC class @ Ithaca High School
    <br /> 
    <a href="https://github.com/Sentientplatypus/handarea"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/Sentientplatypus/handarea">View Demo</a>
    ·
    <a href="https://github.com/Sentientplatypus/handarea/issues">Report Bug</a>
    ·
    <a href="https://github.com/Sentientplatypus/handarea/issues">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>




### Built With

* [![Next][python]][python-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Methodology

1. Accurately trace the shape of your hand on a piece of blank paper.
2. Use a computer vision (CV) algorithm to estimate the area of your hand. The methodology of the CV algorithm is outlined below.
    * Detect the edges of the paper and contours of our hand traced on the paper.
    * Compute the number of pixels within the detected edges and contours.
    * Compute the pixel-to-area ratio (i.e., the true area in the real world captured in a single pixel) given the true dimensions of the paper. In engineering, you typically account for radial and tangential distortion in the lens using the intrinsic camera matrix (optical center, focal length, focal width, skew) and distortion coefficients. To save ourselves the time of calibrating the camera, we instead have to take serious precautions such as angling the camera perfectly above and in the middle of the paper.
    `Jun’s Paper (US Letter): 21.59 cm x 27.94 cm = 603.225 cm^2`
    `Gene’s Paper (A4): 21.00 cm x 29.70 cm = 623.700 cm^2`
    * Estimate the area of the hand based on the pixel-to-area ratio and the number of pixels within the detected edges and contours. That is, multiply the number of pixels observed within the hand trace by the computed area of each pixel. Since each pixel is essentially a tiny square with a known area, the CV algorithm is equivalent to computing the Riemann sum of the area of many small geometries under or between curves. The only difference (and advantage) is that the CV algorithm is more practical and accurate than manually drawing and fitting many small shapes within our hand trace.
3. Verify if the estimated area of the hand is within 1% of the true area. This can be done by drawing a rectangular bounding box with a known area around your hand and comparing that area to the CV algorithm’s estimation. Since the CV algorithm’s precision is consistent for shapes with similar dimensions, the CV’s algorithm’s error on the bounding box must closely match the error in its hand area estimation.

## Results
|       Gene       |
|:---------------------------:|
| ![Alt text](res/GENE.png) | ![Alt text](res/GENEboundingrect.png)  |
|   Estimated Hand Area: 153.715 cm² |
| True Bounding Box Area: 22.3cm x 18.2cm = 405.86 cm² |
| Estimated Bounding Box Area: 403.308 cm² |
| Estimated Error: 0.629% |


|       Jun       |
|:---------------------------:|
| ![Alt text](res/JUN.png)| ![Alt text](res/JUNboundingrect.png)  |
| Estimated Hand Area: 120.221 cm² |
| True Bounding Box Area: 17 cm x 19 cm = 323 cm² |
| Estimated Bounding Box Area: 325.329 cm² |
| Estimated Error: 0.721% |


|       Tirmizi       |
|:---------------------------:|
| ![Alt text](res/TIRMIZI.png)| ![Alt text](res/TIRMIZIboundingrect.png)  |
| Estimated Hand Area: 164.930 cm² |
| True Bounding Box Area: 20 cm x 19.3 cm = 386 cm² |
| Estimated Bounding Box Area: 388.749 cm² |
| Estimated Error:  0.712% |


### Prerequisites

This is an example of how to list things you need to use the software and how to install them.
* pip
  ```sh
  pip install opencv-python
  ```

### Installation


1. Clone the repo
   ```sh
   git clone https://github.com/Sentientplatypus/handarea.git
   ```


<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage

Use this space to show useful examples of how a project can be used. Additional screenshots, code examples and demos work well in this space. You may also link to more resources.

_For more examples, please refer to the [Documentation](https://example.com)_

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ROADMAP -->
## Roadmap

- [X] Filtering
- [X] Getting error
- [X] Writeup

See the [open issues](https://github.com/Sentientplatypus/handarea/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

Geneustace Wicaksono - [My Website](https://genewica.herokuapp.com) - geneustacewicaksono@yahoo.com

Project Link: [https://github.com/Sentientplatypus/handarea](https://github.com/Sentientplatypus/handarea)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* Junyoung Sim


<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/Sentientplatypus/handarea.svg?style=for-the-badge
[contributors-url]: https://github.com/Sentientplatypus/handarea/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Sentientplatypus/handarea.svg?style=for-the-badge
[forks-url]: https://github.com/Sentientplatypus/handarea/network/members
[stars-shield]: https://img.shields.io/github/stars/Sentientplatypus/handarea.svg?style=for-the-badge
[stars-url]: https://github.com/Sentientplatypus/handarea/stargazers
[issues-shield]: https://img.shields.io/github/issues/Sentientplatypus/handarea.svg?style=for-the-badge
[issues-url]: https://github.com/Sentientplatypus/handarea/issues
[license-shield]: https://img.shields.io/github/license/Sentientplatypus/handarea.svg?style=for-the-badge
[license-url]: https://github.com/Sentientplatypus/handarea/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/linkedin_username
[product-screenshot]: images/screenshot.png
[python]: https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white
[python-url]: https://python.com
