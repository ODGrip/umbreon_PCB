<p>Browsing the social media of electronics enthusiasts I found a pokèmon-style PCB and I thought I'd make one too.<br></p>

<figure><img class="lazy" src="https://cdn.hackaday.io/images/2678691612370396424.PNG"></figure>


<p>I continued my research to find out if anyone had created a PCB based on my favorite pokèmon that is Umbreon and I found the following keychain where a black soldermark and a gold finish were used to get the pokèmon color pattern. (<a href="https://imgur.com/gallery/Zhk9J/comment/1046781989">https://imgur.com/gallery/Zhk9J/comment/1046781989</a>)<br><br></p>


<figure><img class="lazy" src="https://i.imgur.com/gE53YkN.jpeg"></figure>


<p>I wanted to do something similar but original.</p>


<p>I looked for an alternative to USB power, and WPT seemed like the optimal choice.<br>I asked a friend of mine to draw the pokémon for me,&nbsp;she is a very good drawer and illustrator,&nbsp;you can find her instagram profile at the following link:</p>


<p><a href="https://www.instagram.com/dfane.dsp/">https://www.instagram.com/dfane.dsp/</a></p>


<p>I also thought of using one side of the PCB to draw an ultraball that has the same color pattern as Umbreon.<br></p>


<p>I decided to make 2 prototypes</p>


<ul><li>using the standard for inductive charging</li><li>trying to rectify the small transmitted power in the absence of a chip that uses the standard</li></ul>


<hr>


<p><strong>The right way to design</strong><br></p>


<p><br>I looked for the standard used by the WPT and found that it is Qi.<br><a target="_blank" rel="noopener noreferrer" href="https://en.wikipedia.org/wiki/Qi_(standard)">https://en.wikipedia.org/wiki/Qi_(standard)</a><br></p>


<p>Googling "Qi IC" I found BQ51013 from Texas Instruments, this&nbsp;is an advanced, integrated, receiver IC&nbsp;for wireless power transfer in portable applications.<br></p>


<p>The schematic is easily found in the datasheet, the only unknown was the coil. I tried to design one with inductance similar to the one mentioned in the datasheet with a value of 10.4 μH.<br></p>


<p>Using ADS I found the right size to get this value with a high quality factor.</p>


<p>To insert the coil in kicad I used the following python script.<br></p>


<p><a href="https://gist.github.com/JoanTheSpark/e3fab5a8af44f7f8779c">https://gist.github.com/JoanTheSpark/e3fab5a8af44f7f8779c<br><br></a>After that, I simply copied the schematic into Kicad. Thanks to JLCPCB that offers an assembly service, I was able to use 0201 components obtaining a very compact design despite the presence of many components.<br><br></p>


<figure><img class="lazy" src="https://cdn.hackaday.io/images/6207581612372443012.jpg"></figure>


<hr>


<p><strong>The other way to design<br><br></strong>Using wires I created a coil that I placed above the WPT transmitter, with the oscilloscope I saw that in certain time intervals I could read a decent voltage with which I was able to turn on a LED.<br>I modified the previous coil trying to get the highest quality factor possible at 140 kHZ, surprisingly my previous design was already very close to the optimal one.</p>


<p>I created the schematic with Kicad to rectify the voltage, I added a voltage regulator to protect the LEDs,&nbsp;I chose to insert a capacitor in parallel to the coil to amplify the voltage received by resonance and I chose all the components so that they could withstand high voltages.<br></p>


<figure><img class="lazy" src="https://cdn.hackaday.io/images/3443261612373214745.PNG"></figure>

<figure><img class="lazy" src="https://cdn.hackaday.io/images/7735471612374835619.jpg"></figure>


<hr>


<p><strong>Results<br></strong></p>


<p>I made small mistakes in both designs but nothing that can't be fixed with a few patches.<br>PCBs that use the Qi standard communicate with the transmitter and require continuous delivery of power. On the contrary, the other PCBs normally blink. By placing both types above the transmitter, it is possible to have a constant transmission on both of them.</p>

<a href="//www.youtube.com/embed/qF8k0b99KyQ">Youtube Video</a>.
