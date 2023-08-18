---
layout: default
title: code
---

<style>

  .imagee{
    object-fit: cover;
  }
/*
 * * Skeleton V2.0.4
 * * Copyright 2014, Dave Gamache
 * * www.getskeleton.com
 * * Free to use under the MIT license.
 * * http://www.opensource.org/licenses/mit-license.php
 * * 12/29/2014
 * */

/* Table of contents
 * ––––––––––––––––––––––––––––––––––––––––––––––––––
 * - Grid
 * - Base Styles
 * - Typography
 * - Links
 * - Buttons
 * - Forms
 * - Lists
 * - Code
 * - Tables
 * - Spacing
 * - Utilities
 * - Clearing
 * - Media Queries
 * */

/* Grid
 * –––––––––––––––––––––––––––––––––––––––––––––––––– */

 .container {
    position: relative;
    width: 100%;
    max-width: 1024px;
    margin: 0 auto;
    padding: 0 20px;
    box-sizing: border-box;
}
.column,
.columns {
    width: 100%;
    float: left;
    box-sizing: border-box;
}
/* For devices larger than 400px */

@media (min-width: 400px) {
    .container {
        width: 85%;
        padding: 0;
    }
}
/* For devices larger than 550px */

@media (min-width: 750px) {
    .container {
        width: 80%;
    }
    .column,
    .columns {
        margin-left: 4%;
    }
    .column:first-child,
    .columns:first-child {
        margin-left: 0;
    }
    .one.column,
    .one.columns {
        width: 4.66666666667%;
    }
    .two.columns {
        width: 13.3333333333%;
    }
    .three.columns {
        width: 22%;
    }
    .four.columns {
        width: 30.6666666667%;
    }
    .five.columns {
        width: 39.3333333333%;
    }
    .six.columns {
        width: 48%;
    }
    .seven.columns {
        width: 56.6666666667%;
    }
    .eight.columns {
        width: 65.3333333333%;
    }
    .nine.columns {
        width: 74.0%;
    }
    .ten.columns {
        width: 82.6666666667%;
    }
    .eleven.columns {
        width: 91.3333333333%;
    }
    .twelve.columns {
        width: 100%;
        margin-left: 0;
    }
    .one-third.column {
        width: 30.6666666667%;
    }
    .two-thirds.column {
        width: 65.3333333333%;
    }
    .one-half.column {
        width: 48%;
    }
    /* Offsets */
    .offset-by-one.column,
    .offset-by-one.columns {
        margin-left: 8.66666666667%;
    }
    .offset-by-two.column,
    .offset-by-two.columns {
        margin-left: 17.3333333333%;
    }
    .offset-by-three.column,
    .offset-by-three.columns {
        margin-left: 26%;
    }
    .offset-by-four.column,
    .offset-by-four.columns {
        margin-left: 34.6666666667%;
    }
    .offset-by-five.column,
    .offset-by-five.columns {
        margin-left: 43.3333333333%;
    }
    .offset-by-six.column,
    .offset-by-six.columns {
        margin-left: 52%;
    }
    .offset-by-seven.column,
    .offset-by-seven.columns {
        margin-left: 60.6666666667%;
    }
    .offset-by-eight.column,
    .offset-by-eight.columns {
        margin-left: 69.3333333333%;
    }
    .offset-by-nine.column,
    .offset-by-nine.columns {
        margin-left: 78.0%;
    }
    .offset-by-ten.column,
    .offset-by-ten.columns {
        margin-left: 86.6666666667%;
    }
    .offset-by-eleven.column,
    .offset-by-eleven.columns {
        margin-left: 95.3333333333%;
    }
    .offset-by-one-third.column,
    .offset-by-one-third.columns {
        margin-left: 34.6666666667%;
    }
    .offset-by-two-thirds.column,
    .offset-by-two-thirds.columns {
        margin-left: 69.3333333333%;
    }
    .offset-by-one-half.column,
    .offset-by-one-half.columns {
        margin-left: 52%;
    }
}
/* Base Styles
                                                                                                                                           * –––––––––––––––––––––––––––––––––––––––––––––––––– */

