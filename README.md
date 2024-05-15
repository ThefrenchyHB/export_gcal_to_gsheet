La fonction `export_gcal_to_gsheet` est conçue pour exporter des événements d'un calendrier Google vers une feuille de calcul Google dans une plage de dates spécifiée. Voyons ce que fait cette fonction et comment elle accomplit cette tâche :

1. **Authentification et récupération du calendrier** :
   - Elle commence par récupérer l'adresse e-mail de l'utilisateur actuel (`Session.getActiveUser().getEmail()`) pour identifier le calendrier Google associé à cet utilisateur.
   - Ensuite, elle récupère le calendrier en utilisant l'identifiant obtenu.

2. **Détermination de la plage de dates** :
   - La fonction récupère les dates de début et de fin pour l'exportation des événements à partir des cellules B3 et D3 de la feuille active, respectivement.
   - Elle incrémente la date de fin d'un jour pour s'assurer que les événements sur cette journée sont exclus.

3. **Effacement des données précédentes** :
   - Elle efface le contenu des lignes après la ligne 6 dans la feuille de calcul Google pour supprimer toute donnée d'événement précédente. Cela garantit que seuls les événements les plus récents sont affichés.

4. **Récupération des événements** :
   - En utilisant les dates de début et de fin déterminées, elle récupère les événements du calendrier Google dans la plage de dates spécifiée.
   - Facultativement, elle filtre les événements pour inclure uniquement ceux qui correspondent à une requête de recherche spécifique, spécifiée ici comme `'-project123'`.

5. **Formatage et population** :
   - Elle formate les événements récupérés dans un format structuré adapté à l'affichage dans la feuille de calcul Google.
   - Elle définit la ligne d'en-tête dans la feuille de calcul Google avec des étiquettes pour différents attributs d'événement.
   - Elle remplit la feuille de calcul Google avec les détails des événements, plaçant les attributs de chaque événement (comme l'heure de début, l'heure de fin, le titre, le lieu et la description) dans des colonnes séparées.

6. **Optimisation de l'écriture en lot** :
   - Pour optimiser les performances, elle utilise des écritures en lot pour définir les détails des événements dans la feuille de calcul Google. Cette approche minimise le nombre d'interactions avec l'API Google Sheets, améliorant ainsi l'efficacité, surtout pour les ensembles de données plus importants.

7. **Récupération du jour de la semaine** :
   - Elle inclut une fonction d'aide `getWeekDay` qui convertit un objet date en le nom du jour de la semaine correspondant (par exemple, dimanche, lundi, etc.). Cette fonction est utilisée pour déterminer le jour de la semaine de la date de début de chaque événement.

En résumé, cette fonction automatise le processus d'exportation des événements récents d'un calendrier Google vers une feuille de calcul Google, offrant un moyen pratique de consulter et d'analyser les données d'événement.



The `export_gcal_to_gsheet` function is designed to export events from a Google Calendar to a Google Sheet within a specified date range. Let's break down what this function does and how it accomplishes the task:

1. **Authentication and Calendar Retrieval**:
   - It first retrieves the email address of the current user (`Session.getActiveUser().getEmail()`) to identify the Google Calendar associated with that user.
   - Then, it fetches the calendar using the ID obtained.

2. **Date Range Determination**:
   - The function retrieves the start and end dates for the event export from cells B3 and D3 of the active sheet, respectively.
   - It increments the end date by one day to ensure that events occurring on that day are excluded.

3. **Clearing Previous Data**:
   - It clears the contents of rows after row 6 in the Google Sheet to remove any previous event data. This ensures that only the latest events are displayed.

4. **Event Retrieval**:
   - Using the determined start and end dates, it retrieves events from the Google Calendar within the specified date range.
   - Optionally, it filters the events to include only those that match a specific search query, specified here as `'-project123'`.

5. **Formatting and Population**:
   - It formats the retrieved events into a structured format suitable for display in the Google Sheet.
   - It sets the header row in the Google Sheet with labels for different event attributes.
   - It populates the Google Sheet with event details, placing each event's attributes (such as start time, end time, title, location, and description) in separate columns.

6. **Batch Write Optimization**:
   - To optimize performance, it uses batch writes to set event details in the Google Sheet. This approach minimizes the number of interactions with the Google Sheets API, improving efficiency, especially for larger datasets.

7. **Weekday Retrieval**:
   - It includes a helper function `getWeekDay` that converts a date object into the corresponding weekday name (e.g., Sunday, Monday, etc.). This function is used to determine the weekday of each event's start date.

Overall, this function automates the process of exporting recent events from a Google Calendar to a Google Sheet, providing a convenient way to review and analyze event data.
