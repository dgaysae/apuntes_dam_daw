---
{"dg-publish":true,"permalink":"/1-dam-ed/unidad-05/anexos/","dg-note-properties":{"unidad":"[[Unidad 5 - Repositorios, documentación y refactorización]]","descripcion":"...","orden":6}}
---


Índice:
```table-of-contents
```

---


## Anexo i - Ejemplos de `.gitignore` en proyecto Maven

Este fichero .gitignore debe estar en la carpeta raíz del proyecto, donde está el fichero pom.xml. Se ha creado para trabajar con él desde Eclipse, Netbeans y VSCode.

```bash
# ==========================================
# GITIGNORE PARA PROYECTO MAVEN (DAM)
# Compatible con Eclipse y NetBeans
# ==========================================

### --- MAVEN ---
# Ignora la carpeta donde se guarda el código compilado y los .jar/.war
target/
pom.xml.tag
pom.xml.releaseBackup
pom.xml.versionsBackup
pom.xml.next
release.properties
dependency-reduced-pom.xml
buildNumber.properties
.mvn/timing.properties
# Evita subir el "wrapper" de maven si no es necesario
.mvn/wrapper/maven-wrapper.jar

### --- ECLIPSE ---
# Ficheros de metadatos y configuración del proyecto en Eclipse
.metadata/
.project
.classpath
.settings/
*.launch
bin/
.externalToolBuilders/

# Específico de plugins de Eclipse (como el de Maven)
.m2e/
.factorypath

### --- NETBEANS ---
# Carpeta donde NetBeans guarda la configuración local del usuario
nbproject/private/
nbbuild/
dist/
nbdist/
.nb-gradle/
# Si usas el sistema de compilación propio de NetBeans (no Maven)
build/

### --- VISUAL STUDIO CODE ---
# Configuraciones del espacio de trabajo
.vscode/
# Historial local de VS Code (evita basura innecesaria)
.history/
# Ficheros de extensiones y workspace
*.code-workspace
# Diccionario de usuario para el corrector
.vscode/spellright.dict

### --- SISTEMA OPERATIVO ---
# Ficheros temporales de Windows
Thumbs.db
Desktop.ini
$RECYCLE.BIN/

# Ficheros temporales de macOS
.DS_Store
.AppleDouble
.LSOverride

### --- LOGS Y TEMPORALES ---
*.log
temp/
tmp/
```




---

<p><span>⬅️ <strong>Anterior:</strong> <a data-tooltip-position="top" aria-label="1DAM_ED/Unidad 05/Referencias.md" data-href="1DAM_ED/Unidad 05/Referencias.md" href="1DAM_ED/Unidad 05/Referencias.md" class="internal-link" target="_blank" rel="noopener nofollow">Referencias</a> | 🏠 <strong>Unidad:</strong> <a data-tooltip-position="top" aria-label="1DAM_ED/Unidades/Unidad 5 - Repositorios, documentación y refactorización.md" data-href="1DAM_ED/Unidades/Unidad 5 - Repositorios, documentación y refactorización.md" href="1DAM_ED/Unidades/Unidad 5 - Repositorios, documentación y refactorización.md" class="internal-link" target="_blank" rel="noopener nofollow">Unidad 5 - Repositorios, documentación y refactorización</a></span></p>