Javascript wird interpretiert durch die Javascript Engine. Standartmäßig kann man (anders als bei Java und der JVM) allerdings den Code nur in den modernen Browsern ausführen, da die Engine dort Built-In ist.

Um Javascript dennoch auf dem Desktop auszuführen benötigen wir [[NodeJS]].
Dann führen wir unseren Javascript Code folgendermaßen aus:

1) Wir haben eine Datei "javascript_code.js" mit dem folgenden Inhalt:

```shell
console.log("Hello World!");
```

2) Wir nutzen das CLI Tool "node" um den Code in der Datei auszuführen.

```shell
node javascript_code

oder

node javascript_code.js
```

3) (Optional) Die Datei muss nicht mit ".js" enden, dies ist aber der Dateityp für Javascript Dateien und somit Standart. Falls wir z.B: Code in einer "javascript_code.txt" ausführen wollen, müssen wir die Endung explizit angeben.

```shell
node javascript_code.txt
```

Falls die Datei nicht existiert gibt eine Fehlermeldung vom CLI Tool node:

```shell
node:internal/modules/cjs/loader:1042                                                    
  throw err;                                                                             
  ^                                                                                      
                                                                                         
Error: Cannot find module 'C:\Users\Lead\Desktop\hello_world'                            
    at Module._resolveFilename (node:internal/modules/cjs/loader:1039:15)                
    at Module._load (node:internal/modules/cjs/loader:885:27)                            
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:82:12)
                                                                                         
    at node:internal/main/run_main_module:23:47 {                                        
  code: 'MODULE_NOT_FOUND',                                                              
  requireStack: []                                                                       
}                                                                                        
                                                                                         
Node.js v19.3.0                                                                          
```