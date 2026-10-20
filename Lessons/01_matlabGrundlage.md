# Grundlagen

### Der MATLAB-Desktop

1. Toolstrip
2. Quick Access Toolbar
3. Search Bar
4. Current Folder Toolbar
5. Current Folder Browser
6. Command Window
7. Workspace Browser
8. Command History

![MATLAB Desktop](./assets/images/matlabMainWindow.JPG)

### Die MATLAB Hilfe
Zwei der größten Stärken von MATLAB gegenüber freier Software Alternativen wie
GNU Octave sind die umfangreiche Dokumentation und die große Online-Community.
Mit help kann die Hilfe zu einem MATLAB-Befehl direkt im Command Window ausgegeben
werden.


```matlab
help sinh
```

     sinh - Hyperbolic sine
        This MATLAB function returns the hyperbolic sine of the elements of X.
    
        Syntax
          Y = sinh(X)
    
        Input Arguments
          X - Input angles in radians
            scalar | vector | matrix | multidimensional array | table |
            timetable
    
        Examples
          openExample('matlab/HyperbolicSineOfVectorExample')
          openExample('matlab/GraphOfHyperbolicSineFunctionExample')
          openExample('matlab/PlotHyperbolicSineAndExponentialFunctionsExample')
    
        See also sin, asinh, cosh
    
        Introduced in MATLAB before R2006a
        Documentation for sinh
           doc sinh
    
        Other uses of sinh
    
           sym/sinh    tabular/sinh
    
    

Über helpwin kann die Online-Hilfe zu einem Befehl im Hilfe-Browser geöffnet werden.
Die etwas ausführlichere und oft mit Beispielen versehene HTML-Dokumentation
zu einem Befehl öffnet sich über doc.
Ist der genaue Name eines Befehls oder einer Funktion nicht bekannt, kann mit
lookfor die Kommentarzeilen aller MATLAB-Dateien im MATLAB-Pfad angezeigt werden.
Die in 2.1 erwähnte Search Bar vereint alle Möglichkeiten der MATLAB-Hilfe sehr
komfortabel.
Unter den größten und kompetentesten Online-Communities sind insbesondere MATLAB
Central und Stack Overflow zu nennen.

### Variablen und Datentypen
In MATLAB ist eine vorherige Deklaration der Variablen nicht erforderlich. Mit dem
Gleichheitszeichen = wird eine Variable im Workspace definiert und ihr ein Wert
zugewiesen. Gültige Variablennamen beginnen mit einem Buchstaben, gefolgt von
Buchstaben, Zahlen und Unterstrichen. MATLAB ist case-sensitive. Mit der exist Funktion
kann geprüft werden, ob ein Variablenname schon belegt ist; die Eingabe eines
Variablennamens ohne Zuweisung gibt ihren aktuellen Wert aus.


```matlab
exist variable_1
```




<html><body><pre>ans = 0</pre></body></html>




```matlab
variable_1 = 20
exist variable_1
```




<html><body><pre>variable_1 = 20</pre></body></html>






<html><body><pre>ans = 1</pre></body></html>




```matlab
Variable_1 = 10;
variable_1
```




<html><body><pre>variable_1 = 20</pre></body></html>



Standardmäßig verwendet MATLAB den Fließkomma-Datentyp double und wandelt ggf. vor Rechenoperationen dorthin um. Dieser Datentyp belegt 64 bit; der Datentyp single dahingegen
32 bit. Mit b = single(a) kann die Variable a eines beliebigen Datentyps in die Variable b des Datentyps single umgewandelt werden.

Es stehen drei vorzeichenbehaftete – int8, int16, int32 – und drei vorzeichenlose – uint8, uint16, uint32 – Festkomma-Datentypen zur Verfügung, wobei der Name den jeweils benötigten Speicherplatz
beschreibt – int8 etwa belegt 8 bit.

Für Strings wird der Datentyp char verwendet, welcher 16 bit belegt. Diese werden in einfachen Anführungszeichen eingegeben und in Zeilenvektoren gespeichert.


```matlab
word_1 = 'hello'
word_2 = 'world'
sentence_1 = [ word_1 ,', ', word_2 ]

```




<html><body><pre>word_1 = 'hello'</pre></body></html>






<html><body><pre>word_2 = 'world'</pre></body></html>






<html><body><pre>sentence_1 = 'hello, world'</pre></body></html>



Der Datentyp logical wird für logische Ausdrücke verwendet und belegt 8 bit. So
wird etwa mit a = logical (1) der Wahrheitswert a als logisch wahr definiert.
Mit Hilfe der Befehle struct und cell können Variablen in Strukturen bzw. multidimensionalen
Cell Arrays (siehe 3.1) zusammengestellt werden. Eine Struktur kann
aus mehreren Feldern mit zugehörigen Werten bestehen. Jedoch müssen alle Felder
einer Struktur dieselbe Dimension aufweisen.


```matlab
a = logical(1)
```




<html><body><pre>a = logical
   1
</pre></body></html>




```matlab
format hex;
a
variable_1
format long;
```




<html><body><pre>a = logical
   1
</pre></body></html>






<html><body><pre>variable_1 = 
   4034000000000000
</pre></body></html>



Mit Hilfe der Befehle struct und cell können Variablen in Strukturen bzw. multidimensionalen
Cell Arrays (siehe 3.1) zusammengestellt werden. Eine Struktur kann
aus mehreren Feldern mit zugehörigen Werten bestehen. Jedoch müssen alle Felder
einer Struktur dieselbe Dimension aufweisen.
Jedes Feld kann mit Hilfe eines Punktes und alle sich darin befindenden Werte mit
einer Klammer aufgerufen werden.


```matlab
s = struct ('a' ,{'k1 ','k2 '},'b' ,{3 ,5});
s.a
s(2).a
s.b
s(1).b
s(2).b
```




<html><body><pre>ans = 'k1 '</pre></body></html>






<html><body><pre>ans = 'k2 '</pre></body></html>






<html><body><pre>ans = 'k2 '</pre></body></html>






<html><body><pre>ans = 
     3
</pre></body></html>






<html><body><pre>ans = 
     5
</pre></body></html>






<html><body><pre>ans = 
     3
</pre></body></html>






<html><body><pre>ans = 
     5
</pre></body></html>



### Vorbelegte Variablen und Werte

 []()  |  |    
|:---:|---------------------------------|
|  pi | Kreiszahl  π               |
| i,j | Imaginäre Einheiten i           |
| inf | Unendlich ∞                      |
| ans | Variable der letzten Ausgabe    |
| eps | Relative Fließkomma-Genauigkeit |
| NaN | Not a Number                    |

