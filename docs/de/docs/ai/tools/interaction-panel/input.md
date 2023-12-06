---
 title: "Eingabe" 
 Schnecke: "Eingang" 
 ausgeblendet: false 
---
# Eingabe

Der Input ist ein kurzfristiges JSON-Datenobjekt, das jedes Mal generiert wird, wenn eine Nachricht an Cognigy.AI gesendet wird. 

Das Eingabeobjekt enthält allgemeine Informationen über die Nachricht, z. B. die **Uhrzeit**, zu der die Nachricht empfangen wurde, und den **Kanal**
Von wo aus die Nachricht gesendet wurde.
Spezifischere Ergebnisse aus dem NLU-Intent-Mapping-Prozess sind ebenfalls verfügbar, z. B. die ausgewählte **Intent**,
die identifizierten **Slots** und viele andere nützliche Informationen.

Das Eingabeobjekt wird an den [Flow]({{config.site_url}}ai/resources/build/flows/) des Agenten übergeben, um über die nächste auszuführende Aktion zu entscheiden. Weitere Informationen zur Lebensdauer der Eingabe finden Sie auf der Seite [CognigyScript]({{config.site_url}}ai/tools/cognigy-script/).

!!! Hinweis "Intent Default Replies überschreiben die Flow-Logik"
    Wenn ein Intent mit einer Standardantwort konfiguriert ist, überschreibt diese die Flow-Logik des Agenten und wird automatisch als Antwort übermittelt.

<figure>
  <img class="image-center" src="{{config.site_url}}ai/tools/images/d2f39be-interaction-input.jpg" width="100%" />
  <figcaption>Untersuchen Sie das aktuelle Input-Objekt auf der Registerkarte INFO des Interaktionsfensters

</figcaption>
</figure>

## Eigenschaften<div class="divider"></div>[! [Versions-Abzeichen] (https://img.shields.io/badge/Updated in-v4.45-blue.svg)] (.. /.. /.. /release-notes/4.45.md)

Das Input-Objekt enthält die folgenden Eigenschaften (für die Texteingabe).

