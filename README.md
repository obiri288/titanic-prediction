# Titanic Überlebens-Vorhersage

Dieses Projekt ist eine vollständige End-to-End-Analyse des klassischen Titanic-Datensatzes von Kaggle. Das Ziel war es, ein Machine-Learning-Modell zu entwickeln, das vorhersagen kann, ob ein Passagier die Tragödie überlebt hat oder nicht. Es wurde ein **Logistisches Regressionsmodell** trainiert, das auf dem Testdatensatz eine Genauigkeit von **81.01%** erreichte.

---

## Inhaltsverzeichnis
1.  [Projekt-Workflow](#projekt-workflow)
2.  [Ergebnisse](#ergebnisse)
3.  [Verwendete Technologien](#verwendete-technologien)
4.  [Setup und Ausführung](#setup-und-ausführung)
5.  [Autor](#autor)
6.  [Lizenz](#lizenz)

---

## Projekt-Workflow

Das Projekt folgt einem strukturierten Machine-Learning-Workflow, der die folgenden Schritte umfasst:

**1. Explorative Datenanalyse (EDA)**
* Laden des Datensatzes mit `pandas`.
* Analyse der Datenstruktur, Datentypen und statistischen Kennzahlen mit `.info()` und `.describe()`.
* Identifizierung von fehlenden Werten (`NaN`) in den Spalten `Age`, `Cabin` und `Embarked`.

**2. Datenvorverarbeitung (Data Preprocessing)**
* **Behandlung fehlender Werte:**
    * `Age`: Die 177 fehlenden Alterswerte wurden mit dem **Median** der Spalte aufgefüllt, um die Robustheit gegenüber Ausreißern zu gewährleisten.
    * `Embarked`: Die 2 fehlenden Werte für den Einschiffungshafen wurden mit dem häufigsten Wert (Modus: 'S') aufgefüllt.
    * `Cabin`: Aufgrund der hohen Anzahl fehlender Werte (>77%) wurde diese Spalte vollständig entfernt, um das Modell nicht mit spekulativen Daten zu verzerren.

**3. Feature Engineering & Auswahl**
* **Umwandlung kategorialer Merkmale:**
    * `Sex`: Die Werte 'male' und 'female' wurden in `0` und `1` umgewandelt.
    * `Embarked`: Die Spalte wurde mittels **One-Hot Encoding** in drei separate binäre Spalten (`Embarked_C`, `Embarked_Q`, `Embarked_S`) transformiert, um eine fälschliche ordinale Beziehung zu vermeiden.
* **Entfernen nicht relevanter Merkmale:** Die Spalten `PassengerId`, `Name` und `Ticket` wurden entfernt, da sie in ihrer Rohform keinen direkten prädiktiven Wert für dieses Modell bieten.

**4. Modelltraining & Evaluierung**
* **Datensplitting:** Die aufbereiteten Daten wurden in ein Trainingsset (80%) und ein Testset (20%) aufgeteilt.
* **Modellwahl:** Es wurde ein **Logistisches Regressionsmodell** aus `scikit-learn` gewählt.
* **Training:** Das Modell wurde mit den Trainingsdaten (`X_train`, `y_train`) trainiert.
* **Evaluierung:** Die Leistung des trainierten Modells wurde auf dem ungesehenen Testset (`X_test`) bewertet.

---

## Ergebnisse

Das Modell lieferte auf dem Testdatensatz solide Ergebnisse für einen ersten Versuch:

* **Genauigkeit (Accuracy): `81.01%`**

* **Klassifikationsbericht:**
    ```
                  precision    recall  f1-score   support

               0       0.83      0.86      0.84       105
               1       0.79      0.74      0.76        74
    ```
    Das Modell kann **nicht-überlebende Passagiere (0)** sehr zuverlässig identifizieren (Recall von 0.86). Bei der Identifizierung von **Überlebenden (1)** ist es etwas zurückhaltender (Recall von 0.74).

* **Konfusionsmatrix:**
    ```
    [[90 15]
     [19 55]]
    ```
    * **90** Nicht-Überlebende wurden korrekt klassifiziert.
    * **55** Überlebende wurden korrekt klassifiziert.
    * **19** Überlebende wurden fälschlicherweise als nicht überlebt klassifiziert.

---

## Verwendete Technologien
* **Python 3**
* **Pandas:** Für Datenmanipulation und -analyse.
* **NumPy:** Für numerische Berechnungen.
* **Scikit-learn:** Für das Machine-Learning-Modell und Evaluierungsmetriken.
* **Matplotlib & Seaborn:** Für die Datenvisualisierung.
* **Jupyter Notebook / Google Colab:** Als Entwicklungsumgebung.

---

## Setup und Ausführung

Um dieses Projekt nachzuvollziehen, können Sie die folgenden Schritte ausführen:

1.  **Klone dieses Repository:**
    ```bash
    git clone (https://github.com/obiri288?tab=repositories)
    cd repositories
    ```

2.  **Installiere die Abhängigkeiten:**
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn
    ```

3.  **Führe das Notebook aus:**
    Öffne die `.ipynb`-Datei (z.B. `titanic_prediction.ipynb`) in einer Jupyter-Umgebung oder Google Colab und führe die Zellen nacheinander aus.

---

## Autor

* **OBIRI BORDOM**
* GitHub: `https://github.com/obiri288`

---

## Lizenz

Dieses Projekt ist unter der **MIT Lizenz** lizenziert.