## Vorbelegte Variablen und Werte
Einige Variablennamen sind reserviert und sollten nicht anders belegt werden. So
kann etwa mit pi auf die Kreiszahl pi oder mit eps auf die relative Fließkomma-Genauigkeit
zugegriffen werden. Eine Auswahl der gängigsten reservierten Variablen ist in 2.1
gegeben.
|  Befehl  |  Beschreibung     	|   Befehl    	|   Beschreibung   |
|---------	|---------------------	|-------	|---------------------------------	|
| pi   |Kreiszahl pi           |  ans | Variable der letzten Ausgabeeit |
| inf  |    Unendlich 1        |  eps | Relative Fließkomma-Genauigkeit |
| i, j |   Imaginäre Einheit i |  NaN | Not a Number|


```matlab
pi
i
eps
```




<html><body><pre>ans = 
   3.141592653589793
</pre></body></html>






<html><body><pre>ans = 
  0.000000000000000 + 1.000000000000000i
</pre></body></html>






<html><body><pre>ans = 
     2.220446049250313e-16
</pre></body></html>



How to get NaN and inf as an output?


```matlab
1 / inf
1 / 0
1 / -0
0 / 0
```




<html><body><pre>ans = 
     0
</pre></body></html>






<html><body><pre>ans = 
   Inf
</pre></body></html>






<html><body><pre>ans = 
  -Inf
</pre></body></html>






<html><body><pre>ans = 
   NaN
</pre></body></html>



### Arithmetische Operatoren und Ausdrücke
Addition +, Subtraktion -, Multiplikation * und Division /. Das Ergebnis wird als ans – kurz für „answer“ – in den Workspace
geschrieben. Mit der ans kann weiter gerechnet werden und die Ausgabe kann mit einem Semikolon
unterdrückt werden.

Der Potenzoperator ^ wird vor Multiplikation bzw. Division und diese wiederum vor Addition bzw.
Subtraktion ausgewertet. Zehnerpotenzen können mit e oder E definiert werden.


```matlab
1 + 2
ans+1;
ans+1
```




<html><body><pre>ans = 
     3
</pre></body></html>






<html><body><pre>ans = 
     5
</pre></body></html>




```matlab
2e-1
2^2*5^(-1)
```




<html><body><pre>ans = 
   0.200000000000000
</pre></body></html>






<html><body><pre>ans = 
   0.800000000000000
</pre></body></html>



### Komplexe Zahlen und Zufallszahlen
Eine komplexe Zahl kann mit dem Befehl complex oder mit der reservierten Variable
i erzeugt werden.


```matlab
complex (3 , -2)
3-2i
```




<html><body><pre>ans = 
  3.000000000000000 - 2.000000000000000i
</pre></body></html>






<html><body><pre>ans = 
  3.000000000000000 - 2.000000000000000i
</pre></body></html>



| | |
|:-----------:|-------------------------------------------------------------|
|     rand    | gleichverteilte Zufallszahl zwischen 0 und 1                |
| randi(max)  | ganzzahlige, gleichverteilte Zufallszahl zwischen 1 und max |
| randn       | standardnormalverteilte Zufallszahl                         |
|     rng     | Variable der letzten Ausgabe                                |

Mit dem Befehl rng kann der Status des Zufallszahlengenerators gespeichert und somit dieselben
Zufallszahlen erneut generiert werden. Der Befehl rng(seed) generiert eine Abfolge von Zufallszahlen
anhand eines Startwerts (seed). Standardmäßig ist der Startwert Null hinterlegt. Mit dem Befehl
rng(’default’) kann die Abfolge von Zufallszahlen auf die Standardeinstellungen zurückgesetzt
werden. Diese Befehle dienen dazu Zufallsfolgen reproduzierbar bzw. Ergebnisse vergleichbar zu
machen.
|  Befehl     	|     Beschreibung     	|  
|---------	|--------	|
|rand       | gleichverteilte Zufallszahl zwischen 0 und 1                 | 
|randi(max) | ganzzahlige, gleichverteilte Zufallszahl zwischen 1 und max  | 
|randn      | standardnormalverteilte Zufallszahl                          | 
|rng        | Status des Zufallszahlengenerators                           | 


```matlab
rng (42)
rand
randn
randi(10)
rng(123)
rand
randi(10)

```




<html><body><pre>ans = 
   0.374540118847362
</pre></body></html>






<html><body><pre>ans = 
   0.867232157629573
</pre></body></html>






<html><body><pre>ans = 
     8
</pre></body></html>






<html><body><pre>ans = 
   0.696469185597862
</pre></body></html>






<html><body><pre>ans = 
     3
</pre></body></html>



### Mathematische Funktionen

MATLAB stellt von Haus aus eine Vielzahl mathematischer Funktionen bereit. Neben
der in 2.3 gegebenen Auswahl führt die help elfun zu einer Übersicht der elementaren
mathematischen Funktionen; help datafun zu einer weiterführenden Übersicht
von Funktionen zur Datenanalyse wie Mittelwert und Median; help specfun zu speziellen
Funktionen.
| Befehl      | Beschreibung                          | Befehl      | Beschreibung                          |
|-------------|--------------------------------------|-------------|--------------------------------------|
| sin(x)      | Sinus (x im Bogenmaß)               | bs(x)       | Betrag                               |
| cos(x)      | Cosinus (x im Bogenmaß)             | angle(x)    | Argument                             |
| tan(x)      | Tangens (x im Bogenmaß)             | real(x)     | Real                                 |
| cot(x)      | Cotangens (x im Bogenmaß)           | imag(x)     | Imaginär                             |
| sind(x)     | Sinus (x im Gradmaß)                | conj(x)     | Komplexe Konjugation                |
| asin(x)     | Arkussinus (x im Bogenmaß)          |     -        |         -                             |
| asind(x)    | Arkussinus (x im Gradmaß)           | ceil(x)     | Rundung aufwärts                    |
| floor(x)    | Rundung abwärts                     |    -        |              -                        |
| exp(x)      | Exponentialfunktion                 | fix(x)      | Rundung Richtung null               |
| log(x)      | Natürlicher Logarithmus             | round(x)    | Rundung zur nächsten Ganzzahl       |
| log10(x)    | Dekadischer Logarithmus             | sign(x)     | Signum                               |
| log2(x)     | Logarithmus zur Basis 2             | mod(x,y)    | Modulo                               |
| sqrt(x)     | Quadratwurzel                       | rem(x,y)    | Rest                                |


