# Podstawy matematyczne

Czy wiesz co to jest medal Fieldsa? Jest to nagroda przyznawana wyłącznie wybitnym matematykom w wieku poniżej 40 lat. Nazywana jest matematycznym Noblem. Co ciekawe żaden matematyk nie otrzyma nagrody Nobla – zgodnie z życzeniem fundatora. Sam John Charles Fields (1863-1932) był Kanadyjskim matematykiem. John Charles Fields miał jednego doktoranta – Samuela Beatty (1881-1970). &#x20;

Samuel Beatty w 1926 roku opublikował następujące twierdzenie \[1]:

Jeśli p, q są dodatnimi liczbami niewymiernymi i zachodzi pomiędzy nimi zależność

<p align="center"> <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAF8AAAB+CAMAAAB1Yj1UAAAAAXNSR0IArs4c6QAAAH5QTFRFAAAAD0dhEEd+EEeZEGmZEGm0EIrOQkd+QkdhQmlhQoqZQoq0QorOQqjnbEdhbGlhbIp+bIq0bIrObKi0bKjObMbnbMb/k2lhk4p+k+P/uYp+uYphuf//ueP/3Kh+3KiZ3MaZ3Ma03P/O3P///8aZ/8a0/+O0///O/+PO///nEPl0ZwAAAAF0Uk5TAEDm2GYAAAAJcEhZcwAAFiUAABYlAUlSJPAAAAAZdEVYdFNvZnR3YXJlAE1pY3Jvc29mdCBPZmZpY2V/7TVxAAABm0lEQVRoQ+2aW1ODMBCFm2g1WgvesVJbFQTy//+gSXAsl5JdYeiUevLQl5492XxsNmGG2QwDBEAABEAABEAABEAABEAABEDgIATEuOMga8AkIAACIAACIAACIHBsBN4vV6yUuLq62UcoztYMf66uYZXeJBuOP1e3J1OWv4nj6ppTcOO4Ovgzyq0i4XLl6hqz60g+cRLi6qzXbivmgXtDWlIzcHXWpwiF9LcEHc0Tasau/4sXeUu1hCH+r49JHhAtYYi/WdcU/NPam3P9eU4hf1957fKvLLIM6Fh2S+et3inwOe3nO2L/se2TaphD+kOmymKTz901NsS/b9/9n3FbJVfmPJvTV1BzARXXzKvwL8vtMlMP90mqyAN4Y87oIvj7sZmpC3vgmB/vyGwGOqJkbQ93q3HR3hGXMk9Nd4THdsmpIALLDZES237PFI4MvZ2cLO+HP9ExmZeOztfFXdgDv7wSYvFGbs4vJRafQU/8pPvP2Ukus2VEF2YlpMcF2jRTNlMdUddKJgfIQAAEQAAEQAAEQOCECYz7eYX4BlpvHZG95V6zAAAAAElFTkSuQmCC" alt=""></p>

to sekwencje

<p align="center"> <img src=".gitbook/assets/unknown (2).png" alt=""> </p>

oraz

<p align="center">  <img src=".gitbook/assets/unknown (1) (1).png" alt=""> </p>

oraz dokonują podziału zbioru dodatnich liczb całkowitych.

Te dwie sekwencje dokonują podziału zbioru liczb naturalnych. Oznacza to że dysponując dwoma liczbami niewymiernymi, pomiędzy którymi wskazana w twierdzeniu zależność – będziemy mogli podzielić zbiór wszystkich liczb naturalnych na dwa rozłączne zbiory (Rys. 1).

<p align="center"><img src=".gitbook/assets/unknown.png" alt=""></p>

<p align="center">Rys. 1 Zbiory rozłączne</p>

Twierdzenie Beaty samo w sobie jest bardzo ciekawą obserwacją – jednak w przypadku systemów komputerowych mamy pewien problem z liczbami niewymiernymi. Liczby rzeczywiste – pomimo faktu że w niektórych językach programowania pojawia się czasem słowo Real lub Float jako reprezentanta typu liczby rzeczywistej, z liczbami rzeczywistymi nie mają wiele wspólnego. Fundamentalny problem polega na tym że ich nie mamy i zapewne nigdy mieć nie będziemy.

I tu nasza podróż gwałtownie by się skończyła gdyby nie powstało kolejne twierdzenie. Sytuacja diametralnie uległa zmianie za sprawą matematyka – Aviezri Siegmund Fraenkel (1926) specjalizującego się w kombinatorycznych aspektach teorii gier.

Przedstawił on w 1969 roku następujące twierdzenie \[2]:

Sekwencje ![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAFQAAAAhCAMAAABwWnyBAAAAAXNSR0IArs4c6QAAAIRQTFRFAAAAAAAAAAA6AABmADpmADqQAGa2OgAAOjo6OjpmOmaQOma2OpDbZgAAZjoAZjpmZmZmZmaQZpC2ZpDbZrb/kDoAkGY6kGaQkLbbkNv/tmYAtmY6tpA6ttvbttv/tv/btv//25A627Zm27aQ29u229vb2////7Zm/9uQ/9u2//+2///bLoMD1AAAAAF0Uk5TAEDm2GYAAAAJcEhZcwAAFiUAABYlAUlSJPAAAAAZdEVYdFNvZnR3YXJlAE1pY3Jvc29mdCBPZmZpY2V/7TVxAAABzElEQVRIS+1VyXLCMAy1y2IKDXRLWqClMaFk+///qyXLsgMkhmNn0IExsvUkPS0R4i53Bs4YKJZPV7NSylEuhB5/Dlu06UPkRWiv5RT+FsvJkdV1piTI7GVHuiYJrqMBmwjW+KhNIWI8beffv5WainavpE3ZX0YB4UGTYKB4ssG0KQBt5Lv5rZR1WRL4VZBgBsYoGnGEBpwmQbQ2Rd2NgQrtuaJQMcZKIRlEDnBxi2yCPtlgdCU0QinRGaHpIPs6k3K8dg+8qz59YGuPezVHmi3BKKWa7IQe/bj6xvTGu8vScIliADwJcKwUZFCpZ+8GYfv07gbe2DodMknlorZzhWuSk26ggp7p2Z13DHkDC9zLFBB3HzNqAz3Xd0AdEbZQHpRYD/rQ4vbpO6CuMlR9LhQdgsJZ0D49VNYVqkloZEuaB57Wzpxx9kSpmz/WB0lwNiaCBdWW2gIjaj++qHAcxYk+RLXNb7qAtsAhe7PXPKYG5VivcjPQ9cp0G4Oe6ANQGlPXo3L2ysuQF8pWysXReJWP0MG+sbv6AJQWSocR+tOzUQYsyHBwD1+8bBJLeb9E1tulz4mOfbQKNc6HvRZL3iqR+Nw17ru7/CcG/gCQkii0UN06AQAAAABJRU5ErkJggg==) oraz ![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAFMAAAAhCAMAAACShmf4AAAAAXNSR0IArs4c6QAAAH5QTFRFAAAAAAAAAAA6AABmADpmADqQAGa2OgAAOjo6OjpmOmaQOma2OpC2OpDbZgAAZjoAZjo6ZmaQZpCQZpC2ZpDbZrb/kDoAkGY6kLbbkNv/tmYAtmY6ttvbttv/tv//25A627Zm27aQ29u229vb2////7Zm/9uQ/9u2//+2///biiUUyAAAAAF0Uk5TAEDm2GYAAAAJcEhZcwAAFiUAABYlAUlSJPAAAAAZdEVYdFNvZnR3YXJlAE1pY3Jvc29mdCBPZmZpY2V/7TVxAAAB7klEQVRIS+1V7XaCMAylG1p1G+xL3FCHOEF4/xdcm6RpWunc2W/7q+cmuc3HJWTZ7dw6IDrQlk9/70en7r+yJv/4NWKs7pzDuNVKLfcX7hJv1NzY23J2cm7njYkyZ/HiIoeCrUOR77NzYfIIj8RNBp/WOlbkNm5Xu+9ez7PxoBXWyza+NmodUpIL4kNh04QL5DJWlqcGW6/xvY64/bXxCEaTC+K9di/iG42lGQogGyuAgjTxFXzTH1ct4o3olL0C2mtoBHnaRtDpNbgPcT9DvPYSqW0OnVVApyCUyEShWCLlL/JM4ZmPxdtBr0ALolC4tmUODRAnhZvsqEaTB5wZaMn1iq6m1+8RI7hM4bZU6i2O6LhRNCmcC/TRehz0Q0SawgWnI6+pe8xJlUwoCSq8wAWnawLOSNROQTRCn2wKF5xuKDR3PyNQBsvCc6Zw64ozYvV1qGwuyRlwRfiTwkUsc9Q4C9Y8K9ulS9QRHogMXXtaQscNaYa/zU6px1N2LuljZ+1FeFCBFYrTplq88fJzO6RWr89GtssdRjFnhAvOi/3FNkpU7BIwuYAYl432WzmYAEzN2sRmxlGS9CPcB6cfsz7w7+BaMapx2yfCmbPVefw3CJNty/XEZ0I9mPz9wYa7dkjZF24p/Brfzf6/DvwAi9wt1xO4OhsAAAAASUVORK5CYII=) dokonują podziału zbioru ![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABIAAAAhCAMAAADj/gtmAAAAAXNSR0IArs4c6QAAAFFQTFRFAAAAAAAAAAA6AABmADqQAGa2OgAAOgA6Ojo6OpDbZgAAZmYAZraQZrb/kDoAkNv/tmYAtv+2tv//25A625Bm27Zm2////7Zm/9uQ//+2///bQQE1RQAAAAF0Uk5TAEDm2GYAAAAJcEhZcwAAFiUAABYlAUlSJPAAAAAZdEVYdFNvZnR3YXJlAE1pY3Jvc29mdCBPZmZpY2V/7TVxAAAAk0lEQVQoU82QWxaDIAxEEx9obcVHtCD7X2iTEKRLMB+QM3AnAwDPrYCIvcSTpvtq0AOx3bNmCoT2jbNI0enGRd1pZLOYtPbXpCRlHuCaXskLmbxOEYdhARKSz0wKfD06XkK14slK3lbJy3Uh15Iqh2Fyq1bqwOTnL6g+i3As7slnh+juB57WMWlB64cQlqCW9/nbD44SBscFrerRAAAAAElFTkSuQmCC) wtedy i tylko wtedy gdy następujące pięć warunków zostanie spełnionych:\
<br>

