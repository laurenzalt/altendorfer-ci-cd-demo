
# Branching-Strategie

Dieses Dokument beschreibt die Branching-Strategie, die im Projekt verwendet wird. Wir orientieren uns an einer GitFlow-ähnlichen Struktur, um stabile Produktionszweige und eine klare Feature-Entwicklung zu gewährleisten.

## Branch-Typen

- **main (oder master):**  
  Enthält den stabilen, produktionsbereiten Code. Jeder Commit in diesem Branch ist vollständig getestet und einsatzbereit.

- **develop:**  
  Dieser Branch dient als Integrationszweig, in den alle neuen Features und Bugfixes gemerged werden, bevor ein Release vorbereitet wird.

- **feature/xxx:**  
  Für neue Features wird jeweils ein separater Branch vom develop-Branch abgezweigt, z. B. `feature/user-authentication`.

- **release/xxx:**  
  Sobald ein Satz von Features fertiggestellt und in develop integriert wurde, wird ein Release-Branch erstellt, um den finalen Release-Prozess vorzubereiten.

- **hotfix/xxx:**  
  Dringende Bugfixes, die direkt in der Produktion (main) benötigt werden, werden in einem Hotfix-Branch erstellt und anschließend in main und develop gemerged.

## Arbeitsablauf

1. **Feature-Entwicklung:**  
   - Ein neuer Feature-Branch wird vom develop-Branch abgezweigt.
   - Nach Fertigstellung und erfolgreichem Testen wird ein Pull Request (PR) gegen develop erstellt.
   - Nach Code-Review und Integration wird der Feature-Branch gelöscht.

2. **Release-Vorbereitung:**  
   - Ein Release-Branch wird von develop erstellt, wenn genügend neue Features integriert sind.
   - Dieser Branch wird für letzte Bugfixes und Tests verwendet.
   - Nach erfolgreichem Testing wird der Release-Branch in main (für den Release) und zurück in develop gemerged.

3. **Hotfix:**  
   - Ein Hotfix-Branch wird direkt vom main-Branch abgezweigt.
   - Nach der Korrektur wird der Hotfix in main und develop gemerged.

## Entscheidungsgrundlagen

Die Wahl dieser Strategie basiert auf dem Bedarf,:
- Einen stabilen Produktionszweig (main) zu haben.
- Parallele Feature-Entwicklungen und Testphasen im develop-Branch zu ermöglichen.
- Schnelle Bugfixes durch isolierte Hotfix-Branches zu ermöglichen.

## Tools und Regeln

- GitHub Pull Requests und Branch Protection Rules sorgen für einen strukturierten Merge-Prozess.
- Code-Reviews und automatisierte Tests sind verpflichtend, bevor Branches gemerged werden.