```matlab
sin(pi/2)
sin(90)
log(10)
log10(10)
log2(4)
sqrt(-1)
abs(3+4i)
angle(3+4i)
conj(-3-4i)


```




<html><body><pre>ans = 
     1
</pre></body></html>






<html><body><pre>ans = 
   0.893996663600558
</pre></body></html>






<html><body><pre>ans = 
   2.302585092994046
</pre></body></html>






<html><body><pre>ans = 
     1
</pre></body></html>






<html><body><pre>ans = 
     2
</pre></body></html>






<html><body><pre>ans = 
  0.000000000000000 + 1.000000000000000i
</pre></body></html>






<html><body><pre>ans = 
     5
</pre></body></html>






<html><body><pre>ans = 
   0.927295218001612
</pre></body></html>






<html><body><pre>ans = 
 -3.000000000000000 + 4.000000000000000i
</pre></body></html>




```matlab
ceil(0.2)
floor(0.2)
fix(2.1)
round(2.5)
sign([-6, 0, 2.5])
```




<html><body><pre>ans = 
     1
</pre></body></html>






<html><body><pre>ans = 
     0
</pre></body></html>






<html><body><pre>ans = 
     2
</pre></body></html>






<html><body><pre>ans = 
     3
</pre></body></html>






<html><body><pre>ans = 1×3 double
    -1     0     1
</pre></body></html>



Unterschied zwischen mod und rest?
Das Konzept des Rests nach einer Division ist nicht eindeutig definiert, und die beiden Funktionen mod und rem berechnen jeweils eine unterschiedliche Variante. Die mod-Funktion liefert ein Ergebnis, das entweder null ist oder dasselbe Vorzeichen wie der Divisor hat. Die rem-Funktion liefert ein Ergebnis, das entweder null ist oder dasselbe Vorzeichen wie der Dividend hat.
Ein weiterer Unterschied ist die Konvention, wenn der Divisor null ist. Die mod-Funktion folgt der Konvention, dass mod(a,0) den Wert a zurückgibt, während die rem-Funktion der Konvention folgt, dass rem(a,0) NaN zurückgibt.
Beide Varianten haben ihre Anwendungsbereiche. Zum Beispiel ist die mod-Funktion in der Signalverarbeitung im Zusammenhang mit periodischen Signalen nützlich, da ihre Ausgabe periodisch ist (mit einer Periode, die dem Divisor entspricht).


```matlab
mod(10, 3)
rem(10, 3)
mod(-14, 3)
rem(-14, 3)
```




<html><body><pre>ans = 
     1
</pre></body></html>






<html><body><pre>ans = 
     1
</pre></body></html>






<html><body><pre>ans = 
     1
</pre></body></html>






<html><body><pre>ans = 
    -2
</pre></body></html>



🔢 1. Kryptographie
Beispiel: RSA-Verschlüsselung nutzt Modulo-Arithmetik, um Schlüssel zu erzeugen und Nachrichten zu verschlüsseln/entschlüsseln.
Warum: Modulo hilft, große Zahlen in einem festen Zahlenbereich zu halten.

🧮 2. Hashfunktionen
Beispiel: Hash-Tabellen verwenden mod, um einen Hashwert auf einen Index im Array zu reduzieren.
Warum: Um sicherzustellen, dass der Index innerhalb der Array-Grenzen liegt.

🕒 3. Zeit- und Datumsberechnungen
Beispiel: Uhrzeitberechnungen wie (Stunde + x) % 24 für 24-Stunden-Format.
Warum: Um zyklische Werte wie Stunden, Tage oder Monate korrekt zu berechnen.

🎮 4. Spieleentwicklung
Beispiel: Spielfiguren, die sich auf einem Spielfeld zyklisch bewegen (z. B. bei Snake oder Pac-Man).
Warum: Um Bewegungen innerhalb eines begrenzten Spielfelds zu ermöglichen.

🧪 5. Mathematische Simulationen
Beispiel: Simulationen mit periodischen Randbedingungen (z. B. in der Physik).
Warum: Um Modelle mit wiederkehrenden Mustern zu erstellen.

# Beispiele und Übungen zu den Grundlagen

### Beispiel 1
Verwenden Sie den Befehl lookfor um einen Überblick über alle MATLAB-Dateien zu
geben, die auf das Winkelmaß Grad (degree) Bezug nehmen.
Welche mathematische Funktion ist geeignet um den Sinus vom Winkelmaß in Grad
zu berechnen?


