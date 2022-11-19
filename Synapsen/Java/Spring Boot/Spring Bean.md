# Spring Bean
Eine Bean in Spring ist eine Komponente, die von Spring im Application Context gemaneged wird.

Beispiel um eine Bean aus dem Kontekt zu bekommen:

```Java
package com.example.demo;

import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

@SpringBootApplication
public class DemoApplication {
  
    // Main driver method
    public static void main(String[] args)
    {
  
        // Annotation based spring context
        AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext();
        context.scan("com.example.demo");
        context.refresh();
  
        // Getting the Bean from the component class
        ComponentDemo componentDemo = context.getBean(ComponentDemo.class);
        componentDemo.demoFunction();
  
        // Closing the context
        // using close() method
        context.close();
    }
}
```