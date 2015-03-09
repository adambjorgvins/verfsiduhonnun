# verfsiduhonnun
<html lang="en">
<head>
<meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta name="description" content="Grindakerfi Pure CSS">
        <meta name="author" content="Tækniskólinn - GJG">

        <title>VSH2A verkefni 2</title>

<link rel="stylesheet" href="http://yui.yahooapis.com/pure/0.6.0/pure-min.css">
<!--[if lte IE 8]>
    <link rel="stylesheet" href="http://yui.yahooapis.com/pure/0.5.0/grids-responsive-old-ie-min.css">
<![endif]-->
<!--[if gt IE 8]><!-->
    <link rel="stylesheet" href="http://yui.yahooapis.com/pure/0.5.0/grids-responsive-min.css">
<!--<![endif]-->
</head>
<style type="text/css">
    body {
                max-width: 80em;  /*1280px*/
                margin: 0 auto;
            }
            img, h1, h3, h4, p {
                margin: 0;
                padding: 1em;
            }
            .pure-g div, 
            .pure-g article,
            .pure-g aside {
                -webkit-box-sizing: border-box;
                -moz-box-sizing: border-box;
                box-sizing: border-box;
            
                /*border: 1px solid rgb(255,195,13);*/
            }
            .tabs {
  position: relative;   
  min-height: 200px; /* This part sucks */
  height: 300px;
  clear: both;
  margin: 25px 0;
}
.tab {
  float: left;
}
.tab label {
  background: #eee; 
  padding: 10px; 
  border: 1px solid #ccc; 
  margin-left: -1px; 
  position: relative;
  left: 1px; 
}
.tab [type=radio] {
  display: none;   
}
.content {
  position: absolute;
  top: 28px;
  left: 0;
  background: white;
  right: 0;
  bottom: 0;
  padding: 20px;
  border: 1px solid #ccc; 
}
[type=radio]:checked ~ label {
  background: white;
  border-bottom: 1px solid white;
  z-index: 2;
}
[type=radio]:checked ~ label ~ .content {
  z-index: 1;
}
            /*  
                ATHUGIÐ! pure-u~ klasar eru hannaðir sem ílát fyrir annað efni. 
                EKKI setja útlitsstíla á þá (t.d. border, því þá riðlast uppbyggingin). 
                Þó má gera undantekningu á því, t. d. á meðan hönnun vefsins stendur yfir.            
            */ 
</style>
<style>
.custom-wrapper {
    background-color: #ffd390;
    margin-bottom: 1em;
    -webkit-font-smoothing: antialiased;
    height: 2.1em;
    overflow: hidden;
    -webkit-transition: height 0.5s;
    -moz-transition: height 0.5s;
    -ms-transition: height 0.5s;
    transition: height 0.5s;
}
.custom-wrapper.open {
    height: 14em;
}
.custom-menu-3 {
    text-align: right;
}
.custom-toggle {
    width: 34px;
    height: 34px;
    display: block;
    position: absolute;
    top: 0;
    right: 0;
    display: none;
}
.custom-toggle .bar {
    background-color: #777;
    display: block;
    width: 20px;
    height: 2px;
    border-radius: 100px;
    position: absolute;
    top: 18px;
    right: 7px;
    -webkit-transition: all 0.5s;
    -moz-transition: all 0.5s;
    -ms-transition: all 0.5s;
    transition: all 0.5s;
}
.custom-toggle .bar:first-child {
    -webkit-transform: translateY(-6px);
    -moz-transform: translateY(-6px);
    -ms-transform: translateY(-6px);
    transform: translateY(-6px);
}
.custom-toggle.x .bar {
    -webkit-transform: rotate(45deg);
    -moz-transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    transform: rotate(45deg);
}
.custom-toggle.x .bar:first-child {
    -webkit-transform: rotate(-45deg);
    -moz-transform: rotate(-45deg);
    -ms-transform: rotate(-45deg);
    transform: rotate(-45deg);
}
@media (max-width: 47.999em) {
    .custom-menu-3 {
        text-align: left;
    }
    .custom-toggle {
        display: block;
    }
}
</style>
<body>