```matlab
lookfor degree
sind(90)
```

    amd                            - Approximate minimum degree permutation
    colamd                         - Column approximate minimum degree permutation
    deg2rad                        - Convert angle from degrees to radians
    rad2deg                        - Convert angle from radians to degrees
    rot90                          - Rotate array 90 degrees
    symamd                         - Symmetric approximate minimum degree permutation
    digraph.indegree               - In-degree of nodes
    digraph.outdegree              - Out-degree of nodes
    double.acosd                   - Inverse cosine in degrees
    double.acotd                   - Inverse cotangent in degrees
    double.acscd                   - Inverse cosecant in degrees
    double.asecd                   - Inverse secant in degrees
    double.asind                   - Inverse sine in degrees
    double.atan2d                  - Four-quadrant inverse tangent in degrees
    double.atand                   - Inverse tangent in degrees
    double.cosd                    - Cosine of argument in degrees
    double.cotd                    - Cotangent of argument in degrees
    double.cscd                    - Cosecant of argument in degrees
    double.secd                    - Secant of argument in degrees
    double.sind                    - Sine of argument in degrees
    double.tand                    - Tangent of argument in degrees
    graph.degree                   - Degree of graph nodes
    matlab.graphics.chart.GeographicBubbleChart.LatitudeData - Latitude coordinates in degrees
    matlab.graphics.chart.GeographicBubbleChart.LongitudeData - Longitude coordinates in degrees
    matlab.graphics.chart.primitive.DensityPlot.LatitudeData - Latitude coordinates in degrees
    matlab.graphics.chart.primitive.DensityPlot.LongitudeData - Longitude coordinates in degrees
    matlab.graphics.shape.Ellipse.Rotation - Rotation angle in degrees
    matlab.graphics.shape.Rectangle.Rotation - Rotation angle in degrees
    matlab.graphics.shape.TextArrow.TextRotation - Text rotation angle in degrees
    matlab.graphics.shape.TextBox.Rotation - Rotation angle in degrees
    matlab.ui.control.NinetyDegreeGauge.Value - Location of gauge needle
    matlab.ui.control.NinetyDegreeGauge.Limits - Minimum and maximum gauge scale values
    matlab.ui.control.NinetyDegreeGauge.Orientation - Orientation
    matlab.ui.control.NinetyDegreeGauge.ScaleDirection - Direction of gauge scale
    matlab.ui.control.NinetyDegreeGauge.ScaleColors - Scale colors
    matlab.ui.control.NinetyDegreeGauge.ScaleColorLimits - Scale color limits
    matlab.ui.control.NinetyDegreeGauge.MajorTicks - Major tick mark locations
    matlab.ui.control.NinetyDegreeGauge.MajorTicksMode - Major tick creation mode
    matlab.ui.control.NinetyDegreeGauge.MajorTickLabels - Major tick labels
    matlab.ui.control.NinetyDegreeGauge.MajorTickLabelsMode - Major tick labels mode
    matlab.ui.control.NinetyDegreeGauge.MinorTicks - Minor tick locations
    matlab.ui.control.NinetyDegreeGauge.MinorTicksMode - Minor tick creation mode
    matlab.ui.control.NinetyDegreeGauge.FontName - Font name
    matlab.ui.control.NinetyDegreeGauge.FontSize - Font size
    matlab.ui.control.NinetyDegreeGauge.FontWeight - Font weight
    matlab.ui.control.NinetyDegreeGauge.FontAngle - Font angle
    matlab.ui.control.NinetyDegreeGauge.FontColor - Font color
    matlab.ui.control.NinetyDegreeGauge.BackgroundColor - Background color
    matlab.ui.control.NinetyDegreeGauge.Visible - State of visibility
    matlab.ui.control.NinetyDegreeGauge.Enable - Operational state of gauge
    matlab.ui.control.NinetyDegreeGauge.Tooltip - Tooltip
    matlab.ui.control.NinetyDegreeGauge.ContextMenu - Context menu
    matlab.ui.control.NinetyDegreeGauge.Position - Location and size of gauge
    matlab.ui.control.NinetyDegreeGauge.InnerPosition - Inner location and size of gauge
    matlab.ui.control.NinetyDegreeGauge.OuterPosition - Outer location and size of gauge
    matlab.ui.control.NinetyDegreeGauge.Layout - Layout options
    matlab.ui.control.NinetyDegreeGauge.CreateFcn - Creation function
    matlab.ui.control.NinetyDegreeGauge.DeleteFcn - Deletion function
    matlab.ui.control.NinetyDegreeGauge.Interruptible - Callback interruption
    matlab.ui.control.NinetyDegreeGauge.BusyAction - Callback queuing
    matlab.ui.control.NinetyDegreeGauge.BeingDeleted - Deletion status
    matlab.ui.control.NinetyDegreeGauge.Parent - Parent container
    matlab.ui.control.NinetyDegreeGauge.HandleVisibility - Visibility of object handle
    matlab.ui.control.NinetyDegreeGauge.Type - Type of graphics object
    matlab.ui.control.NinetyDegreeGauge.Tag - Object identifier
    matlab.ui.control.NinetyDegreeGauge.UserData - User data
    matlab.ui.control.NinetyDegreeGauge - Ninety-degree gauge UI component
    Celsius to Fahrenheit          - Convert degrees Celsius to degrees Fahrenheit
    Degrees to Radians             - Convert degrees to radians
    Fahrenheit to Celsius          - Convert degrees Fahrenheit to degrees Celsius
    Radians to Degrees             - Convert radians to degrees
    Discrete PID Controller (2DOF) - Discrete-time or continuous-time two-degree-of-freedom PID controller
    PID Controller (2DOF)          - Continuous-time or discrete-time two-degree-of-freedom PID controller
    TMP102 Temperature Sensor      - Read ambient temperature in degree Celsius using TMP102 temperature sensor
    Compiler optimization level    - Degree of compiler optimization when generating code for simulation
    couplerRatrace                 - Create equal-split rat-race coupler or 180-degree-ring hybrid
    quaternion.eulerd              - Convert quaternion to Euler angles (degrees)
    quaternion.rotvecd             - Convert quaternion to rotation vector (degrees)
    quaternion.eulerd              - Convert quaternion to Euler angles (degrees)
    quaternion.rotvecd             - Convert quaternion to rotation vector (degrees)
    sym.polynomialDegree           - Degree of polynomial
    comm.Ray.AngleOfDeparture      - Angle of departure, in degrees
    comm.Ray.AngleOfArrival        - Angle of arrival, in degrees
    measuredAntenna.PhaseShift     - Phase shift of array elements in degrees
    PolarPattern.AngleResolution   - Number of degrees between radial lines
    PolarPattern.ZeroAngleLine     - Highlight radial line at zero degrees
    rfprop.Rain.Tilt               - Polarization tilt angle of signal, in degrees
    rfprop.RayTracing.AngularSeparation - Average number of degrees between launched rays
    rxsite.Latitude                - Latitude coordinates of site, in degrees
    rxsite.Longitude               - Longitude coordinates of site, in degrees
    rxsite.AntennaAngle            - Antenna x-axis angle, in degrees
    txsite.Latitude                - Latitude coordinates of site, in degrees
    txsite.Longitude               - Longitude coordinates of site, in degrees
    txsite.AntennaAngle            - Antenna x-axis angle, in degrees
    comm.DPDCoefficientEstimator.Degree - Memory-polynomial degree
    comm.Ray.AngleOfDeparture      - Angle of departure, in degrees
    comm.Ray.AngleOfArrival        - Angle of arrival, in degrees
    dpdPreprocessor.Degree         - Nonlinearity degree of DPD
    rfprop.Rain.Tilt               - Polarization tilt angle of signal, in degrees
    rfprop.RayTracing.AngularSeparation - Average number of degrees between launched rays
    rxsite.Latitude                - Latitude coordinates of site, in degrees
    rxsite.Longitude               - Longitude coordinates of site, in degrees
    rxsite.AntennaAngle            - Antenna x-axis angle, in degrees
    txsite.Latitude                - Latitude coordinates of site, in degrees
    txsite.Longitude               - Longitude coordinates of site, in degrees
    txsite.AntennaAngle            - Antenna x-axis angle, in degrees
    geoTrajectory.Course           - Angle between velocity direction and North (degree)
    ggiwphd.DegreesOfFreedom       - Degrees of freedom parameter of Inverse-Wishart distribution for each component
    polynomialTrajectory.Course    - Horizontal direction of travel (degrees)
    waypointTrajectory.Course      - Horizontal direction of travel (degree)
    gabor.Orientation              - Orientation of filter in degrees
    images.geotrans.PolynomialTransformation2D.Degree - Degree of polynomial transformation
    images.ui.graphics.Viewer.DenoisingDegreeOfSmoothing - Denoising degree of smoothing
    fgen.StartPhase                - Horizontal offset in degrees of the standard waveform the function generator produces
    Polar.AngleResolution          - Number of degrees between radial lines
    Polar.ZeroAngleLine            - Highlight radial line at zero degrees
    classreg.regr.CompactGeneralizedLinearModel.DFE - Degrees of freedom for error
    classreg.regr.CompactLinearModel.DFE - Degrees of freedom for error
    GeneralizedLinearMixedModel.DFE - Degrees of freedom for error
    GeneralizedLinearModel.DFE     - Degrees of freedom for error
    LinearMixedModel.DFE           - Residual degrees of freedom
    LinearModel.DFE                - Degrees of freedom for error
    manova.DFE                     - Degrees of freedom for error
    mixtureDOE.Degree              - Degree of design
    MultinomialRegression.DFE      - Degrees of freedom for error
    NonLinearModel.DFE             - Degrees of freedom for error
    prob.tLocationScaleDistribution.nu - Degrees of freedom
    RepeatedMeasuresModel.DFE      - Error degrees of freedom
    
    




