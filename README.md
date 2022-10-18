
<html>
<head>
<title>Digital_clock</title>
<style>
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body{
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    background: #2f3c3e;
}
#time{
    position: relative;
    width: 250px;
    height: 250px;
    display: flex;
    justify-content: center;
    align-items: center;
}
#time .circle{
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
}
#time .circle svg{
    position: relative;
    transform: rotate(270deg);
}
#time .circle:nth-child(1) svg {
    width: 250px;
    height: 250px;
}
#time .circle:nth-child(2) svg {
    width: 210px;
    height: 210px;
}
#time .circle:nth-child(3) svg {
    width: 170px;
    height: 170px;
}
#time .circle svg circle{
    width: 100%;
    height: 100%;
    fill: transparent;
    stroke: var(--clr);
    stroke-width: 5;
    transform: translate(5px,5px);
    /* opacity: 0.25; */
}
 #time .circle:nth-child(1) svg circle{
    stroke-dasharray: 760;
    stroke-dashoffset: 760;
}
#time .circle:nth-child(2) svg circle{
    stroke-dasharray: 630;
    stroke-dashoffset: 630;
}
#time .circle:nth-child(3) svg circle{
    stroke-dasharray: 510;
    stroke-dashoffset: 510;
} 
.dots{
    position: absolute;
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: flex-start;
    z-index: 10;
}

.dots::before{
 content: '';
 top: -3;
 position: absolute;
 width: 15px;
 height: 15px;
 background: var(--clr) ;
 border-radius: 50%;
 box-shadow: 0 0 20px var(--clr),
 0 0 40px var(--clr),
 0 0 60px var(--clr),
 0 0 80px var(--clr);
}
 .timeBx{
    display: flex;
    position: absolute;
    inset: 0;
    justify-content: center;
    align-items: center;
    width: 100%;
    color: white;
    font-family: 'Courier New', Courier, monospace;
    gap: 25px;
    font-size: 1.38em;
    font-weight: bold;
 }
 .timeBx #hours::after,
 .timeBx #minutes::after{
    content: '❤';
   overflow: hidden;
    position: absolute;
 }
 .timeBx div{
    color: var(--c);
    text-shadow: 0 0 20px var(--c),
    0 0 40px var(--c),
    0 0 60px var(--c),
    0 0 80px var(--c);
 }
 .ap{
    position: absolute;
    transform: translateY(-15px);
    font-size: 0.5em;
    right: 56px;
 }
 </style>
 </head>
 <body>
  <div id="time">
        <div class="circle" style="--clr: #ff2972;">
            <div class="dots sec_dot" style="transform: rotate(300deg);"></div>
            <svg>
                <circle cx="120" cy="120" r="120" id="ss" style="stroke-dashoffset: 126.667;"></circle>
            </svg>
        </div>
        <div class="circle" style="--clr: #fee800;">
            <div class="dots min_dot" style="transform: rotate(138deg);"></div>
            <svg>
                <circle cx="100" cy="100" r="100" id="mm" style="stroke-dashoffset: 388.5;"></circle>
            </svg>
        </div>
        <div class="circle" style="--clr: #04fc43;">
            <div class="dots hr_dot" style="transform: rotate(690deg);"></div>
            <svg>
                <circle cx="80" cy="80" r="80" id="hh" style="stroke-dashoffset: -467.5;"></circle>
            </svg>
        </div>
        <div class="timeBx">
            <div id="hours" style="--c:#04fc43;">11</div>
            <div id="minutes" style="--c:#fee800;">23</div>
            <div id="seconds" style="--c:#ff2972;">50</div>
            <div class="ap" style="--c:#fff;">
                <div id="ampm">PM</div>
            </div>
        </div>
    </div>
    <script>
     setInterval(() => {
            // for analog clock
            let hh = document.getElementById('hh');
            let mm = document.getElementById('mm');
            let ss = document.getElementById('ss');

            let sec_dot = document.querySelector('.sec_dot');
            let min_dot = document.querySelector('.min_dot');
            let hr_dot = document.querySelector('.hr_dot');


            let h = new Date().getHours();
            let m = new Date().getMinutes();
            let s = new Date().getSeconds();


            hh.style.strokeDashoffset = 510 - (510 * h) / 12;
            //12 hrs clock``
            mm.style.strokeDashoffset = 630 - (630 * m) / 60;
            //60 minute
            ss.style.strokeDashoffset = 760 - (760 * s) / 60;
            //60 second
            sec_dot.style.transform = `rotate(${s * 6}deg)`;
            //360/60sec = 6
            min_dot.style.transform = `rotate(${m * 6}deg)`;
            //360/60min = 6
            hr_dot.style.transform = `rotate(${h * 30}deg)`;
            //360/ 12hrs = 30


            // for digital clock box 
            let hours = document.getElementById('hours');
            let minutes = document.getElementById('minutes');
            let seconds = document.getElementById('seconds');
            let ampm = document.getElementById('ampm');

            let am = h >= 12 ? "PM" : "AM";

            // convert 24hr in 12hr
            if (h > 12) {
                h -= 12;
            }

            // add zero before single digit
            h = (h < 10) ? "0" + h : h;
            m = (m < 10) ? "0" + m : m;
            s = (s < 10) ? "0" + s : s;


            hours.innerHTML = h;
            minutes.innerHTML = m;
            seconds.innerHTML = s;
            ampm.innerHTML = am;


        })
    </script>
    </body>
    </html>
