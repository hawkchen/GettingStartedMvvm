# Declaring Domain Class

The domain class and application logic are not the main topic of this book, we just present them without detail explanation. Please refer to the source code on your own.

The following is the domain object that represents a car.

```java

public class Car {
    private Integer id;
    private String model;
    private String make;
    private String preview;
    private String description;
    private Integer price;
    //omit getter and setter for brevity
}
```

-   [The complete code](https://github.com/zkoss/zkbooks/blob/master/gettingStarted/getZkUp/src/main/java/tutorial/Car.java).

We then define a service class to perform the business logic (search
cars) shown below:

``` java
public interface CarService {

    /**
     * Retrieve all cars in the catalog.
     * @return all cars
     */
    public List<Car> findAll();

    /**
     * search cars according to keyword in  model and make.
     * @param keyword for search
     * @return list of car that match the keyword
     */
    public List<Car> search(String keyword);
}
```

In this example, we have defined a class - `CarServeImpl` that
implements the above interface. For simplicity, it uses a static list
object as the data model. You can rewrite it so that it connects to a
database in a real application. Implementation details are not in the
scope of this article, please refer to  [CarService.java](https://github.com/zkoss/zkbooks/blob/master/gettingStarted/getZkUp/src/main/java/tutorial/CarService.java)    [CarServiceImpl.java](https://github.com/zkoss/zkbooks/blob/master/gettingStarted/getZkUp/src/main/java/tutorial/CarServiceImpl.java).
