# Cinema
## Choose useful attributes and relations

The STAR-MOVIES company operates a cinema chain with several cinemas (Name,
Address... ). Each cinema can have several halls where the films are shown. The seating plan of each hall should 
be recorded; a row and a seat must be indicated for each seat. A box should be managed like a row.
It must be possible to create a seating plan. Of course, several films can be shown per room on one day. 
In order to be able to determine which seats are available for a performance, each ticket purchase must be noted. 
Each ticket should show: cinema, hall, film title, date, starting time, 
serial number within the screening, row, seat, price.
Provision must be made for pricing: Each row of a hall has a standard price, but for certain 
performances the row prices can be set individually. For information purposes, the actors should 
be recorded with their personal data (surname, first name, nationality, date of birth, date of death, comments, ... ) 
and it should be possible to tell which actors have acted in which films.
The analogous statements should also be possible for directors, whereby it can be assumed that 
there is only one director for a film. However, it is possible that the director also plays a part in a film.
The other data of a film include: Title, type (thriller, western, youth film, ... ), 
year of production, country, language, duration, distribution, etc.

Create a ERD and a Relation Model for this example

 | cinema | hall | filmID | filmtitle | seating plan | seat | box | row | seatnumber | ticket
 |--------|------|------|--------------|------|-----|-----|------------|--------|---  
 | varchar | varchar | int  | varchar | int | int | int | int | int | int
 
 cinema(cinemaID:int, ) <br>
 film(filmID: int, filmtitle: varchar(32), ) <br>
 hall() <br>
 ticket(serialNumber:int, cinema:varchar(32), hall:int, filmtitle:varchar(32), filmDate:date, startingTime: time, raw:int, seatNumber:int, price: double ) <br>
 seat() <br>
 
 ### first solution:
 
![ERM own](20200213_114037.jpg)
 
 Added photo Groupwork:
 
![ERM group](groupERM.jpg)
 
 ### second solution:
 
 #### ERM:
 
 ![ERM own](cinemaERM_mario.jpg)
 
 #### textual notation:
 
* cinema ( **cinemaID**:INT, name:VARCHAR(32), address:VARCHAR(32), city:VARCHAR(32), postalcode:INT, numberofhalls:INT )

* hall ( **hallNR**:INT, *cinemaID*:INT, maxseats:INT, maxrows:INT  )

* seatingplan ( *cinemaID*:INT, *hallNR*:INT, rowNR:INT, seatNR:INT)

* row ( *cinemaID*:INT, *hallNR*:INT, **rowNR**:INT, isbox:BOOLEAN, standardprice:INT, specialprice:INT, maxseats:INT )

* screening schedule ( *cinemaID*:INT, *hallNR*:INT, date:DATE, startingtime:TIME, filmID:INT )

* film(filmID:INT, filmtitle:VARCHAR(32), *director*:INT, type:VARCHAR(32), yearofproduction:INT, country:VARCHAR(32), 
language:VARCHAR(32), duration:INT, distribution:VARCHAR(32)) 

* ticket(serialNumber:INT, cinemaID:INT, hallNR:INT, filmID:INT, date:DATE, startingtime:TIME, 
rowNR:INT, seatNR:INT, price:INT , isreserved:BOOLEAN, ispurchased:BOOLEAN)

* actor (**actorID**:INT, firstname:VARCHAR(32), lastname:VARCHAR(32), nationality:VARCHAR(32), date of birth:DATE, 
date of death:DATE, comments:VARCHAR(1000), isactor:BOOLEAN, isdirector:BOOLEAN) 

* filmcast( *filmID*:INT, *actorID*:INT )

       
 #### SQL DB Schema:
 
[SQL DB Schema](cinemaDB_Schema.pdf)