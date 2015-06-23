# Abstracting the View

ViewModel is an abstraction of View. Therefore when we design a
ViewModel, we should analysis UI's functions for what **state** it
contains and what **behavior** it has.

The state:

1.  keyword from user input
2.  car list of search result
3.  selected car

The behavior:

1.  search

According to above analysis, the ViewModel should have 3 variables for
above states and one method for the behavior. In ZK, creating a
ViewModel is just like creating a POJO, and it exposes its states like
JavaBean's properties through setter and getter methods. The search
method implements search logic with service class and updates the
property "carList".

**SearchViewModel.java**

```java
package tutorial;

import java.util.List;
import org.zkoss.bind.annotation.*;

public class SearchViewModel {

    private String keyword;
    private List<Car> carList;
    private Car selectedCar;

    //omit getter and setter

    public void search(){
        carList = carService.search(keyword);
    }
}
```

## Annotation

In ZK MVVM, any behavior which can be requested by a View is implemented by a
method in a ViewModel. We can bind a component's event to such
method and ZK will invoke the method when bound event is triggered. In
order to let ZK know which method (behavior) can be requested, you
should apply an annotation `@Command` on a method. Hence we also call such method a **command method**.

Here we apply `@Command` on `search()` with **default command name**, `search`, which is the same as
method name. The command name is used in a data binding expression we'll
talk about in next section.

In `search()`, we change a ViewModel's property: `carList`. Thus, we
should tell ZK this change with `@NotifyChange` so that ZK can reload
the changed list for us after it invokes this method.

For "search" command, it looks like:

**SearchViewModel.java**

``` java
package tutorial;

import java.util.List;
import org.zkoss.bind.annotation.*;

public class SearchViewModel {

    //omit other codes

    @Command
    @NotifyChange("carList")
    public void search(){
        carList = carService.search(keyword);
    }
}
```

For complete source code, please refer to  [SearchViewModel.java](https://github.com/zkoss/zkbooks/blob/master/gettingStarted/getZkUp/src/main/java/tutorial/SearchViewModel.java).

