# Wiki de sistemas de RubyCraft (1.7.10)

> Esta wiki resume los sistemas principales del mod y señala las clases clave donde se implementan.

## 1) Núcleo y registro general
- El punto de entrada del mod declara y organiza la mayor parte de bloques, ítems y sistemas que se inicializan en el arranque de RubyCraft. Está en `RubyCraft.java`, que importa los registros de bloques, ítems, máquinas, eventos y generación del mundo para su uso global.【F:src/main/java/RubyCraft/RubyCraft.java†L1-L200】
- Hay un control de versión interno con “flags” para activar modos especiales (desarrollador, versión trol, eventos estacionales). Esta lógica vive en `Control_de_Version` y se ejecuta al iniciar el mod.【F:src/main/java/RubyCraft/Control_de_Version.java†L1-L26】
- El mod define un “Creative Tab” propio con barra de búsqueda, y usa la mesa de Ruby como icono del tab. Esto se implementa en `TabdeCreativoAvanzada`.【F:src/main/java/RubyCraft/TabdeCreativoAvanzada.java†L1-L29】

## 2) Generación de mundo y estructuras
- La clase `Generacion_Principal` registra los generadores de worldgen: minerales (Ruby, Zafiro, materiales preciosos), generación de piedra, magma, árboles y estructuras personalizadas. Este es el núcleo del sistema de generación de mundo del mod.【F:src/main/java/RubyCraft/Generacion/Generacion_Principal.java†L1-L19】
- El sistema también añade botín a cofres vanilla (bonus chest, dungeon y pirámide) mediante `Loot_Cofres`. Esto inyecta objetos del mod en cofres del juego base.【F:src/main/java/RubyCraft/Generacion/Loot_Cofres.java†L1-L18】

## 3) Biomas y tipo de mundo
- RubyCraft registra un bioma propio llamado “Ruby”, asignándolo a la categoría PLAINS y habilitando su spawn en el mundo. La definición está en `Registrar_Biomas`.【F:src/main/java/RubyCraft/Biomas/Registrar_Biomas.java†L1-L31】
- También existe un tipo de mundo específico (`WorldTypeRuby`) que genera su capa de biomas usando `RubyGenLayerBiome` y mezcla con `GenLayerZoom` y `GenLayerBiomeEdge`.【F:src/main/java/RubyCraft/Biomas/WorldTypeRuby.java†L1-L23】

## 4) Crafteos y mesas especiales
- RubyCraft tiene un sistema de recetas extendidas que soporta mesas propias: Mesa de Ruby, Mesa de Zafiro y un Transformador de Losas a Bloques. La API de registros para estas mesas está en `Registros` y se usa para recetas “shaped” y “shapeless”.【F:src/main/java/RubyCraft/Registrar/Registros_Importantes/Registros.java†L1-L58】
- La Mesa de Ruby posee su propio gestor de recetas, que además incorpora las recetas vanilla al iniciar. Esto se implementa en `MesarubyManager`.【F:src/main/java/RubyCraft/Manager/MesarubyManager.java†L1-L34】
- El archivo `Crafteos` define los crafteos principales del mod: recetas en mesa vanilla, recetas con métodos auxiliares, recetas de mesas personalizadas y hornos (smelting).【F:src/main/java/RubyCraft/Registrar/Crafteos.java†L1-L200】

## 5) Máquinas y GUI
- RubyCraft tiene varias mesas y máquinas con interfaces propias: Mesa de Ruby, Mesa de Zafiro, Transformador de Losas, y mesas de trabajo por tipo de madera, además de GUI de eventos. `GuiHandler` coordina qué contenedor/GUI se abre según el ID y el bloque en el mundo.【F:src/main/java/RubyCraft/Gui/GuiHandler.java†L1-L200】

## 6) Eventos y lógica de gameplay
- El mod registra eventos de juego para logros, crafteos, minería, totém, revoluciones de mobs y manejo de teclas del cliente. La lista de eventos vive en `Eventos_Principal`.【F:src/main/java/RubyCraft/Eventos/Eventos_Principal.java†L1-L51】
- Además existe un sistema de teclas que registra bindings (por ejemplo, la tecla para ver updates) en `Teclas_Principal`.【F:src/main/java/RubyCraft/Teclas/Teclas_Principal.java†L1-L24】

## 7) Entidades y mobs
- RubyCraft registra entidades normales y sin huevo de spawn, además de granadas del mod (Ruby, Zafiro, Uranio) y entidades de eventos estacionales. La lógica de registro se encuentra en `Entidades_Principal`.【F:src/main/java/RubyCraft/Entidades/Entidades_Principal.java†L1-L83】

## 8) Combustibles personalizados
- Se define un sistema de combustibles que registra manejadores de combustible personalizados (maderas, magma, uranio) y bloquea el uso como combustible de ciertas mesas. Esto se hace en `Combustible_Principal`.【F:src/main/java/RubyCraft/Combustible_Iniciar/Combustible_Principal.java†L1-L23】

## 9) Actualizaciones y notificaciones
- RubyCraft incluye un sistema para verificar versiones nuevas desde una URL (Dropbox) o un backend MySQL, actualizando mensajes, changelog y flags internos. La lógica principal está en `Buscar_Actualizaciones`.【F:src/main/java/RubyCraft/Actualizaciones/Buscar_Actualizaciones.java†L1-L102】

## 10) Integraciones y drops especiales
- Hay un manejador de drops de mobs para integraciones específicas, por ejemplo el drop de un objeto al derrotar a `AlejandroMob`. Esto se gestiona en `DropeoMobsIntegracionHandler`.【F:src/main/java/RubyCraft/Integracion/DropeoMobsIntegracionHandler.java†L1-L37】

---

Si necesitas ampliar la wiki con detalles de un sistema concreto (por ejemplo, recetas de una mesa específica, mobs o estructuras concretas), dime cuál y preparo una sección extendida.
