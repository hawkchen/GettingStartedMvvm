# Automatic UI Controlling

The approach we introduce here to control user interaction is to **let
ZK control UI components for you**. This approach is classified to
**Model-View-ViewModel** (**MVVM**) design pattern. [^2] This pattern
divides an application into three parts.

The **Model** consists of application data and business rules.
`CarService` and other classes used by it represent this part in our
example application.

The **View** means user interface. The zul page which contains ZK
components represents this part. A user's interaction with components
triggers events to be sent to controllers.

The **ViewModel** is responsible for exposing data from the Model to the
View and providing required action requested from the View. The
ViewModel is type of **View abstraction** which contains a View's state
and behavior. But **ViewModel should contain no reference to UI
components**. ZK framework handles communication and state
synchronization between View and ViewModel.

Under this approach, we just **prepare a ViewModel class** with proper
setter, getter and application logic methods, then **assign data binding
expression to a component's attributes** in a ZUL. There is a binder in
ZK which will synchronize data between ViewModel and components and
handle events automatically according to binding expressions. We don't
need to control components by ourselves.

Here we use search function to explain how MVVM works in ZK. Assume that
a user click "Search" button then *listbox* updates its content. The
flow is as follows:

![ center](../images/tutorial-mvvm.png  " center")

1.  A user clicks "Search" button and a corresponding event is sent.
2.  ZK's binder invokes the corresponding command method in the
    ViewModel.
3.  The method accesses data from Model and updates some ViewModel's
    properties.
4.  ZK's binder reloads changed properties from the ViewModel to update
    component's states.