<html><body><pre>ans = 
     1
</pre></body></html>



### Beispiel 2
Erzeugen Sie eine zufällige ganze Zahl zwischen -1000 und 1000 und weisen Sie diese der Variable
q mit dem Datentyp int32 zu.

Verwenden Sie nun die Funktion typecast um aus der Variable einen uint32 zu machen. Wie
unterscheidet sich die klassische Umwandlung des Datentyps in der Form uint32(q) von der
Umwandlungsfunktion typecast?


```matlab
q= int32 ( randi (2001) -1001)
typecast (q,'uint32')
uint32 (q)
q= int32 ( randi (2001) -1001)
typecast (q,'uint32')
uint32 (q)
```




<html><body><pre>q = int32
   -547
</pre></body></html>






<html><body><pre>ans = uint32
   4294966749
</pre></body></html>






<html><body><pre>ans = uint32
   0
</pre></body></html>






<html><body><pre>q = int32
   103
</pre></body></html>






<html><body><pre>ans = uint32
   103
</pre></body></html>






<html><body><pre>ans = uint32
   103
</pre></body></html>




```matlab
format hex;
q= int32 ( randi (2001) -1001)
typecast (q,'uint32')
uint32 (q)
format long;

```




<html><body><pre>q = int32
   000001b7
</pre></body></html>






<html><body><pre>ans = uint32
   000001b7
</pre></body></html>






<html><body><pre>ans = uint32
   000001b7
</pre></body></html>



