# Binding UI to ViewModel

Under MVVM, we build our UI as same as we do in the MVC approach,
then we specify relationship between a ZUL and a ViewModel by writing
data binding expression in component's attribute, and let ZK handle
components for us.

To bind a component to a ViewModel, we should set the component's **viewModel** attribute with
following syntax:

**`@id('ID') @init('FULL.QUALIFIED.CLASSNAME')`**

-   ` @id() ` is used to set ViewModel's id to whatever we want like a
    variable name. We will use this id to reference ViewModel's
    properties (e.g. vm.carList) in a data binding expression.
-   We should provide full-qualified class name for `@init()` to
    initialize the ViewModel object.

**Extracted from searchMvvm.zul**

```xml
    <window title="Search" width="600px" border="normal"
     viewModel="@id('vm') @init('tutorial.SearchViewModel')">
    <!-- omit other tags-->
    </window>
```


After binding the ViewModel to the component, all its child components
can access the same ViewModel and its properties. ZK also implicitly applies a composer called
`org.zkoss.bind.BindComposer`. This composer processes data binding
expressions and initializes the ViewModel class.

We can bind View to both ViewModel's properties and methods with data
binding expression. Let's see how to use data binding to achieve search
function.

Since we have declared variables in ViewModel class for component's
states in previous section, we can bind component's attributes to them.
After binding a component's attribute to ViewModel, ZK will synchronize
data between attribute's value and a ViewModel's property for us
automatically. We can specify **which attribute is bound to which
property** by writing data binding expression as a component attribute's
value with syntax:

**`@bind(vm.aProperty) `**

-   Remember that `vm` is the id we have given it in ` @id()` previously
    and now we use it to reference ViewModel object.

There are 2 states which relate to search function to be stored in the
ViewModel upon previous analysis. First, we want to store value of
*textbox* in ViewModel's `keyword`. We can then bind "value" of
*textbox* to `vm.keyword` with `@bind(vm.keyword)`. Second, we want to
store the data model of a *listbox* in ViewModel's `carList`, so we
should bind *listbox*'s "model" to `vm.carList`.

**Extracted from searchMvvm.zul**

```xml

        <hbox>
            Keyword:
            <textbox value="@bind(vm.keyword)" />
            <button label="Search" image="/img/search.png"/>
        </hbox>
        <listbox height="160px" model="@bind(vm.carList)" emptyMessage="No car found in the result">
        <!-- omit other tags -->
```

We can only bind a component's event attribute (e.g. onClick) to
a ViewModel's method. After we bind an event to a ViewModel, each time a
user triggers the event, ZK finds the bound command method and invokes
it. In order to handle clicking on "Search" button, we have to bind
button's onClick attribute to a command method with following syntax:

**` @command('COMMAND_NAME')`**

-   We should look for command name specified in our ViewModel's command
    method.

**Extracted from searchMvvm.zul**

```xml
        <hbox>
            Keyword:
            <textbox value="@bind(vm.keyword)" />
            <button label="Search" image="/img/search.png" onClick="@command('search')" />
        </hbox>
        <listbox height="160px" model="@bind(vm.carList)" emptyMessage="No car found in the result">
        <!-- omit other tags -->
```

After binding this "onClick" event, when a user clicks "Search" button,
ZK will invoke `search() ` and reload the property "carList" which is
specified in `@NotifyChange`.
