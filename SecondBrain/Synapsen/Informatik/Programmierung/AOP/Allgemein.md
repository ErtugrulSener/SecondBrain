## Problem
- Modularisierung von [[Cross-Cutting-Concerns]]
	- ohne Modularisierung hat man Business Code + Cross Cutting Concerns in einer Methode (*Code tangling* bzw. *Code Verwicklung*)
	- außerdem wiederholt man den Cross Cutting Concern über viele Module (*Code scattering* bzw. *Code Streuung*)

![[problems-with-cross-cutting-concerns.png]]

## Lösung
- Die Business-Logik fokussiert sich auf Business-Prozesse, die das Hauptproblem lösen
- Man implementiert [[Aspekte]] für die [[Cross-Cutting-Concerns]]
- Man webt die Aspekte in die Anwendung ([[Aspect Weaving]])

![[solution-to-cross-cutting-concerns.png]]