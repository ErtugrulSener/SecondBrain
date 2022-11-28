# Bei Maven Central hochladen
Wenn man endlich fertig ist mit Tests und dem Build, will man sein Modul als Build irgendwo veröffentlichen, damit andere davon profitieren. Das macht man folgendermaßen als Maven Projekt ("Pom Files werden generiert"):

```Groovy
plugins {
	id("java-library")
	id("maven-publish")
}

publishing {
	publications {
		create<MavenPublication>("library") {
			from(components["java"])
		}
	}

	repositories {
		maven {
			url = uri(layout.buildDirectory.dir("repo"))
		}
	}
}
```