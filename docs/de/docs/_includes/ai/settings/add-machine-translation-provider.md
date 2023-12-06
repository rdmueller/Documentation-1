1. Öffnen Sie die Cognigy.AI-Schnittstelle.
2. Wählen Sie im Menü auf der linken Seite einen Agenten aus.
3. Wählen Sie im Menü "Agent" auf der linken Seite die Option "> Einstellungen verwalten" aus.
4. Wählen Sie im Abschnitt **Übersetzungseinstellungen** einen der folgenden Anbieter aus:

=== "Microsoft Übersetzer"
        - **API-Schlüssel des Übersetzungsanbieters**: Geben Sie Ihren eindeutigen API-Schlüssel ein, der von Microsoft Translator bereitgestellt wird. Es ist für die Authentifizierung erforderlich und ermöglicht Ihnen den Zugriff auf Übersetzungsdienste.
        - **Request Retriers** — Geben Sie an, wie oft Cognigy versuchen soll, den Übersetzungsanbieter anzurufen, wenn während der ersten Anfrage ein Fehler auftritt. Wenn Sie es beispielsweise auf "3" setzen, versucht es Cognigy dreimal, bevor eine Übersetzungsanfrage aufgegeben wird.
        - **Request Timeout** — legen Sie fest, wie lange Cognigy auf eine Antwort des Übersetzungsanbieters warten soll, nachdem Sie eine Anfrage gestellt haben, gemessen in Millisekunden. Wenn der Anbieter nicht innerhalb dieses Zeitrahmens antwortet, wird dies als Zeitüberschreitung betrachtet.
        - **Sentence Cache Expiry Timeout** — legt fest, wie lange Übersetzungen im Cache aufbewahrt werden sollen, bevor sie als veraltet gelten und entfernt werden. Der Standardwert ist "84.600" Sekunden, was 1 Tag entspricht. Sie können ihn auf "0" setzen, wenn kein Caching möglich ist.
        - **Benutzerdefinierte API-Basis-URL** – diese Einstellung ist optional. Wenn Sie bestimmte Anforderungen haben oder eine Verbindung mit einer benutzerdefinierten Instanz der Microsoft Translator-API herstellen müssen, die sich von der Standardinstanz "https://api.cognitive.microsofttranslator.com/" unterscheidet, können Sie dieses Feld verwenden, um eine benutzerdefinierte Basis-URL anzugeben. Es ermöglicht Ihnen, die URL einschließlich des Protokollschemas zu definieren, z. B. "https://api-eur.cognitive.microsofttranslator.com", um die API-Verbindung an Ihre Bedürfnisse anzupassen.
        - **Benutzerdefinierte Abonnementregion** – diese Einstellung ist optional. Er stellt den Standort oder die Region Ihrer Azure MS Translator-Ressource dar. Möglicherweise müssen Sie dieses Feld verwenden, wenn Sie diese API aufrufen, insbesondere wenn Sie in Ihrem Azure-Konto eine bestimmte Region angegeben haben.

=== "Google Cloud-Übersetzung"
        - **API-Schlüssel des Übersetzungsanbieters**: Geben Sie Ihren eindeutigen API-Schlüssel ein, den Sie von Google Cloud Translation erhalten haben. Es ist für die Authentifizierung erforderlich und ermöglicht Ihnen den Zugriff auf Übersetzungsdienste.
        - **Request Retriers** — Geben Sie an, wie oft Cognigy versuchen soll, den Übersetzungsanbieter anzurufen, wenn während der ersten Anfrage ein Fehler auftritt. Wenn Sie es beispielsweise auf "3" setzen, versucht es Cognigy dreimal, bevor eine Übersetzungsanfrage aufgegeben wird.
        - **Request Timeout** — legen Sie fest, wie lange Cognigy auf eine Antwort des Übersetzungsanbieters warten soll, nachdem Sie eine Anfrage gestellt haben, gemessen in Millisekunden. Wenn der Anbieter nicht innerhalb dieses Zeitrahmens antwortet, wird dies als Zeitüberschreitung betrachtet.
        - **Sentence Cache Expiry Timeout** — legt fest, wie lange Übersetzungen im Cache aufbewahrt werden sollen, bevor sie als veraltet gelten und entfernt werden. Der Standardwert ist "84.600" Sekunden, was 1 Tag entspricht. Sie können ihn auf "0" setzen, wenn kein Caching möglich ist.

=== "DeepL Translate Pro"
        - **API-Schlüssel des Übersetzungsanbieters** — Geben Sie Ihren eindeutigen API-Schlüssel ein, der von DeepL Translate Pro bereitgestellt wird. Es ist für die Authentifizierung erforderlich und ermöglicht Ihnen den Zugriff auf Übersetzungsdienste.
        - **Request Retriers** — Geben Sie an, wie oft Cognigy versuchen soll, den Übersetzungsanbieter anzurufen, wenn während der ersten Anfrage ein Fehler auftritt. Wenn Sie es beispielsweise auf "3" setzen, versucht es Cognigy dreimal, bevor eine Übersetzungsanfrage aufgegeben wird.
        - **Request Timeout** — legen Sie fest, wie lange Cognigy auf eine Antwort des Übersetzungsanbieters warten soll, nachdem Sie eine Anfrage gestellt haben, gemessen in Millisekunden. Wenn der Anbieter nicht innerhalb dieses Zeitrahmens antwortet, wird dies als Zeitüberschreitung betrachtet.
        - **Sentence Cache Expiry Timeout** — legt fest, wie lange Übersetzungen im Cache aufbewahrt werden sollen, bevor sie als veraltet gelten und entfernt werden. Der Standardwert ist "84.600" Sekunden, was 1 Tag entspricht. Sie können ihn auf "0" setzen, wenn kein Caching möglich ist.
        - **Benutzerdefinierte API-Basis-URL** – diese Einstellung ist optional. Wenn Sie bestimmte Anforderungen haben oder eine Verbindung zu einer benutzerdefinierten Instanz der DeepL Translate Pro API herstellen müssen, können Sie dieses Feld verwenden, um eine benutzerdefinierte Basis-URL anzugeben. Es ermöglicht Ihnen, die URL einschließlich des Protokollschemas zu definieren, z. B. "https://api-free.deepl.com/", um die API-Verbindung an Ihre Bedürfnisse anzupassen.

5. Klicken Sie auf **Speichern**.