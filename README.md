Java Nested Code Style Demo
===========================

View `NormalStyle.java` and `NestedStyle.java`:

Normal Java Code:

```Java
MenuBar menuBar = new MenuBar();
Menu menu = new Menu("Menu");
MenuItem item = new MenuItem("change content");
item.setOnAction(new EventHandler<ActionEvent>() {
    public void handle(ActionEvent event) {
        label.setText("Changed!");
    }
});
menu.getItems().add(item);
menuBar.getMenus().add(menu);
return menuBar;
```

No level, hard to see the relations of the objects.

Use Java's instance initialization code block feature:

```Java
class X {
    public void doSomething() {}
}

new X() {
    {
        this.doSomething();
    }
}
```

Put the `{`s together:

```Java
new X() {{
    this.doSomething();
}}
```

We can refactor the example to:

```Java
new MenuBar() {{
    getMenus().add(new Menu("Menu") {{
        getItems().add(new MenuItem("change content") {{
            this.setOnAction(new EventHandler<ActionEvent>() {
                public void handle(ActionEvent event) {
                    label.setText("Changed!");
                }
            });
        }});
    }});
}};
```

With IDEA's good format support for `{{`, it looks like some kind of DSL, much better than before.
