I learned very early on that the Bosch D-Jet fuel injection system that was first installed in the 1970 model year is decent when in good working condition, but very difficult to restore to factory settings 50-plus years on. The sensors are difficult or impossible to get, and items like the mechanical Auxiliary Air Slide AKA idle control valve are no longer available and not really rebuildable. Because of this I decided to build my own standalone EFI computer, something I had wanted to do for over a decade after owning a 1973 Honda CB750 motorcycle and learning what it takes to maintain a bank of 4 carburetors.

Although the standard choice would be to build a MegaSquirt system, while planning I discovered the Speeduino project. Speeduino is similar to MegaSquirt in practice, but uses an open source Arduino microcontroller, open source motherboard designs, and open source software. As someone who's been using Linux for over 25 years the open nature of the project overrode the possible challenges of a much smaller and less supported platform, so I put together the following bill of materials.

Components:
* Speeduino UA4C kit w/ wiring harness from SpeedyEFI 
https://speedyefi.com/product/fishdog-ua4c-seawolf-speeduino-ecu/
* YoshiFab Redblock B20 DSM CAS w/ high resolution disk 
https://yoshifab.com/store/vintage-volvo-b16-18-20-dsm-cas-adapter.html
* 1995 Volvo 850 TPS - readily available, adapts to stock throttle body
https://www.rockauto.com/en/moreinfo.php?pk=10065264&cc=1433979&pt=5136&jsn=858
* Intake Air Temp Sensor
AEM Air Inlet Temperature Sensor Kit 1/8 NPT with Bung IAT 30-2014, $55
* Coolant Temp Sensor
You can reuse the stock sensor, but if you need a new one the stock item is hard to find and either expensive or unavailable. Instead I bought a new Bosch 0280130040, it has the same thread size and was used on 80's and 90's VW and Audi vehicles and is still easy to find. $27
* 4 new LS2 Truck coils, pigtails, plug wires, and mounting bracket from Herko. $140
* Wideband O2 Sensor Kit - Innovate Motorsports LC-2
* O2 bung to weld on to exhaust pipe
* Fuse/circuit breaker/relay block
* [Datsun 240Z Firewall grommet](https://zcardepot.com/products/wiring-harness-rubber-boot-grommet-firewall-240z#) - couldn't find a stock replacement and the hole size is the same
* Block off plate for stock IAC valve, Volvo part nr 419895
* Electronic IAC valve - Delphi w/ wiring pigtail and 3d-printed hose adapter
DELPHI CV10017
https://www.thingiverse.com/thing:5422143 - TY Frank Krause
* 1/8 ID hose to run from the intake manifold back to the MAP sensor port on the ECU.
* Tachometer conversion to work with modern ECU tach signal from [Spiyda](https://spiyda.com/tachometer-electronics/tachometer-modules.html)
* Injector resistors or resistor pack or High-Z conversion
### Injector notes
At first I rebuilt the stock Bosch low-Z injectors (part nr 0280150036) and had them cleaned and flow tested, and used an [Injector Resistance Calculator](https://efistuff.orgfree.com/InjectorResistorCalculator.html) to spec a set of resistors wired inline to the injectors. Later, I found a [kit from Injector Rehab](https://injector-rehab.com/product/hose-end-adapter-hat-for-ev1-injector/) to allow the use of later EV1 style injectors on the early hose barb fuel rail, so I switched to a set of Bosch injectors from a 1997-2000 BMW inline 6 engine used in the 328i, M3, and Z3. Bosch part number 0280150440, you can get a set of 6 for pretty cheap. They are high quality and don't generally go bad, and you can get a testing and cleaning kit on Amazon for about $20 that uses a 12V battery to switch the injector on and off, and a little plastic adapter that lets you attach a can of carb cleaner to the injector. These are spec'ed at 231cc/min @ 43.5psi and should be sufficient for up to 200hp 4cyl. You can use an adjustable fuel pressure regulator and a cheap pressure gauge (I attached it to the cold start injector barb before blocking it off) to adjust up from the stock 29psi the D-Jet used.

### General Notes:
* Sensor grounds must tie back to the ECU, not grounded to the body, engine, or battery.
* I made my own air temp sensor plate from a 1/8npt bung and a piece of aluminum bar to fit in place of the original cold start injector, which is no longer needed.
* You can figure out the timing by using a timing light and rotating the CAS unit until you get the 10deg mark set properly on the crank pulley. I did this with the injectors unplugged and a partner cranking the engine over, only took a few seconds.
* The DSM cas should have a nice clean signal and not need to be converted, so set the jumpers on the Speeduino appropriately.
* I made my own TPS adapter plate by measuring how much it needed to be spaced out, and then marked where the mounting holes would be when the throttle is fully closed, and hacking it together from a few small pieces of aluminum welded together. You could make a much nicer looking adapter with a 3d printer if you had the CAD skills. If anyone does this please let me know!

### Initial installation
Looking back at my notes, it's only been a year and half since I started. 