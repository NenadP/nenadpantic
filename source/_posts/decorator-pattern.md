---
title: Decorator Design Pattern
date: 2020-08-22 23:06:20
tags: 
  - design patterns
  - java
  - Gang of Four
---
A simple example of the decorator design pattern in Java.
This is very popular example (and very illustrative) of the Pizza Shop.

#### Create a Pizza Interface. 

We will create a concrete PlainPizza in a second, by implementing this interface.

{% codeblock lang:java %}
interface Pizza {

    String getDescription();

    double getPrice();
}
{% endcodeblock %}

#### Concrete PlainPizza class. 

We are giving some default values to our Plain Pizza which will be dressed with the toppings.

{% codeblock lang:java %}
class PlainPizza implements Pizza {

    public String getDescription() {
        return "Plain Pizza";
    }

    public double getPrice() {
        return 3.00;
    }
}
{% endcodeblock %}


#### Create a Topping abstract class. 

It implements Pizza as well, and HAS-A pizza; This will enable Toppings to be wrapped around each other.
This is our Decorator.

{% codeblock lang:java %}
abstract class Topping implements Pizza {

    protected Pizza pizza;

    Topping(Pizza pizza) {
        this.pizza = pizza;
    }

    abstract public String getDescription();

    abstract public double getPrice();
}
{% endcodeblock %}

#### Create a CheeseTopping class

Our first topping type. We are using pizza instance we defined in Decorator, and adding extra values.

{% codeblock lang:java %}
class CheeseTopping extends Topping {

    CheeseTopping(Pizza pizza) {
        super(pizza);
    }

    public String getDescription() {
        return pizza.getDescription() + 
        ", added Cheese";
    }

    public double getPrice() {
        return pizza.getPrice() + 0.50;
    }
}
{% endcodeblock %}


#### Create a PepperoniTopping class

Our second topping type. Obviously, we can add as many as we like.

{% codeblock lang:java %}
class PepperoniTopping extends Topping {

    PepperoniTopping(Pizza pizza) {
        super(pizza);
    }

    public String getDescription() {
        return pizza.getDescription() + 
        ", added Pepperoni";
    }

    public double getPrice() {
        return pizza.getPrice() + 0.30;
    }
}
{% endcodeblock %}


#### Create your client 

An actual user of your pizza Decorator. You can see how Decorators are wrapping Pizzas and other decorators.

{% codeblock lang:java %}
class Main {

    public static void main(String[] args) {

        Pizza pizza = new PepperoniTopping(new CheeseTopping(new PlainPizza()));
        
        System.out.println("Description: " + pizza.getDescription());
        System.out.println("Price: " + pizza.getPrice());
       }
}
{% endcodeblock %}


Run it on repl.it:
https://repl.it/@NenadP/Decorator-pattern-example#Main.java

UML Diagram for our Pizza Decorator pattern example:
{% asset_img decorator-puml.png Pizza example - Decorator Pattern UML diagram %}

Github example:
https://github.com/NenadP/super-simple-coding/tree/master/src/designpatterns/decorator

Wikipedia:
https://en.wikipedia.org/wiki/Decorator_pattern#cite_note-1

{% youtube Y2SE5THT9Xc %}