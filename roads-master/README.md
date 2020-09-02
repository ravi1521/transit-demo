## Find if a path exists between two cities
#### This application determines if two cities are connected. 

Two points are considered connected if there’s a series of roads that can be traveled from one city to another.

Demo list of roads is available in a project file `cities.txt` located in the `resource` directory. 
File contains a list of city pairs (one pair per line, comma separated), which indicates that there’s a road between those cities.

In the example below 
* city `Albany` has exactly 2 roads connecting cities `Boston` and `Detroit`. 
* cities `Edison` or `Frisco` are not reachable from any of `Albany`, `Boston`, `Cincinatti` or `Detroit`
* `Albany` is connected to `Cincinatti` via `Detroit`
*  `Frisco` is connected to `Kansas` via `Edison` via `Laval`
```
Albany,Boston
Albany,Detroit
Boston,Cincinatti
Detroit,Albany
Edison,Frisco
Albany,Albany
Kansas,Laval
Laval,Edison
```

### Build from source
```bash
    mvn clean install
```
### Run the application

Using maven Spring Boot plugin 
``` 
    mvn spring-boot:run 
```
Using Java command line 
```
    java -jar target/transit-0.0.1.jar
```

### Show the city list and the satellite cities 

[http://localhost:8080/](http://localhost:8080/) 


### Check with it

Example `Albany` and `Edison` _are not_ connected:

[http://localhost:8080/connected?origin=Albany&destination=Edison](http://localhost:8080/connected?origin=Albany&destination=Edison) (result **no**)

Example `Frisco` and `Kansas` _are_ connected:

[http://localhost:8080/connected?origin=Frisco&destination=Kansas](http://localhost:8080/connected?origin=Frisco&destination=Kansas) (result **yes**)

 
Example `Detroit` and `Kansas` _are not_ connected

[http://localhost:8080/connected?origin=Detroit&destination=Kansas](http://localhost:8080/connected?origin=Detroit&destination=Kansas) (result **no**)

### Provide your own roadmap file

Using maven Spring Boot plugin 
``` 
    mvn spring-boot:run -Ddata.file=/tmp/mytest.txt 
```
Using Java command line 
```
    java -Ddata.file=/tmp/mytest.txt -jar target/transit-0.0.1.jar
   
```
### Swagger

[http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)
   

