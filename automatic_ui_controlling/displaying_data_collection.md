# Displaying Data Collection

The way to display a collection of data with data binding is very
similar to the way in MVC approach. we will use a special tag,
` <template> `[^1], to control the rendering of each item. The only
difference is we should use data binding expression instead of EL.

Steps to use ` <template> `:

1.  Use **`<template>`** to enclose components that we want to create
    iteratively.
2.  Set template's "name" attribute to "model". [^2]
3.  Use implicit variable, **each**, to assign domain object's
    properties to component's attributes.

**Extracted from searchMvvm.zul**

```xml

        <listbox height="160px" model="@bind(vm.carList)" emptyMessage="No car found in the result">
            <listhead>
                <listheader label="Model" />
                <listheader label="Make" />
                <listheader label="Price" width="20%"/>
            </listhead>
            <template name="model">
                <listitem>
                    <listcell label="@bind(each.model)"></listcell>
                    <listcell label="@bind(each.make)"></listcell>
                    <listcell>$<label value="@bind(each.price)" />
                    </listcell>
                </listitem>
            </template>
        </listbox>
```


[^1]: [ZK Developer's Reference/MVC/View/Template](http://books.zkoss.org/wiki/ZK%20Developer's%20Reference/MVC/View/Template)

[^2]: [ZK Developer's Reference/MVC/View/Template/Listbox Template](http://books.zkoss.org/wiki/ZK%20Developer's%20Reference/MVC/View/Template/Listbox%20Template)