| Schlüssel | 	Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------  -----------------------------------------------------------------------|
| Text | Der Text der empfangenen Nachricht.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Absicht | Die erkannte Absicht kann NULL sein.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| intentScore | Die Bewertung der erkannten Absicht.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| intentFlow | Der Flow, der die erkannte Absicht enthält.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Spielautomaten | Enthält die erkannten Slots, die von automatischen bis hin zu benutzerdefinierten Lexikonbibliotheken reichen.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| NLU | Enthält die detaillierten NLU-Verarbeitungsergebnisse. Ausführliche Informationen finden Sie unter [NLU-Eigenschaften]({{config.site_url}}ai/tools/interaction-panel/input/#nlu-properties).                                                                                                                                                                                                                                                                                                                                                                                     |
| Modus | Die Art der Eingabe, die von Cognigy.AI empfangen wird. Kann entweder "TextOnly" oder "TextData" sein.                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Typ | Die Art des Eingabesatzes, der durch die NLU-Frage (Statement, Command, Greeting, BGreeting, whQuestion, howQuestion, ynQuestion, pAnswer, nAnswer) bestimmt wird, Gibt an, ob eine Frage als Eingabetext empfangen wurde und welche Art von Frage gestellt wurde.                                                                                                                                                                                                                                                                                                |
| intentOutOfState | Wenn ein Status aktiv ist, enthält diese Eigenschaft die erkannte Absicht, die durch den Status ausgeschlossen wurde.                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| currentTime | Der Zeitstempel, zu dem die Nachricht von Cognigy.AI empfangen wurde.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Bundesland | Der aktuelle Status innerhalb der Sitzung. Standardmäßig enthält es den Wert "default". Andere Zustände können definiert werden. Weitere Informationen finden Sie unter Status.                                                                                                                                                                                                                                                                                                                                                                                                   |
| Kanal | Der Kanal, von dem die Nachricht empfangen wurde, z. B. ein Facebook-Endpunkt, hat den Wert "facebook".<br>Für unsere allgemeineren Endpunkttypen wie "socket", "webhook" und "rest" kann dieser Wert definiert werden. Diese Eigenschaft ist auch in den OData-Datensätzen verfügbar, um die kanalbasierte Analysefilterung zu aktivieren.                                                                                                                                                                                                                             |
| endpointType | Die Art des Endpunkts, über den die Nachricht empfangen wurde, z. B. Alexa, Facebook, Dialogflow usw. Dieser Wert kann nicht geändert werden.                                                                                                                                                                                                                                                                                                                                                                                                             |
| Einstiegspunkt | Die Flow-Knoten-ID, die das Eingabeobjekt empfängt und verarbeitet.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| userId | Die ID des aktuellen Benutzers. Damit identifiziert Cognigy.AI jeden Nutzer als Verweis auf sein individuelles Kontaktprofil.<br>Weitere Informationen finden Sie unter Kontaktprofile.                                                                                                                                                                                                                                                                                                                                                                           |
| inputId | Eine eindeutige ID, die für jede von Cognigy.AI empfangene Nachricht generiert wird.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| sessionId | Die aktuelle Sitzungs-ID. Diese wird entweder von einem Kanal bereitgestellt oder von Cognigy.AI generiert. Die meisten Endpunkte ermöglichen das Definieren eines individuellen Sitzungsablaufs (TTL).                                                                                                                                                                                                                                                                                                                                                                                        |
| flowName | Der Name des aktiven Flows, der die Eingabedaten verarbeitet und über die nächste Aktion entscheidet.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| URLToken | Eine eindeutige ID, die zur Identifizierung des jeweiligen Endpunkts verwendet wird.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| completedGoals | Ein Objekt, das die Namen der Ziele enthält, die bei der Ausführung der Ablauflogik abgeschlossen wurden.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Ausführung | Die Anzahl der Nachrichten, die bisher in der aktuellen Sitzung empfangen wurden.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Daten | Das Datenobjekt, das als Payload an die Benutzereingabe gesendet wurde. Dieses Objekt kann eine "request"-Eigenschaft enthalten, die die ursprüngliche Anforderung aus dem externen Kanal speichert, z. B. Wenn ein Facebook-Endpunkt verwendet wird, enthält input.data.request den ursprünglichen HTTP-Anforderungsinhalt von Facebook.                                                                                                                                                                                                                                                  |
| verstanden | Ein boolesches Flag, das bestimmt, ob die NLU die Nachricht des Benutzers verstanden hat. Eine Eingabe gilt als verstanden, wenn ein Intent oder ein Slot gefunden wird. <br> Die Eingabe wird über den Code Node oder den Overwrite Analytics Node als verstanden markiert, oder der Satztyp ist pAnswer, nAnswer oder Greeting (wenn die Logik des Bestätigungsworts aktiviert ist). In allen anderen Fällen wird sie als nicht verstanden markiert, es sei denn, es gibt eine aktive Übergabe (ohne Aktivierung eines Agenten-Assist-Flows) oder eine Nachricht wurde explizit als "Nicht zählen" oder "Null" markiert. |
| Sprache | Die Sprache des Gebietsschemas, die zum Verarbeiten der Eingabenachricht verwendet wurde.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| traceId | Ein eindeutiger Bezeichner für die jeweilige Benutzereingabe.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| intentLevel | Die übereinstimmende Absicht pro [Absichtshierarchie]({{config.site_url}}ai/nlu/nlu-overview/intent-hierarchy/)-Ebene.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| localeId | Die eindeutige ID für das aktuelle Gebietsschema, das zum Verarbeiten der Eingabenachricht verwendet wird.                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| conditionalEntrypointWasExecuted | Eine boolesche Variable, die "true" anzeigt, wenn der Flow auf einem bedingten Knoten ausgeführt wurde.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| activeFrage | Optional: Informationen zur Frageausführung, wenn eine Frage aktiv ist.<br>Die folgenden Eigenschaften sind verfügbar:<br>nodeId: Die ID des Frageknotens.<br>Typ: Die Art der Frage<br>lastExecutedAt: Index der letzten Ausführung.<br>forgetQuestionThreshold: Konfigurierter Schwellenwert, um die Frage zu vergessen.<br>repromptCount: Anzahl der erneuten Eingabeaufforderungen.<br>escalationCount: Anzahl der Eskalationen.                                                                                                                                                               |

### NLU-Eigenschaften

Die detaillierten NLU-Ergebnisse werden in der Variablen **nlu** veröffentlicht, die die folgenden Eigenschaften enthält:

| Schlüssel | Beschreibung |
|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| intentMapperErgebnisse | Enthält spezifische Details zu den Ergebnissen der NLU-Absichtszuordnung, einschließlich einer Zusammenfassung der Absichtsbewertung für jede der trainierten Absichten, die sich in der untergeordneten Eigenschaft scores befinden. |
| intentFlow | Eine eindeutige ID, die dem Flow zugewiesen ist, der die ausgewählte Absicht enthält.                                                                                                                   |
| intentId | Eine eindeutige ID, die der Absicht zugewiesen ist, die von der NLU ausgewählt wurde.                                                                                                                   |
| detailedSlots | Enthält die erkannten Slots, die von automatischen bis hin zu benutzerdefinierten Lexikonbibliotheken reichen.                                                                                                    |
| Marke | Stellt ein Array bereit, das jedes Wort des Eingabesatzes als Zeichenfolgenelement enthält.                                                                                                  |

!!! Hinweis "NLU-Eigenschaften sind erst nach NLU verfügbar"
    Die folgenden Eigenschaften werden vom NLU-Konnektor berechnet.

Folglich werden sie **nach** der NLU veröffentlicht.

**Sie sind daher nicht in den Cognigy NLU-Regeln und -Bedingungen verfügbar.**

Eigenschaften, die von der NLU in die Eingabe geschrieben werden:
    
*Absicht
      * intentScore
      * NLU
      *Kunst
      * intentLevel
      * localeId
      *verstanden
      * conditionalEntrypointWasExecuted

## Zugriff auf das Eingabeobjekt<div class="divider"></div>Flow-Knoten können dynamisch über [Tokens]({{config.site_url}}ai/resources/manage/tokens/) oder [CognigyScript]({{config.site_url}}ai/tools/cognigy-script/) auf Eingabeeigenschaften zugreifen, d. h. '{{ " {{input.property}}" }}'. Das Cognigy Script, das für den Zugriff auf das Eingabeobjekt verwendet wird, folgt der Punktnotation 'property.child.child'.

**Beispiel**: '{{ " {{input.text}}" }}' würde die Textnachricht zurückgeben, die an den Flow gesendet wurde.

!!! Hinweis "JSON-Pfad aus dem Eingabeobjekt kopieren"
    Sie können den genauen JSON-Pfad kopieren, den Sie benötigen, um auf einen bestimmten Wert im Input-Objekt zu verweisen, indem Sie mit der rechten Maustaste darauf klicken und im Kontextmenü "JSON-Pfad kopieren" auswählen. 

## Mehr Informationen

- [Status]({{config.site_url}}ai/tools/interaction-panel/state/)