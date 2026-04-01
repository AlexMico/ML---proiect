Predicția Traiectoriei Baloanelor Meteorologice cu Machine Learning
Despre proiect
Ideea acestui proiect a pornit de la o întrebare simplă: știind condițiile atmosferice la momentul lansării unui balon meteorologic, putem prezice unde o să ajungă?
Baloanele meteorologice sunt lansate zilnic de sute de stații din toată lumea. Ele urcă până la 30-35 km altitudine timp de 1.5-3 ore, după care membrana explodează și sonda coboară cu parașuta. 
Traiectoria lor depinde enorm de vânt, temperatură și presiune la fiecare nivel de altitudine — exact genul de problemă unde ML-ul poate fi util.
Scopul proiectului este să antrenez modele care să estimeze traiectoria completă a unui balon (latitudine, longitudine și altitudine în timp) și să prezică cât mai precis punctul de aterizare.
Zona geografică
Proiectul se va concentra pe Europa Centrală și de Est (România, Ungaria, Polonia, Austria, Cehia). Această zonă oferă suficiente stații de lansare pentru a colecta un dataset consistent, 
are diversitate meteorologică bună și este acoperită excelent de toate sursele de date folosite.
Surse de date
1. SondeHub API
De pe sondehub.org voi colecta traiectorii reale GPS ale baloanelor lansate în ultimele luni.
Voi folosi API-ul public pentru a descărca automat sute de lansări din zona țintă, fiecare conținând poziția balonului înregistrată la fiecare câteva secunde.
Parametri folosiți:

serial — ID-ul unic al lansării
lat, lon — poziția GPS
alt — altitudinea (metri)
vel_v — viteza verticală (m/s)
vel_h — viteza orizontală (m/s)
heading — direcția de deplasare
temp — temperatura măsurată de sondă
datetime — timestamp-ul fiecărui punct

2. University of Wyoming — Sounding Data
De pe weather.uwyo.edu voi descărca profilele atmosferice la momentul lansărilor.
Acestea descriu cum arată atmosfera pe verticală — esențial pentru că vântul la 20 km altitudine e complet diferit față de cel de la sol.
Parametri folosiți:

HGHT — altitudinea fiecărui nivel (metri)
TEMP — temperatura (°C)
DRCT — direcția vântului (grade)
SKNT — viteza vântului (noduri)
PRES — presiunea atmosferică (hPa)
RELH — umiditatea relativă (%)

3. NOAA IGRA — Integrated Global Radiosonde Archive
De pe ncei.noaa.gov voi lua date istorice de la stațiile de radiosondaj din regiune.
Acest dataset conține zeci de ani de măsurători și va fi folosit atât pentru date despre traiectoriile baloanelor cât și pentru contextul meteorologic pe termen lung.
Parametri folosiți:

PRESS — presiunea la fiecare nivel
GPHGT — altitudinea geopotențială
TEMP — temperatura
WDIR — direcția vântului
WSPD — viteza vântului
DEWPT — temperatura punctului de rouă
