## erychpatch
A Painkiller mod that was initally aimed to up the amount of dynamic lights concurrently existing on a map, which over time has resulted in various set of patches compiled into one.
Some of them are:
* Protection against crashes in case of high system uptime. Might happen in case you haven't picked up the habit of rebooting every so often. Comes after the fact that back then PCF made a brilliant assumption of CPU's internal timer (RDTSC) to be more reliable in a short run, so they never went on implementing a proper software one for counting in-game ticks. This resulted in game's stack space (INT32, limited to 4,294,967,295) for storing the timer value to overflow given enough time (approx. 21-24 days), and due to hardware timers generally NOT getting reset on quit - you're basically out of luck, cause before Overdose release much later on the devs have never put an effort on futureproofing the game. Fixed by essentially increasing the register size to INT64.
* Game:Print() Hooks - may come in handy for developing/breaking down LUA scripts. PCF had used it practially everywhere for debugging their every little thing, but threw it out of all release builds at some point. Brought it back in attempts to better analyze entities.
* Reworked TakeScreenshot() to now output in PNG format through GDI+. While that doesn't provide any performance boosts, it eliminates the issue of BMPs not cooperating well with paste buffer, plus reduces the size by half. Pretty much useless on Steam release with enabled ingame overlay.
* Partial ability to forward other DLL functions onto LUA side. Realized this is pretty much possible while I was tinkering around Game:Print() redirects. Still wip, yet to write a short explanation for it.

### Install
Just grab `dinput8.dll` from the releases page and put alongside `painkiller.exe`

### How to use
Right after booting the game `erychpatch.ini` is gonna get created, edit it to suit your needs. There's still much to be done though, expect things to change

***

100% confirmed to fully work with PK (Black Edition), along with unofficial expansions such as Atonement, Reload and probably rest of the mods based on vanilla engine, 
since the way it does things relies more on shitload of exported funcs, rather than classic signature finding and byte patching. 

#### TODO: 
- [x] Painkiller: Black Edition
- [x] Atonement
- [x] Reload
- [ ] Overdose
- [ ] Resurrecion
- [ ] Recurring Evil
- [ ] Redemption
