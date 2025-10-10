## Nutzen von @Nonnull aus dem dev.hilla Package
Durch das Nutzen von @Nonnull im Header von Endpoint Methoden erreichen wir, das auch bei den generierten Typescript Methoden keine Warnings geschmissen werden. Dies ist bei Typescript wohl der Fall, genaueres weiß ich bisher nicht darüber.

```Java
public @Nonnull List<@Nonnull GroceryItem> findAll() {  
    return groceryRepository.findAll();  
}
```