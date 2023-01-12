Caching ist nicht mehr so einfach wie bei REST, man muss womöglich selbst etwas entwickeln. Wieder könnte man Direktiven wie "@cacheControl(maxAge: 500)" einführen.

## Lösung: ApolloEngine
ApolloEngine ist wie ein Proxy zwischen Client und Server, das ihm viele zusätzliche Features gibt. z.B: eben genau die Direktive "@cacheControl".

## Alternative Lösung: Schema Stitching
Das ist wenn ein "Mega"-Schema existiert, das mit anderen API's (Schemas dahinter) kommuniziert.