/* NOTE
 * html is set to 62.5% so that all the REM measurements throughout Skeleton
 * are based on 10px sizing. So basically 1.5rem = 15px :) */

html {
    font-size: 62.5%;
}
body {
    font-size: 1.5em;
    /* currently ems cause chrome bug misinterpreting rems on body element */
    line-height: 1.6;
    font-weight: 400;
    
    color: #222;
}
/* Typography
             * –––––––––––––––––––––––––––––––––––––––––––––––––– */

h1,
h2,
h3,
h4,
h5,
h6 {
    margin-top: 0;
    margin-bottom: 2rem;
    font-weight: 300;
}
h1 {
    font-size: 4.0rem;
    line-height: 1.2;
    letter-spacing: -.1rem;
}
h2 {
    font-size: 3.6rem;
    line-height: 1.25;
    letter-spacing: -.1rem;
}
h3 {
    font-size: 3.0rem;
    line-height: 1.3;
    letter-spacing: -.1rem;
}
h4 {
    font-size: 2.4rem;
    line-height: 1.35;
    letter-spacing: -.08rem;
}
h5 {
    font-size: 1.8rem;
    line-height: 1.5;
    letter-spacing: -.05rem;
}
h6 {
    font-size: 1.5rem;
    line-height: 1.6;
    letter-spacing: 0;
}
/* Larger than phablet */

@media (min-width: 550px) {
    h1 {
        font-size: 5.0rem;
    }
    h2 {
        font-size: 4.2rem;
    }
    h3 {
        font-size: 3.6rem;
    }
    h4 {
        font-size: 3.0rem;
    }
    h5 {
        font-size: 2.4rem;
    }
    h6 {
        font-size: 1.5rem;
    }
}
p {
    margin-top: 0;
}
/* Lists
                                                            * –––––––––––––––––––––––––––––––––––––––––––––––––– */

ul {
    list-style: circle inside;
}
ol {
    list-style: decimal inside;
}
ol,
ul {
    padding-left: 0;
    margin-top: 0;
}
ul ul,
ul ol,
ol ol,
ol ul {
    margin: 1.5rem 0 1.5rem 3rem;
    font-size: 90%;
}
/* Code
               * –––––––––––––––––––––––––––––––––––––––––––––––––– */

code {
    padding: .2rem .5rem;
    margin: 0 .2rem;
    font-size: 90%;
    white-space: nowrap;
    background: #F1F1F1;
    border: 1px solid #E1E1E1;
    border-radius: 4px;
}
pre > code {
    display: block;
    padding: 1rem 1.5rem;
    white-space: pre;
}
/* Tables
                     * –––––––––––––––––––––––––––––––––––––––––––––––––– */

th,
td {
    padding: 12px 15px;
    text-align: left;
    border-bottom: 1px solid #E1E1E1;
}
th:first-child,
td:first-child {
    padding-left: 0;
}
th:last-child,
td:last-child {
    padding-right: 0;
}
/* Spacing
           * –––––––––––––––––––––––––––––––––––––––––––––––––– */

button,
.button {
    margin-bottom: 1rem;
}
input,
textarea,
select,
fieldset {
    margin-bottom: 1.5rem;
}
pre,
blockquote,
dl,
figure,
table,
p,
ul,
ol,
form {
    margin-bottom: 2.5rem;
}
/* Utilities
       * –––––––––––––––––––––––––––––––––––––––––––––––––– */

.u-full-width {
    width: 100%;
    box-sizing: border-box;
}
.u-max-full-width {
    max-width: 100%;
    box-sizing: border-box;
}
.u-pull-right {
    float: right;
}
.u-pull-left {
    float: left;
}
/* Clearing
         * –––––––––––––––––––––––––––––––––––––––––––––––––– */

/* Self Clearing Goodness */

.container:after,
.row:after,
.u-cf {
    content: "";
    display: table;
    clear: both;
}
/* Media Queries
       * –––––––––––––––––––––––––––––––––––––––––––––––––– */

/*
 * Note: The best way to structure the use of media queries is to create the queries
 * near the relevant code. For example, if you wanted to change the styles for buttons
 * on small devices, paste the mobile query code up in the buttons section and style it
 * there.
 * */

/* Larger than mobile */

