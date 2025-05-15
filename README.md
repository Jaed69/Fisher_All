# Sistema de Evaluación de Personal para Empresa Constructora usando Coeficiente de Fisher y ANTLR4  

**Integrantes:**  
- Olivera Alvarez, Lizbeth Teresita - u201616851  
- Sihuincha Schermuly, Mireya Nicole - u20221a963  

**Curso:** Teoría de Compiladores (CC51)  
**Docente:** Peter Jonathan Montalvo Garcia  
**Universidad:** Universidad Peruana de Ciencias Aplicadas  
**Año:** 2025-01  

---

## 📌 Resumen  
Este proyecto desarrolla un sistema de evaluación de personal para empresas constructoras utilizando el **coeficiente de Fisher** (análisis discriminante) y **ANTLR4** para procesamiento estructurado de datos. Busca eliminar la subjetividad en evaluaciones, cuantificar el rendimiento laboral y reducir la rotación de personal mediante métricas objetivas y automatizadas.  

---

## 📖 Introducción  
Las empresas constructoras enfrentan desafíos en la evaluación de personal, como subjetividad en valoraciones y alta rotación laboral. Este sistema propone:  
- Un enfoque estadístico con el **coeficiente de Fisher** para identificar variables clave de desempeño.  
- Procesamiento automatizado con **ANTLR4** para garantizar consistencia en los datos.  
- Integración con sistemas de RRHH para generar recomendaciones objetivas (ascensos, despidos).  

---

## 🎯 Competencias del Curso  
- **Competencia General:** Manejo de la información y pensamiento crítico (Nivel de logro: 2).  
- **Competencia Específica (ABET 3):** Comunicación efectiva (Nivel de logro: 1).  

---

## ❓ Problemática y Motivación  
**Problemas identificados:**  
1. Subjetividad en evaluaciones de desempeño.  
2. Dificultad para cuantificar rendimiento en roles diversos.  
3. Alta rotación de personal y costos asociados.  
4. Impacto negativo en proyectos por decisiones incorrectas.  

**Solución propuesta:**  
- Sistema basado en datos con **análisis discriminante** (Fisher) y **procesamiento automatizado** (ANTLR4).  

---

## 🎯 Objetivos  
### Objetivo General  
Desarrollar un sistema de evaluación objetiva para personal constructor usando Fisher y ANTLR4.  

### Objetivos Específicos  
1. Cuantificar rendimiento laboral con métricas estandarizadas.  
2. Identificar variables discriminantes con Fisher.  
3. Automatizar procesamiento de datos con ANTLR4.  
4. Generar recomendaciones basadas en umbrales estadísticos.  
5. Visualizar resultados para transparencia en decisiones.  

---

## 📜 Gramática en ANTLR4  
### Diseño de la Gramática  
```antlr
grammar EmployeeEval;

// Reglas del Parser
program      : statement+ EOF ;
statement    : declaration | function | expr ';' ;
declaration  : TYPE ID '=' expr ';' ;
function     : FUNC TYPE ID '(' paramList? ')' block ;
paramList    : param (',' param)* ;
param        : TYPE ID ;
expr         : ID | NUMBER | STRING
             | expr ('+'|'-'|'*'|'/') expr
             | '(' expr ')'
             | 'mean' '(' expr (',' expr)* ')'
             | 'fisher' '(' expr (',' expr)* ')' ;
block        : '{' statement* '}' ;

// Reglas del Lexer
TYPE         : 'int' | 'float' | 'string' ;
FUNC         : 'func' ;
ID           : [a-zA-Z_][a-zA-Z_0-9]* ;
NUMBER       : [0-9]+ ('.' [0-9]+)? ;
STRING       : '"' .*? '"' ;
WS           : [ \t\r\n]+ -> skip ;
