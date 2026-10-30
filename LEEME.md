# rodagentic-site-anchors

Anclajes en Bitcoin de lo que publica https://rodagentic.com. *English below.*

## Qué contiene

Un archivo por despliegue del sitio, en `deploys/`, con su prueba de [OpenTimestamps](https://opentimestamps.org/) (`.ots`) al lado. Cada archivo lleva solo:

- la fecha y hora UTC del despliegue;
- el commit de `main` del repositorio del sitio que se desplegó;
- el SHA-256 de cada archivo servido, una línea por archivo, en formato `sha256sum`.

Sirve para una cosa: que cualquiera pueda comprobar que una página que descarga de rodagentic.com es la que se publicó y ancló, y que un cambio hecho sin pasar por un despliegue anclado quede a la vista.

**Todavía no hay anclajes.** Cuando los haya, las instrucciones para comprobarlos estarán en https://rodagentic.com/verification/.

## Qué no contiene

- El contenido de las páginas: está en el propio sitio.
- Nada del experimento del laboratorio: eso se ancla en otro repositorio, https://github.com/MontanaMiramar/rall-attestations.

## La protección de la rama

- La rama `main` tiene activas dos reglas: no se puede borrar ni reescribir su historial (force push). Las reglas activas, a qué ramas se aplican y cuándo se crearon o cambiaron por última vez se pueden consultar desde fuera, sin credenciales: https://api.github.com/repos/MontanaMiramar/rodagentic-site-anchors/rules/branches/main y https://api.github.com/repos/MontanaMiramar/rodagentic-site-anchors/rulesets
- **Lo que no se puede comprobar desde fuera:** quién puede saltarse esas reglas, y que el propietario del repositorio no las desactive. La integridad de lo anclado no descansa en GitHub sino en las pruebas `.ots`: un archivo alterado no coincidiría con su sello.
- Las reglas cubren solo `main`. **Solo cuenta lo que está en `main`.**

## Historial de pruebas

El 2026-10-30, antes del primer anclaje:

- El commit `df904643b82277fac331ee55dc49e3e2e86853b5` añadió un archivo de prueba de escritura, `prueba-escritura.txt`. Se retiró del árbol en el commit que añade este archivo; borrarlo no lo borra del historial.
- Se intentó un force push sobre `main` para comprobar la regla, y GitHub lo rechazó.
- Para comprobar a qué ramas se aplican las reglas, se creó una rama `prueba-rama`, se hizo un force push en ella (que GitHub aceptó, porque las reglas no la cubren) y se borró.

---

# rodagentic-site-anchors (English)

Bitcoin anchors of what https://rodagentic.com publishes.

**What it contains:** one file per site deployment, in `deploys/`, with its OpenTimestamps proof (`.ots`). Each file holds only the UTC date and time of the deployment, the `main` commit of the site repository that was deployed, and the SHA-256 of every served file, one per line in `sha256sum` format. Its purpose: anyone can check that a page they download from rodagentic.com is the one that was published and anchored, and a change made outside an anchored deployment shows. **There are no anchors yet.** When there are, instructions to check them will be at https://rodagentic.com/verification/.

**What it does not contain:** the content of the pages (that is on the site itself), or anything from the lab's experiment (anchored separately in https://github.com/MontanaMiramar/rall-attestations).

**Branch protection:** `main` has two active rules: it cannot be deleted and its history cannot be rewritten (force push). The active rules, which branches they cover, and when they were created or last changed can be checked from outside, without credentials, at the two API addresses above. **What cannot be checked from outside:** who may bypass those rules, and that the owner does not switch them off. The integrity of the anchors rests on the `.ots` proofs, not on GitHub. The rules cover only `main`: **only what is on `main` counts.**

**Test history (2026-10-30, before the first anchor):** commit `df904643b82277fac331ee55dc49e3e2e86853b5` added a write-test file, `prueba-escritura.txt`, removed from the tree in the commit that adds this file (removing it does not remove it from history). A force push to `main` was attempted to check the rule, and GitHub rejected it. To check which branches the rules cover, a branch `prueba-rama` was created, force-pushed (GitHub accepted it, since the rules do not cover it) and deleted.