<div class="custom-wrapper pure-g" id="menu">
    <div class="pure-u-1 pure-u-md-1-3">
        <div class="pure-menu">
            <a href="#" class="pure-menu-heading custom-brand">VSH2A verkefni 3</a>
            <a href="#" class="custom-toggle" id="toggle"><s class="bar"></s><s class="bar"></s></a>
        </div>
    </div>
    <div class="pure-u-1 pure-u-md-1-3">
        <div class="pure-menu pure-menu-horizontal custom-can-transform">
            <ul class="pure-menu-list">
                <li class="pure-menu-item"><a href="index.html" class="pure-menu-link">Forsíða</a></li>
                <li class="pure-menu-item"><a href="table.html" class="pure-menu-link">Tafla</a></li>
                <li class="pure-menu-item"><a href="form.html" class="pure-menu-link">Form</a></li>
                <li class="pure-menu-item"><a href="takkar.html" class="pure-menu-link">Hnappar</a></li>
            </ul>
        </div>
    </div>
    <div class="pure-u-1 pure-u-md-1-3">
        <div class="pure-menu pure-menu-horizontal custom-menu-3 custom-can-transform">
            <ul class="pure-menu-list">
                <li class="pure-menu-item"><a href="#" class="pure-menu-link">Crazy</a></li>
                <li class="pure-menu-item"><a href="#" class="pure-menu-link">Bjál</a></li>
            </ul>
        </div>
    </div>
</div>


<script>
(function (window, document) {
var menu = document.getElementById('menu'),
    WINDOW_CHANGE_EVENT = ('onorientationchange' in window) ? 'orientationchange':'resize';
function toggleHorizontal() {
    [].forEach.call(
        document.getElementById('menu').querySelectorAll('.custom-can-transform'),
        function(el){
            el.classList.toggle('pure-menu-horizontal');
        }
    );
};
function toggleMenu() {
    // set timeout so that the panel has a chance to roll up
    // before the menu switches states
    if (menu.classList.contains('open')) {
        setTimeout(toggleHorizontal, 500);
    }
    else {
        toggleHorizontal();
    }
    menu.classList.toggle('open');
    document.getElementById('toggle').classList.toggle('x');
};
function closeMenu() {
    if (menu.classList.contains('open')) {
        toggleMenu();
    }
}
document.getElementById('toggle').addEventListener('click', function (e) {
    toggleMenu();
});
window.addEventListener(WINDOW_CHANGE_EVENT, closeMenu);
})(this, this.document);
</script>



<style>
.main {
    padding: 2em;
    color: black;
}
</style>