### Beispiel 3
In einer der Aufgaben müssen Sie einen Text chiffrieren. Dieses Beispiel dient dem Dechiffrieren des
chiffrierten Textes. Das verwendete Chiffre ist das Caesar Chiffre. Dabei wird ein chiffrierter Text
übergeben (’PFL#jrhv#klvwru|’) und durch eine Subtraktion der Zahl 3 sowie einer Umwandlung
des Datentyps wieder zum Ursprungstext zusammengesetzt.


```matlab
char ('PFL#jrhv#klvwru|' -3)
```




<html><body><pre>ans = 'MCI goes history'</pre></body></html>



### Beispiel 4
Generieren Sie eine komplexe Zahl z mit z = a - i · b, wobei der Realteil a und der Imaginärteil
b standardnormalverteilte Zufallszahlen sind und bestimmen Sie das Vorzeichen des Real- und
Imaginärteils.


```matlab
z = randn - i* randn
sign ( real (z))
sign ( imag (z))
```




<html><body><pre>z = 
 -0.323487127917541 - 1.334335877747957i
</pre></body></html>






<html><body><pre>ans = 
    -1
</pre></body></html>






<html><body><pre>ans = 
    -1
</pre></body></html>



### Beispiel 5
In diesem Beispiel wird gezeigt, dass auch periodische und komplex wirkende Zahlen oft zu einem
sehr einfachen, ja sogar natürlichen Ergebnis führen können. Berechnen Sie mit der Euler Zahl,
der Kreiszahl pi und der imaginären Zahl i das Ergebnis wie folgt
√e^(−i2π)


```matlab
sqrt(exp(-i*2* pi ))
```




<html><body><pre>ans = 
  1.000000000000000 + 0.000000000000000i
</pre></body></html>



### Übung 1
Verwenden Sie die help- und doc-Funktion um die Funktionalität und Eigenschaften von verschiedenen
MATLAB Befehlen nachzuschlagen. Welche verschiedenen Datentypen können in MATLAB noch zugewiesen werden? Nennen Sie mindestens
acht verschiedene Datentypen. Was sind deren Eigenschaften in einem kurzen Statement
beschrieben?


```matlab
help double
doc double
```

     double - Double-precision arrays
        double is the default numeric data type (class) in MATLAB, providing
        sufficient precision for most computational tasks.
    
        Creation
          Syntax
            Y = double(X)
    
          Input Arguments
            X - Input array
              scalar | vector | matrix | multidimensional array
    
        Object Functions
          mtimes           - Matrix multiplication
          xor              - Find logical exclusive-OR
          asind            - Inverse sine in degrees
          ellipticPi       - Complete and incomplete elliptic integrals of the third kind
          acosd            - Inverse cosine in degrees
          sqrt             - Square root
          acoth            - Inverse hyperbolic cotangent
          eps              - Floating-point relative accuracy
          uminus           - Unary minus
          ge               - Determine greater than or equal to
          logint           - Logarithmic integral function
          iscolumn         - Determine if input is column vector
          acot             - Inverse cotangent in radians
          isempty          - Determine whether array is empty
          isequal          - Determine array equality
          acscd            - Inverse cosecant in degrees
          isequaln         - Determine array equality, treating NaN values as equal
          dirac            - Dirac delta function
          maxk             - Find k largest elements of array
          cos              - Cosine of argument in radians
          ismatrix         - Determine whether input is matrix
          ellipticF        - Incomplete elliptic integral of the first kind
          isreal           - Determine whether array uses complex storage
          triangularPulse  - Triangular pulse function
          cosd             - Cosine of argument in degrees
          isrow            - Determine if input is row vector
          length           - Length of largest array dimension
          cosint           - Cosine integral function
          cosh             - Hyperbolic cosine
          isscalar         - Determine whether input is scalar
          mldivide         - Solve systems of linear equations Ax = B for x
          issorted         - Determine if array is sorted
          zeta             - Riemann zeta function
          sind             - Sine of argument in degrees
          issortedrows     - Determine if matrix or table rows are sorted
          chebyshevT       - Chebyshev polynomials of the first kind
          isvector         - Determine whether input is vector
          mink             - Find k smallest elements of array
          ndims            - Number of array dimensions
          ellipticCK       - Complementary complete elliptic integral of the first kind
          nnz              - Number of nonzero matrix elements
          numel            - Number of array elements
          size             - Array size
          asec             - Inverse secant in radians
          abs              - Absolute value and complex magnitude
          and              - Find logical AND
          coshint          - Hyperbolic cosine integral function
          ceil             - Round toward positive infinity
          diff             - Differences and approximate derivatives
          eq               - Determine equality
          power            - Element-wise power
          fix              - Round toward zero
          divisors         - Divisors of integer or expression
          floor            - Round toward negative infinity
          gt               - Determine greater than
          uplus            - Unary plus
          sinpi            - Compute sin(X*pi) accurately
          isfinite         - Determine which array elements are finite
          isinf            - Determine which array elements are infinite
          ellipticCPi      - Complementary complete elliptic integral of the third kind
          isnan            - Determine which array elements are NaN
          ldivide          - Left array division
          le               - Determine less than or equal to
          lt               - Determine less than
          or               - Find logical OR
          max              - Maximum elements of array
          min              - Minimum elements of array
          minus            - Subtraction
          ne               - Determine inequality
          mod              - Remainder after division (modulo operation)
          not              - Find logical NOT
          plus             - Add numbers, append strings
          pow2             - Base 2 exponentiation and scaling of floating-point numbers
          prod             - Product of array elements
          rdivide          - Right array division
          rem              - Remainder after division
          round            - Round to nearest decimal or integer
          ellipticCE       - Complementary complete elliptic integral of the second kind
          sign             - Sign function (signum function)
          sum              - Sum of array elements
          cummax           - Cumulative maximum
          cummin           - Cumulative minimum
          cumprod          - Cumulative product
          cumsum           - Cumulative sum
          exp              - Exponential
          expm1            - Compute exp(X)-1 accurately for small X
          minpoly          - Minimal polynomial of matrix
          log              - Natural logarithm
          log10            - Common logarithm (base 10)
          log1p            - Compute natural logarithm of 1+X accurately for small X
          log2             - Base 2 logarithm and floating-point number dissection
          acos             - Inverse cosine in radians
          acosh            - Inverse hyperbolic cosine
          acotd            - Inverse cotangent in degrees
          acsc             - Inverse cosecant in radians
          acsch            - Inverse hyperbolic cosecant
          asecd            - Inverse secant in degrees
          asech            - Inverse hyperbolic secant
          asin             - Inverse sine in radians
          asinh            - Inverse hyperbolic sine
          atan             - Inverse tangent in radians
          atan2            - Four-quadrant inverse tangent
          rectangularPulse - Rectangular pulse function
          atan2d           - Four-quadrant inverse tangent in degrees
          signIm           - Sign of the imaginary part of complex number
          atand            - Inverse tangent in degrees
          atanh            - Inverse hyperbolic tangent
          whittakerW       - Whittaker W function
          cospi            - Compute cos(X*pi) accurately
          sin              - Sine of argument in radians
          sinh             - Hyperbolic sine
          tan              - Tangent of argument in radians
          tand             - Tangent of argument in degrees
          tanh             - Hyperbolic tangent
          bernoulli        - Bernoulli numbers and polynomials
          charpoly         - Characteristic polynomial of matrix
          mrdivide         - Solve systems of linear equations xA = B for x
          dawson           - Dawson integral
          ellipticK        - Complete elliptic integral of the first kind
          svd              - Singular value decomposition
          jacobiP          - Jacobi polynomials
          times            - Multiplication
          erfi             - Imaginary error function
          sinint           - Sine integral function
          legendreP        - Legendre polynomials
          chebyshevU       - Chebyshev polynomials of the second kind
          dilog            - Dilogarithm function
          ei               - One-argument exponential integral function
          ellipticE        - Complete and incomplete elliptic integrals of the second kind
          ellipticNome     - Elliptic nome function
          euler            - Euler numbers and polynomials
          fresnelc         - Fresnel cosine integral function
          fresnels         - Fresnel sine integral function
          gegenbauerC      - Gegenbauer polynomials
          harmonic         - Harmonic function (harmonic number)
          hermiteH         - Hermite polynomials
          hurwitzZeta      - Hurwitz zeta function
          igamma           - Incomplete gamma function
          jordan           - Jordan normal form (Jordan canonical form)
          kummerU          - Confluent hypergeometric Kummer U function
          laguerreL        - Generalized Laguerre Function and Laguerre Polynomials
          pochhammer       - Pochhammer symbol
          poly2sym         - Create symbolic polynomial from vector of coefficients
          polylog          - Polylogarithm
          sinhint          - Hyperbolic sine integral function
          ssinint          - Shifted sine integral function
          whittakerM       - Whittaker M function
          wrightOmega      - Wright omega function
          colon            - Vector creation, array subscripting, and for-loop iteration
          cat              - Concatenate arrays
          horzcat          - Concatenate arrays horizontally
          vertcat          - Concatenate arrays vertically
          ctranspose       - Complex conjugate transpose
          permute          - Permute array dimensions
          reshape          - Reshape array by rearranging existing elements
          sort             - Sort array elements
          transpose        - Transpose vector or matrix
    
        Examples
          openExample('matlab/CreateDoublePrecisionVariablesExample')
          openExample('matlab/DoublePrecisionVersusSinglePrecisionExample')
    
        See also cast, single, str2double, typecast, realmin, realmax, eps
    
        Introduced in MATLAB before R2006a
        Documentation for double
           doc double
    
        Other uses of double
    
           categorical/double    fixedpoint/double      signal/double
           DataMatrix/double     opaque/double          string/double
           dataset/double        opc.hda.Data/double    sym/double
           dsp/double            quaternion/double
    
    

### Übung 2
Definieren Sie sich vier verschiedene Variablen mit verschiedenen Datentypen und zeigen Sie in
einem Beispiel wie Sie kontrollieren können, ob eine Variable bereits existiert.


```matlab
a = 23
exist a
exist b
```




<html><body><pre>a = 
    23
</pre></body></html>






<html><body><pre>ans = 
     1
</pre></body></html>






<html><body><pre>ans = 
     0
</pre></body></html>



### Übung 3
MATLAB verwendet den Datentyp double als Standard Datentyp bei der Definition von Variablen,
soweit kein anderer Datentyp bei der Definition spezifiziert wird. Definieren Sie eine Variable mit
dem Datentyp double mit dem Wert -5400. Wandeln Sie diese Variable in die Datentypen int8,
single und uint16 um. Berichten Sie von den Ergebnissen und begründen Sie diese.


```matlab
x = -5400
int8(x)
single(x)
uint16(x)
format hex
single(x)
x
format long
```




<html><body><pre>x = 
       -5400
</pre></body></html>






<html><body><pre>ans = int8
   -128
</pre></body></html>






<html><body><pre>ans = single
       -5400
</pre></body></html>






<html><body><pre>ans = uint16
   0
</pre></body></html>






<html><body><pre>ans = single
   c5a8c000
</pre></body></html>






<html><body><pre>x = 
   c0b5180000000000
</pre></body></html>



int8. Werte außerhalb des Bereichs $[-2^7, 2^7-1]$ werden dem nächsten Endpunkt zugeordnet.

uint8. Werte außerhalb des Bereichs $[0 , 2^8-1]$ werden dem nächsten Endpunkt zugeordnet.

MATLAB konstruiert seine Doppel- und Single-Floating-Point-Datentypen nach IEEE-Format und folgt der Runde bis zum nächsten, bindet standardmäßig sogar den Rundmodus an.

Eine schwebende Punktzahl x hat die Form:

$x= (-1^s) (1+f) 2^e$

wo:

s bestimmt das Zeichen.

f ist die Fraktion oder Mantissa, die 0 .

e ist der Exponent.

s, f, und e werden jeweils durch eine begrenzte Anzahl von Bits im Speicher bestimmt, mit f und e abhängig von der Genauigkeit des Datentyps.

einer **double** Zahl benötigt 64 Bit, wie in dieser Tabelle gezeigt.

|   Bits   | Width |                          Usage                         |
|:--------:|:-----:|:------------------------------------------------------:|
| 63       | 1     | Stores the sign, where 0 is positive and 1 is negative |
| 62 to 52 | 11    | Stores the exponent, biased by 1023                    |
| 51 to 0  | 52    | Stores the mantissa                                    |

Die Speicherung einer **single** Zahl benötigt 32 Bit, wie in dieser Tabelle gezeigt.
|   Bits   | Width |                          Usage                         |
|:--------:|:-----:|:------------------------------------------------------:|
| 31       | 1     | Stores the sign, where 0 is positive and 1 is negative |
| 30 to 23 | 8     | Stores the exponent, biased by 127                     |
| 22 to 0  | 23    | Stores the mantissa                                    |

### Übung 4
Vor mehr als 2000 Jahren hat Gaius Iulius Caesar seine komplette militärische Korrespondenz mit
der Caesar Chiffre verschlüsselt. Diese Chiffre beruht auf der monoalphabetischen Substitution.
Dabei wird beispielsweise der Buchstabe A zu D, B zu E, C zu F, indem das Alphabet einfach
um drei Stellen verrückt wird. In MATLAB kann dieser Code recht simpel durch eine klassische
Umwandlung des Datentyps und einer Addition umgesetzt werden. Definieren sie einen beliebigen
Text und wandeln Sie ihn in den Datentyp uint16 um. Zählen Sie 3 zum Ergebnis hinzu und
wandeln Sie das Ergebnis wieder in den Datenyp char um.


```matlab
hiddenText = 'This is a hidden text that should not be displayed in the output.'
encryptedText = uint16(hiddenText) + 3;
char (encryptedText)
decryptedText = char(encryptedText - 3);
fprintf(decryptedText)
```




<html><body><pre>hiddenText = 'This is a hidden text that should not be displayed in the output.'</pre></body></html>






<html><body><pre>ans = 'Wklv#lv#d#klgghq#wh{w#wkdw#vkrxog#qrw#eh#glvsod|hg#lq#wkh#rxwsxw1'</pre></body></html>



    This is a hidden text that should not be displayed in the output.

### Übung 5
Versuchen Sie herauszufinden, welche Variablen noch vordefiniert sind. Nennen Sie mindestens
fünf verschiedene Variablen (ohne die Variable pi). Tipp: Verwenden Sie
````matlab 
doc pi
````
als Startpunkt für Ihre Recherche.

### Übung 6
Definieren Sie sich verschiedene Variablen a, b und c, mit einem Wert von 127.5, jeweils mit
verschiedenen Datentypen, int8, int16 und double, z.B. Welchen Einfluss hat der Datentyp auf das Ergebnis?


```matlab
a = int8(127.5)
int8(127.5)
int16(127.5)
double(127.5)
```




<html><body><pre>a = int8
   127
</pre></body></html>






<html><body><pre>ans = int8
   127
</pre></body></html>






<html><body><pre>ans = int16
   128
</pre></body></html>






<html><body><pre>ans = 
     1.275000000000000e+02
</pre></body></html>



### Übung 7
Initialisieren Sie selber verschiedene Variablen mit beliebigen Werten und zeigen Sie in fünf verschiedenen
Beispielen, dass Sie den Umgang mit verschiedenen Rechenoperatoren beherrschen.
Nutzen Sie dabei auch die Variable ans, z.B.

````Matlab
>>a = int8 (3);
>>b = 9;
>>a + b;
>>c = int8 (ans /9);
````

Verwenden Sie in Ihren Beispielen auch die Eulersche Zahl e. Achten Sie auf die korrekte Verwendung
von Datentypen.


```matlab
a = 2;
a1 = int8(a)
b = 5;
a + b
c = a / b
c1 = a1 / b
c12 = b / a
c11 = b / a1
c2 = 2 *log (exp(1))
d = exp(-i*pi/4)
```




<html><body><pre>a1 = int8
2</pre></body></html>






<html><body><pre>ans = 7</pre></body></html>






<html><body><pre>c = 0.4000</pre></body></html>






<html><body><pre>c1 = int8
0</pre></body></html>






<html><body><pre>c12 = 2.5000</pre></body></html>






<html><body><pre>c11 = int8
3</pre></body></html>






<html><body><pre>c2 = 2</pre></body></html>






<html><body><pre>d = 0.7071 - 0.7071i</pre></body></html>



### Übung 8
Bestimmen Sie den exakten Wert von tan(60°).


```matlab
tan(deg2rad(60))
tand(60)
```




<html><body><pre>ans = 1.7321</pre></body></html>






<html><body><pre>ans = 1.7321</pre></body></html>



### Übung 9
Berechne zu einem beliebigen Kreisradius r, welcher als Variable definiert werden soll, die Fläche
A und den Umfang U des Kreises, durch die Verwendung der Variable r.


```matlab
r  = 3;
% Area of a circle
A = pi * r^2
% Circumference of a circle
U = 2 * pi * r
```




<html><body><pre>A = 28.2743</pre></body></html>






<html><body><pre>U = 18.8496</pre></body></html>



### Übung 10
Fur ein rechtwinkliges Dreieck, Abbildung A.1, gilt b = 2,53 cm und c = 3,88 cm. Berechnen Sie
die Winkel α und β sowie die Langen a und hc.

![Rechtwinkliges Dreieck](./assets/images/rechtDreieck.bmp)


```matlab
b = 2.53;
c = 3.88;
%The length of a
a = sqrt(c^2 - b^2)
% The angle α between c and b
alpha = rad2deg(acos(b/c))
alpha = acosd (b/c)
% The angle β between a and b
beta = acosd (a/c)
%The height h of the triangle
h = b * sind(alpha)
h = a * sind(beta)
```




<html><body><pre>a = 
   2.941683191643859
</pre></body></html>






<html><body><pre>alpha = 
  49.302762059203360
</pre></body></html>






<html><body><pre>alpha = 
  49.302762059203353
</pre></body></html>






<html><body><pre>beta = 
  40.697237940796640
</pre></body></html>






<html><body><pre>h = 
   1.918159400736846
</pre></body></html>






<html><body><pre>h = 
   1.918159400736846
</pre></body></html>



### Übung 11
Berechnen Sie den Betrag der komplexen Zahl c = 5 − 3i. Verwenden Sie dazu die Formel
$|c| = √(Real(c)^2 + Imag(c)^2)$. Erstellen Sie zur Kontrolle eine alternative Implementierung mit
dem Befehl abs.


```matlab
c = 5 - 3i
% The module of c
modulus_c = sqrt(real(c)^2 + imag(c)^2)
% The module of c using abs function
modulus_c = abs(c)
```




<html><body><pre>c = 
  5.000000000000000 - 3.000000000000000i
</pre></body></html>






<html><body><pre>modulus_c = 
   5.830951894845301
</pre></body></html>






<html><body><pre>modulus_c = 
   5.830951894845301
</pre></body></html>



### Übung 12
Berechnen Sie den Cosinus einer komplexen Zahl z, wobei der Real- und Imaginärteil von z
ganzzahlige, gleichverteilte Zufallszahlen zwischen 1 und 6 sind. Verwenden Sie dabei die Formel
$cos(z) = (e^{(iz)}+e^{(−iz)})/2$ . Erstellen Sie zur Kontrolle eine alternative Implementierung mit dem Befehl
cos.


```matlab
real_z= randi(6)
imag_z= randi(6)
z = complex(real_z, imag_z)
%cos of z
cos_z1 = (exp(i * z) + exp(-i * z)) / 2
cos_z = cos(z)
```




<html><body><pre>real_z = 
     5
</pre></body></html>






<html><body><pre>imag_z = 
     3
</pre></body></html>






<html><body><pre>z = 
  5.000000000000000 + 3.000000000000000i
</pre></body></html>






<html><body><pre>cos_z1 = 
  2.855815004227387 + 9.606383448432581i
</pre></body></html>






<html><body><pre>cos_z = 
  2.855815004227387 + 9.606383448432581i
</pre></body></html>



### Übung 13
Bestimmen Sie für die Funktion f(x) = log(4^x) + log(3^x) + log(2^x) den Funktionswert an der
Stelle x = 1,57 und runden Sie diesen auf zwei Nachkommastellen.


```matlab
x = 1.57;
f_x = log10(4^x) + log10(3^x) + log10(2^x)
% Runden auf zwei Nachkommastellen
f_x_rounded = round(f_x, 2)
% Zwei Dezimalstellen zeigen
fprintf('%.2f\n', f_x)
```




<html><body><pre>f_x = 
   2.166931649487221
</pre></body></html>






<html><body><pre>f_x_rounded = 
   2.170000000000000
</pre></body></html>



    2.17
    

### Übung 14
Die Temperatur eines 50 °C heißen Körpers sinkt innerhalb einer Stunde jeweils auf die Hälfte ihres
Wertes. Der Abkühlungsprozess wird beschrieben durch T = 50 °C * (1/2)^t.

a. Welche Temperatur hat der Körper 8 Stunden nach Beginn des Abkühlungsvorganges?

b. Nach welcher Zeit beträgt die Temperatur des Körpers 1 °C?


```matlab
t = 8;
% Körpertemperatur nach t Stunden
T = 50 * 0.5 ^ t
% Zeitpunkt t, an dem die Temperatur 1 Grad erreicht
t_1 = log(1/50) / log(0.5)

```




<html><body><pre>T = 
   0.195312500000000
</pre></body></html>






<html><body><pre>t_1 = 
   5.643856189774724
</pre></body></html>



### Übung 15
Die Andler-Formel ermittelt die optimale Bestellmenge bx für das statische Losgrößenmodell. In
diesem Modell werden die Lagerkosten den Bestellkosten gegenübergestellt. Die Andler-Formel
lautet

x̂ = √(2Fm/l)

Bestimmen Sie die optimale Bestellmenge für die Bestellkosten F = 50 €, den Lagerkostensatz
l = 0.8 € pro Stück und einen mittleren Monatsbedarf von m = 150 Stück. Berechnen Sie
die prozentuale Änderung der optimalen Bestellmenge wenn sich die Bestellkosten verdoppeln
bzw. halbieren.


```matlab
F = 50; %ordering cost
l = 0.8; % holding cost per unit per month
m = 150; % 
x = sqrt(2*F*m/l); % optimal ordering quantity
x_F_doppel = sqrt(4*F*m/l); % optimal ordering quantity with double the fixed cost
x_F_mid = sqrt(F*m/l); % optimal ordering quantity with half the fixed cost

pro_cent_doppel = 100 * (x_F_doppel - x) / x; % percentage increase in optimal ordering quantity with double the fixed cost
pro_cent_mid = 100 * (x_F_mid - x) / x; % percentage increase in optimal ordering quantity with half the fixed cost
fprintf('The optimal ordering quantity is: %.2f\n', x);
fprintf('The optimal ordering quantity with double the ordering cost is: %.2f\n', x_F_doppel);
fprintf('The optimal ordering quantity with half the ordering cost is: %.2f\n', x_F_mid);
```

    The optimal ordering quantity is: 136.93
    The optimal ordering quantity with double the ordering cost is: 193.65
    The optimal ordering quantity with half the ordering cost is: 96.82
    


```matlab

```
