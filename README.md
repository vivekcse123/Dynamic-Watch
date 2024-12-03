<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dynamic Clock</title>
</head>
<style>
    *{
        padding: 0;
        margin: 0;
        box-sizing: border-box;
        font-family: sans-serif;
    }
    body{
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        min-height: 100vh;
        background-color: #2f363e;
      }
      .content{
        position: relative;
        min-height: 530px;
        box-shadow: 10px 50px 70px rgb(0,0,0,0.5),
        inset 5px 5px 10px rgba(0,0,0.2),
        inset 5px 5px 20px rgba(0,0,0.7),
        inset -5px -5px 15px rgba(0,0,0.9);
        border-top-left-radius: 225px;
        border-top-right-radius: 225px;
        border-bottom-left-radius: 6px;
        border-bottom-right-radius: 6px;
      }
    .clock{
        width: 450px;
        height: 450px;
        border-radius: 50%;
        display: flex;
        align-items: center;
        text-align: center;
        justify-content: center;
        position: relative;
        box-shadow: 10px 50px 70px rgb(0,0,0,0.5),
        inset 5px 5px 10px rgba(0,0,0.2),
        inset 5px 5px 20px rgba(0,0,0.7),
        inset -5px -5px 15px rgba(0,0,0.9);
    }
    .clock span{
        position: absolute;
        text-align: center;
        inset: 20px;
        color: #fff;
        transform: rotate(calc(30deg * var(--i)));
    }
    .clock span b{
        transform: rotate(calc(-30deg * var(--i)));
        display: inline-block;
        font-size: 2em;
        opacity: 0.5;
    }
    .clock::before{
        content: '';
        width: 8px;
        height: 8px;
        border: 2px solid #fff;
        position: absolute;
        border-radius: 50%;
    }
    .circle{
        position: absolute;
        width: 300px;
        height: 300px;
        border: 2px solid rgba(22,17,17);
        border-radius: 50%;
        opacity: 1;
    }
    .circle2{
        position: absolute;
        width: 240px;
        height: 240px;
        border: 2px solid rgba(22,17,17);
        border-radius: 50%;
    }
    .circle3{
        position: absolute;
        width: 180px;
        height: 180px;
        border: 2px solid rgba(22,17,17);
        border-radius: 50%;
    }
    .circle i{
        position: absolute;
        width: 6px;
        height: 50%;
        background-color: var(--clr);
        opacity: 0.75;
        transform-origin: bottom;
        transform: scaleY(0.5);
        align-items: flex-start;
        justify-content: center;
        align-items: center;
        margin: auto;
    }
    .circle:nth-child(1) i{
        width: 2px;
      }
    .circle:nth-child(2) i{
        width: 2px;
      }
      .circle:nth-child(1) i ::before{
          width: 5px;
          height: 5px;
          position: absolute;
          background-color: red;
      }
      .clock1{
          position: relative;
          width: 200px;
          height: 50px;
          display: flex;
          margin: auto;
          box-shadow: 10px 50px 70px rgb(0,0,0,0.5),
          inset 5px 5px 10px rgba(0,0,0.2),
          inset 5px 5px 20px rgba(0,0,0.7),
          inset -5px -5px 15px rgba(0,0,0.9);
          text-align: center;
          align-items: center;
          justify-content: center;
          border-radius: 10px;
      }
      .clock1 span{
          position: relative;
          font-size: 20px;
          font-weight: 700;
          margin: 3px;
      }
      #h{
          color: red;
      }
      #m{
          color: rgb(206, 209, 24);
      }
      #s{
          color: rgb(0, 153, 255);
      }
      #ap{
          color: rgb(0, 153, 255);
          animation: mymove 1s infinite;
          opacity: 1;
      }
      @keyframes mymove{
        0%{opacity: 0;}
        100%{opacity: 1;}
      }
</style>
<body>
    <div class="content">
        <div class="clock">
            <div class="circle" ><i style = '--clr: red;width: 2px;' id = 'hr'></i></div>
            <div class="circle circle2" ><i style = '--clr: rgb(206, 209, 24);' id = 'mn'></i></div>
            <div class="circle circle3" ><i style = '--clr: rgb(0, 153, 255);width: 2px;' id = 'sc'></i></div>
            <span style = '--i:1;'><b>1</b></span>
            <span style = '--i:2;'><b>2</b></span>
            <span style = '--i:3;'><b>3</b></span>
            <span style = '--i:4;'><b>4</b></span>
            <span style = '--i:5;'><b>5</b></span>
            <span style = '--i:6;'><b>6</b></span>
            <span style = '--i:7;'><b>7</b></span>
            <span style = '--i:8;'><b>8</b></span>
            <span style = '--i:9;'><b>9</b></span>
            <span style = '--i:10;'><b>10</b></span>
            <span style = '--i:11;'><b>11</b></span>
            <span style = '--i:12;'><b>12</b></span>
        </div>
        <br>
        <div class="clock1">
            <span id = 'h'></span>
            <span id = 'm'></span>
            <span id = 's'></span>
            <span id = 'ap'></span>
        </div>
    </div>

    <script>

        var hr = document.querySelector('#hr');
        var mn = document.querySelector('#mn');
        var sc = document.querySelector('#sc');

        setInterval(clock, 1000);
        function clock(){
            var d = new Date();
            var h = d.getHours() * 30;
            var m = d.getMinutes() * 6;
            var s = d.getSeconds() * 6;

            hr.style.transform = `rotateZ(${h+(m/12)}deg)`;
            mn.style.transform = `rotateZ(${m}deg)`;
            sc.style.transform = `rotateZ(${s}deg)`;
        }

        var h1 = document.querySelector('#h');
        var m1 = document.querySelector('#m');
        var s1 = document.querySelector('#s');
        var ap = document.querySelector('#ap');
        setInterval(clock1, 1000);
        function clock1()
        {
            var d1 = new Date();
            if(d1.getHours()>=12)
            {
                h1.innerHTML = d1.getHours() + ' : ';
                m1.innerHTML = d1.getMinutes();
                s1.innerHTML = ' : ' + d1.getSeconds() + '  ';
                ap.innerHTML = ' PM';
            }
            else{
                h1.innerHTML = d1.getHours() + ' : ';
                m1.innerHTML = d1.getMinutes();
                s1.innerHTML = ' : ' + d1.getSeconds() + ' '; 
                ap.innerHTML = ' AM';
            }
        }
    </script>
</body>
</html>