@media (min-width: 400px) {}
/* Larger than phablet (also point when grid becomes active) */

@media (min-width: 550px) {}
/* Larger than tablet */

@media (min-width: 750px) {}
/* Larger than desktop */

@media (min-width: 1000px) {}
/* Larger than Desktop HD */

@media (min-width: 1200px) {}

</style>
<body>
<div>
    
    
<center>
  <p>
    <!-- 
          To those 
          who doubted me, 
          hated me all my life,
          for no good reason
          but be pessimistic

          I don't care    
          'cause in the end,
          at least you'll get 
          to witness, 
          beaches

          IT'S NEVER TOO LATE FAM! WE'RE ALL GONNA MAKE IT.
          - john
      -->
  </p>
  <h2>code</h2>
  <p>
    some of the projects i worked on that improved my programming skills. click the photos or the title to learn more.
    </p>
	<!-- Song: Ships With Holes Will Sink | Artist: We were promised Jetpacks -->
  <p>music to listen to while browsing: <a href="https://open.spotify.com/playlist/4MJqdF6COgF5BJy35j7Ca1?si=15babfa57a6741fe">spotify link</a></p>

</center>


<!---  ROW 1 --->
<section>
<div class="row">
  <div class="four columns">
  <div class="imagg">
      <a href="https://github.com/johnamata/moviedb">
        <img src="https://raw.githubusercontent.com/johnamata/moviedb/main/pic1.png" class="image-col" alt="math">
        <span class="proj-title">moviedb</span></a> - Python, Django
		<p>simple movie database, a python django webapp for my practice</p>
  </div>
  </div>
  
  <div class="four columns">
  <div class="imagg">
      <a href="https://github.com/johnamata/firebase-messenger">
        <img src="https://raw.githubusercontent.com/johnamata/firebase-messenger/master/pic.png" class="image-col" alt="math">
        <span class="proj-title">firebase-messenger</span></a> - HTML, Node, React, JS
		<p>realtime chat app deployed at <a href="https://firebase-messenger.netlify.app">firebase-messenger.netlify.app</a>, supports group messaging + photos</p>
  </div>
  </div>
  
  <div class="four columns">
  <div class="imagg">
      <a href="https://github.com/johnamata/pen-island">
        <img src="https://camo.githubusercontent.com/d72f4173adf4ec0a8b11789d8f3ca9146dc6299a38ddde2d08a33495095d2ae1/68747470733a2f2f692e696d6775722e636f6d2f634538304c6f582e706e67" class="image-col" alt="math" height="200">
        <span class="proj-title">pen-island</span></a> - Java
		<p>2d desktop game akin to flappy bird that I developed as one of my projects in a java class at my college</p>
  </div>
  </div>
</div>

<!--- Row ---->
<section>
<div class="row">
  <div class="four columns">
  <div class="imagg">
      <a href="computer-science">
        <img src="../projects/pics/cs2.png" class="image-col" alt="sicp-htdp">
        <span class="proj-title">compsci</span></a> - Racket, Scheme
<p>my solutions for legendary computer science textbooks like (HtDP) <a href="https://htdp.org/2020-8-1/Book/index.html">How to Design Programs</a> - slowly reviewing them to have better fundamentals</p>
  </div>
  </div>
  
  <div class="four columns">
  <div class="imagg">
      <a href="freecodecamp">
        <img src="../projects/pics/fcc.png" class="image-col" alt="fcc">
        <span class="proj-title">freecodecamp</span></a> - HTML/CSS, JavaScript (JS)
		<p>originally containing my solutions for freecodecamp's full stack web developer curriculum, it now has my other JS & HTML learning projects</p>
  </div>
  </div>
  
  <div class="four columns">
  <div class="imagg">
      <a href="thinking">
        <img src="../projects/pics/think.png" class="image-col" alt="fcc">
        <span class="proj-title">thinking</span></a> - C++, Java
		<p>developing my computational and algorithmic thinking by solving algorithm problems. The linked repo has my solutions and notes</p>
  </div>
  </div>
</div>
</section>




<center><p>questions? feel free to send digital love letters at &lt;<code>j+pa@johnamata.com</code>&gt;</p></center>
