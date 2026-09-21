# Dies ist die Readme für die Extensions

## has-changes-hook

Es wird ein Hook hinzugefügt, welches als erstes abgesetzt wird, sogar vor dem
anhalten des containers. Dieser Hook ermöglicht es zu prüfen ob ein Backup
notwendig ist.

Idee ist es, dass es nur lesend feststellt ob mit dem backup fortgesetzt werden
soll. Anhand des Exitcodes wird entschieden, alles okay ist, ein skip erfolgt
oder ein fehler eingetreten ist.

| ErrorCodes   | Beschreibung                                                                                                     |
| ------------ | ---------------------------------------------------------------------------------------------------------------- |
| 0            | Check ok, Backup soll laufen (unverändertes Verhalten, abwärtskompatibel)                                        |
| 75           | Skip, kein Backup nötig – als "übersprungen" loggen, KEINE Fehlerbenachrichtigung                                |
| alles andere | echter Fehler (Skript abgestürzt, Tool nicht gefunden etc.) – wie bisher als fehlgeschlagen behandeln und melden |