<div class="main">

    <!-- row 1 -->
        <header class="pure-g">
            <div class="pure-u-1 pure-u-sm-12-24 pure-u-md-10-24">
                <a href="index.html"><img src="img/logo.png" width="90%" alt="Wisdom Pets. click for home." class=""></a>
            </div>
            <div class="pure-u-1 pure-u-sm-12-24 pure-u-md-14-24">
                <img src="img/animals.jpg" width="90%" alt="Nú eru góð ráð dýr!" class="">
            </div>
        </header>     
        <!-- row 2 -->
        <section class="pure-g">
            <article class="pure-u-1 pure-u-md-1 pure-u-lg-16-24">
                <!-- nested row 1-->
                <section class="pure-g">
                    <div class="pure-u-1 pure-sm-17-24 pure-u-md-15-24 pure-u-lg-15-24">
                        <h1>Form</h1>
                        <p>Wisdom Pet Medicine is a state-of-the-art veterinary hospital,   featuring the latest in diagnostic and surgical equipment, and a staff   of seasoned veterinary specialists in the areas of general veterinary   medicine and surgery, oncology, dermatology, orthopedics, radiology,   ultrasound, and much more. We also have a 24-hour emergency clinic in   the event your pet needs urgent medical care after regular business   hours.</p>
                        <p>At Wisdom, we strive to be your pet&rsquo;s medical experts from youth   through the senior years. We build preventative health care plans for   each and every one of our patients, based on breed, age, and sex, so   that your pet receives the most appropriate care at crucial milestones   in his or her life. Our overarching goal is to give your pet the best   shot possible at a long and healthy life, by practicing simple   preventative care. We even provide an online Pet Portal where you can   view all your pet&rsquo;s diagnostic results, treatment plans, vaccination and   diagnostic schedules,  prescriptions, and any other health records.</p>
                    </div>
                    <div class="pure-u-1 pure-sm-7-24 pure-u-md-9-24 pure-u-lg-9-24">
                        <img src="img/goldfish.jpg" width="90%">
                    </div>
                </section>
                <!-- nested row 2-->
                <section class="pure-g">
                    <div class="pure-u-1 pure-u-sm-12-24 pure-u-md-12-24 pure-u-lg-6-24">
                        <h4><span class="glyphicon glyphicon-pushpin"></span> Vaccinations</h4>
                        <p>Dogs, cats, rats and snakes are susceptible to a variety of illnesses that can be completely prevented by following the appropriate vaccination schedule.</p>
                        <p><a href="#" class="">Read more >></a></p>
                    </div>
                    <div class="pure-u-1 pure-u-sm-12-24 pure-u-md-12-24 pure-u-lg-6-24">
                        <h4><span class="glyphicon glyphicon-ok"></span> Checkups</h4>
                        <p>Regular checkups are a key factor in pet wellness, and can often unearth problems that could lead to health issues down the road.  </p>
                        <p><a href="#" class="">Read more >></a></p>
                    </div>
                    <div class="pure-u-1 pure-u-sm-12-24 pure-u-md-12-24 pure-u-lg-6-24">
                        <h4><span class="glyphicon glyphicon-heart"></span> Senior Pets</h4>
                        <p>Senior pets generally require more medical attention than their younger counterparts, just as senior humans do. So when is a pet considered “senior”? </p>
                        <p><a href="#" class="">Read more >></a></p>
                    </div>
                    <div class="pure-u-1 pure-u-sm-12-24 pure-u-md-12-24 pure-u-lg-6-24">
                        <h4><span class="glyphicon glyphicon-cutlery"></span> Diet Plans</h4>
                        <p>Wisdom veterinarians have all had extensive training in pet nutrition and are your best resources when considering changing your pet’s diet. </p>
                        <p><a href="#" class="">Read more >></a></p>
                    </div>
                </section><!-- end nested row -->
            </article>    
            <aside class="pure-u-1 pure-u-md-1 pure-u-lg-8-24">

                <div class="tabs">
    
   <div class="tab">
       <input type="radio" id="tab-1" name="tab-group-1" checked>
       <label for="tab-1">Sign In</label>
       
       <div class="content">
           <form class="pure-form" style="padding: 10px;">
                    <fieldset class="pure-group">
                        <input type="text" class="pure-input-1" placeholder="Username" required>
                        <input type="password" class="pure-input-1" placeholder="Password" required pattern="^[a-zA-Z][a-zA-Z0-9-_.]{1, 20}$">
                    </fieldset>
<button type="submit" class="pure-button pure-input-1 pure-button-primary">Sign in</button>
                </form>
       </div> 
   </div>
    
   <div class="tab">
       <input type="radio" id="tab-2" name="tab-group-1">
       <label for="tab-2">Register</label>
       
       <div class="content">
           <form class="pure-form pure-form-aligned">
                    <fieldset>
                        <div class="pure-control-group">
                            <label for="name">Username</label>
                            <input id="name" type="text" placeholder="Username" required>
                        </div>

                        <div class="pure-control-group">
                            <label for="password">Password</label>
                            <input id="password" type="password" placeholder="Password" required>
                        </div>

                        <div class="pure-controls">


                            <button type="submit" class="pure-button pure-button-primary">Submit</button>
                        </div>
                    </fieldset>
                </form>
       </div> 
   </div>
    
    <div class="tab">
       <input type="radio" id="tab-3" name="tab-group-1">
       <label for="tab-3">Tab Three</label>
     
       <div class="content">
           stuff
       </div> 
   </div>
    
</div>
            </aside>
        </section><!-- end row 2 -->
        <!-- row 3 -->
        <footer class="pure-u-1">
            <p>This not a real veterinary medicine site, and is not meant to diagnose or offer treatment. Please see your veterinarian for all matters related to your pet's health.</p>
        </footer>
        <!-- javascript -->
        <script src=""></script>
</div>



</body>
</html
