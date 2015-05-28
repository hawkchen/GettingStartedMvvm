# Implementing View Details Functionality

The steps to implement the view details functionality are similar to
previous sections.

1.  We bind attribute `selectedItem` of *listbox* to the property
    `vm.selectedCar` to save selected domain object.
2.  Because we want to show selected car's details, we bind value of
    *label* and src of *image* to selected car's properties which can be
    access by chaining dot notation like `vm.selectedCar.price`.
3.  Each time a user selects a *listitem*, ZK saves selected car to the
    ViewModel. Then ZK reloads `selectedCar`'s properties to those bound
    attributes.

```xml
        <listbox height="160px" model="@bind(vm.carList)" emptyMessage="No car found in the result"
        selectedItem="@bind(vm.selectedCar)">
        <!-- omit child components -->
        </listbox>
        <hbox style="margin-top:20px">
            <image width="250px" src="@bind(vm.selectedCar.preview)" />
            <vbox>
                <label value="@bind(vm.selectedCar.model)" />
                <label value="@bind(vm.selectedCar.make)" />
                <label value="@bind(vm.selectedCar.price)" />
                <label value="@bind(vm.selectedCar.description)" />
            </vbox>
        </hbox>
```

You can view complete zul in References. [^11]
