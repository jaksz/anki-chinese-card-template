# Front template

```
<div class="info">What is the definition?</div>
<div class=chinese>{{Hanzi}}</div>
```

# Styling

```
.card {
 font-family: arial;
 font-size: px;
 text-align: center;
 color: black;
 background-color: white;
}
.card { word-wrap: break-word; }
/* .win .chinese { font-family: "MS Mincho", "ＭＳ 明朝"; }*/
.mac .chinese { }
/*.linux .chinese { font-family: "Kochi Mincho", "東風明朝"; }*/
/* .mobile .chinese { font-family: "Hiragino Mincho ProN"; }  */
.chinese { font-size: 80px;}
.reading { font-size: 50px;}
.meaning { font-size: 24pt;}
.comment {font-size: 15px; color:grey;}
.tags {color:gray;text-align:right;font-size:10pt;}
.note {color:gray;font-size:12pt;margin-top:20pt;}
.hint {font-size:12pt;}
.answer { background-color:bisque; border:dotted;border-width:1px}

.tone1 {background: #b3e0ff; color: #1aa3ff; text-decoration: underline overline;}
.x{
margin: 10px;
display: inline-block;
    -webkit-animation: tone1 1s infinite;
}
@-webkit-keyframes tone1 {
    0%   {top: 0px;}
    50%  {-webkit-transform: scaleX(1.5);}
    100% {top: 0px;}
}

.tone2 {
background: #fff7a0; color: #c9bc28;}
.x{
margin: 10px;
display: inline-block;
-webkit-animation: tone2 1s infinite;
}
@-webkit-keyframes tone2 {
    0%   {top: 0px;}
    50%  {-webkit-transform: rotate(-15deg);}
    100% {top: 0px;}
}

.tone3 {
background: #ddffda; color: #3bbf31;}
.x{
margin: 10px;
    position: relative;
    -webkit-animation: tone3 1s infinite;
}
@-webkit-keyframes tone3 {
    0%   {top: -5px;}
    50%  {top: 5px;}
    100% {top: -5px;}
}

.tone4 {background: #ffb3b3; color: #ff0000; font-style:italic; font-weight:bold;}
.x{
display: inline-block;
margin: 10px;
position: relative;
    -webkit-animation: tone4 1s infinite;
}
@-webkit-keyframes tone4 {
    0%   {top: -15px; -webkit-transform: scale(1);;opacity: 0}
  10%   {top: -15px; -webkit-transform: scale(1);;opacity: 0}
20%   {top: 15px; -webkit-transform: scale(1.2);;opacity: 100}

80%   {top: 15px; -webkit-transform: scale(1.2);opacity: 100}

    100% {top: 15px;-webkit-transform: scale(1);opacity: 0}
}



.tone5 {color: gray;}



.hide {
text-indent: -9999px;
}

.info {
text-align:left;
}

.nocolors {
color: black;
}
```

# Back template

```
<div class="meaning" id="meaning">{{Meaning}}</div>
{{#Color}}{{#Reading}}{{Sound}}{{/Reading}}{{/Color}}

<div class=reading id=reading>{{Reading}}</div>
<hr>
<div id="coloredhanzi" class="chinese">{{Hanzi}}</div>

<br/>{{Notes}}<br/>{{Meme}}


<script>
document.getElementById('meaning').innerHTML = document.getElementById('meaning').innerHTML.split('<br>').join('| ');
</script>


<script>
var reading = document.getElementById('reading').textContent;
var hanzi = document.getElementById('coloredhanzi').textContent;
hanzi = hanzi.split("")
reading = reading.split(" ")
var colored_hanzi = [];
if (hanzi && reading && hanzi.length == reading.length) {
	for (var h in hanzi) {
		var tone = reading[h].match(/\d/)[0]
		var colored_h = '<span class="tone' + tone + '">' + hanzi[h] + '</span>'
		colored_hanzi.push(colored_h)
	}
}
document.getElementById('coloredhanzi').innerHTML = colored_hanzi.join("");
</script>


<script>
var reading = document.getElementById('reading').innerHTML;
reading = reading.replace(/(1)</g, '--<');
reading = reading.replace(/(2)</g, '?<');
reading = reading.replace(/(3)</g, '√<');
reading = reading.replace(/(4)</g, '!<');
reading = reading.replace(/(5)</g, '<');
document.getElementById('reading').innerHTML = reading;
</script>
```
