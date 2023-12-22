# Códigos para Sintonización Óptima de Control Automático de Generación 

![GRAPHICAL_Abstract_8475](https://github.com/jenriquezq/IEEE_OptimalTuningAGC/assets/72208683/74bc0d41-dd44-4165-bded-5cf059fd2416)

1. **Códigos de MATLAB**:
   1. `main.m`. Script principal para lectura de archivos de Excel con registros para: lógica de no seguimiento, lógica de limitación de rampa y lógica de control del sistema (lógica de filtrado del ACE).
   2. `MVMO_Configuration.m`. Script para seleccionar la función objetivo, establecer límites de las variables de optimización y definir los parámetros del algoritmo MVMO.
   3. `MVMO_old_nakawiro.m`. Es una función llamada por el script `MVMO_Configuration.m`. Esta función permite correr el algoritmo de optimización MVMO. 
   4. `Objective_Function.m`. Es una función llamada por la función `MVMO_old_nakawiro.m`. Contiene las funciones objetivo y restricciones para: lógica de no seguimiento, lógica de limitación de rampa y lógica de control del sistema (lógica de filtrado del ACE). 
   5. `elitism.m`. Es una función llamada por la función `MVMO_old_nakawiro.m`. Función que permite identificar si la solución actual es mejor que la solución anterior.
   6. `tracking_logic.m`. Script que permite simular la lógica de no seguimiento.
   7. `rate_limiting_logic.m`. Script que permite simular la lógica de limitación de rampa.
   8. `face_logic.m`. Script que permite simular la lógica de control del sistema (lógica de filtrado del ACE).
2. **Archivos Excel**:
   1. `parametros_originales_Molino.xlsx`: Este archivo contiene los registros de Potencia Real (medida) y Potencia Deseada (calculada por AGC) para una unidad de la central Molino. Estos registros fueron obtenidos de OTS (Simulador de Entrenamiento de Operadores).
   2. `parametros_originales_FACE.xlsx`: Este archivo contiene los registros de ACE crudo (calculado por AGC). Estos registros fueron obtenidos de OTS.

# Instrucciones para correr scripts:
1. Abrir `main.m`. En la variable `option` digitar una de las siguientes opciones:
   1. `1`: Para escoger los registros de Potencia Real (medida) y Potencia Deseada (calculada por AGC) para unidad con rampa de subida.
      > **NOTA** Esta opción es válida para la lógica de no seguimiento y lógica de limitación de rampa. 
   3. `2`: Para escoger los registros de Potencia Real (medida) y Potencia Deseada (calculada por AGC) para unidad con rampa de bajada. 
      > **NOTA** Esta opción es válida para la lógica de no seguimiento y lógica de limitación de rampa.
   5. `3`: Para escoger los registros de ACE crudo. 
      > **NOTA** Esta opción es válida para la lógica de control del sistema (lógica de filtrado del ACE).
      
      > Para este caso se debe ingresar el valor de la variable `const1` que es el valor de suavizado que se mantendrá constante durante la optimización de la precisión (restricción de la lógica de filtrado del ACE).
2. Ejecutar `main.m`.
3. Abrir `MVMO_Configuration.m`. En la variable `iss` digitar una las siguientes opciones:
   1. `1`: Para escoger la función objetivo de la lógica de no seguimiento.
   2. `2`: Para escoger la función objetivo de la lógica de limitación de rampa.
   3. `3`: Para escoger la función objetivo de la lógica de control del sistema (lógica de filtrado del ACE).
4. Ejecutar `MVMO_Configuration.m`.
4. Correr el script `tracking_logic.m` para simular los resultados de la lógica de no seguimiento.
   > **NOTA** Ingresar los parámetros óptimos en las variables `T1` y `T2`.
6. Correr el script `rate_limiting_logic.m` para simular los resultados de la lógica de limitación de rampa.
   > **NOTA** Ingresar los parámetros óptimos en las variables `T3` y `T4`.
8. Correr el script `face_logic.m` para simular los resultados de la lógica de control del sistema (lógica de filtrado del ACE).
   > **NOTA** Ingresar los parámetros óptimos en las variables `win_size` (n) y `XWMATC` (T).


