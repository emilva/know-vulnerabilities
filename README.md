# know-vulnerabilities
Idea: open source vulnerability database that is close to the developers.

## first version:
github repository based
 - folder: `known-vulnerabilities/`
 - contains a file per pacakge manager describing project and vulnerabilities
 - for mono-repos: one sub-folder for each sub project etc, same structure

## goals:
* self serve: developers themselves create and update their known-vulnerabilities.
* anybody could crawl repos to get up to date vulnerability information. 
* developers "claim" their packages by creating the known-vulnerabilities folder and updating the list of known vulnerabilities as they go
* open source database could be created based on this information. 


## Examples:

### single repo with one or more package manager (<package-manager>.json)
```
known-vulnerabilities/npm.json
known-vulnerabilities/composer.json
known-vulnerabilities/gradle.json
```
### single repo with sub modules:

```
known-vulnerabilities/api/gradle.json
known-vulnerabilities/frontend/npm.json
```

`<package-manager>.json` consists of project info from package manager + list of vulnerabilities

package identifier will follow https://github.com/package-url/purl-spec

example data:
```
{
  "vulnerabilities": [
    {
      "vulnerable-package": "maven:org.apache.xmlgraphics/batik-anim@1.9.1",
      "description": "Deserialization of Untrusted Data",
      "vulnerable-path": [
        "maven:org.apache.xmlgraphics/batik-anim@1.9.1",
        "maven:uk.org.lidalia/lidalia-slf4j-ext@1.0.0-jdk6",
        "maven:com.google.guava/guava@18.0"
      ],
      "affected-versions": [
      	"1.9.1",
      	"1.9.2",
      	"1.9.3",
      	"1.9.4",  // could also write 1.9.x for all
      	"2.4.4",      	      	
      	"2.4.5"
      ],
      "fix-versions": [
      	"1.9.6",
      	"2.4.6"
      ],
      "upgrade-paths": [
      	"1.9.x": "1.9.6",
      	"2.4.x": "2.4.6"
      ]
      "mitigations": "",
      "references": [
        "https://links-to-issue",
        "https://links-to-anything-informational"
      ],      
    }
  ]
}
```
