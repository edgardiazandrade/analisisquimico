# Plataforma Pericial de Química Forense (ChemFlow / AnalisisQuimico)

Herramienta analítica e interactiva desarrollada para peritos químicos, analistas forenses y profesionales del laboratorio químico-legal. Facilita la toma de decisiones metodológicas en el análisis de sustancias controladas, modelando el comportamiento fisicoquímico de extracción líquido-líquido (L-L), la partición diferencial frente a adulterantes y sustancias de corte, el tamizaje presuntivo colorimétrico y la confirmación espectroscópica (FTIR y GC-MS).

---

## 🔬 Módulos y Capacidades Analíticas

### 1. Tamizaje y Batería Presuntiva (Árbol de Decisión Colorimétrico)
* **Algoritmo de descarte secuencial:** Recreación interactiva de las rutas analíticas de campo y laboratorio basadas en las series estandarizadas ODV / Sirchie:
  * Reactivo de Mayer (#901) para alcaloides y bases nitrogenadas.
  * Reactivo de Marquis (#902) con confirmación mediante Mecke (#924) para opiáceos y Simon's (#923) para metanfetamina/MDMA.
  * Prueba de Tiocianato de Cobalto / Scott (#904) con visualización de la secuencia trifásica para cocaína base y clorhidrato.
  * Pruebas para derivados no alcaloideos e indoles: Dille-Koppanyi (#905) y Reactivo de Ehrlich (#907).
  * Ensayos específicos para material vegetal y resinas: Duquenois-Levine (#908) con partición en capa clorofórmica y Reactivo KN (#909).
* **Fichas cromáticas estandarizadas:** Representación visual de los virajes mediante bloques de color con códigos HEX / Pantone y advertencias periciales sobre falsos positivos.

### 2. Fisicoquímica y Extracción Líquido-Líquido (L-L)
* **Ecuación de Henderson-Hasselbalch:** Modelado continuo del porcentaje de ionización en función del pH:
  $$\text{Ácidos débiles: } \%\,\text{Ionizado} = \frac{100}{1 + 10^{(pK_a - \text{pH})}}$$
  $$\text{Bases débiles: } \%\,\text{Ionizado} = \frac{100}{1 + 10^{(\text{pH} - pK_a)}}$$
* **Separación Diferencial Analito Objetivo vs. Sustancia de Corte:**
  * Superposición gráfica de curvas duales de ionización en el mismo plano cartesiano.
  * Marcadores interactivos sincronizados con el control de pH del medio extractor.
  * Cálculo algorítmico de la ventana de separación óptima ($\Delta\text{pH}$) para el aislamiento selectivo entre la sustancia de interés (ej. Cocaína) y adulterantes comunes (ej. Fenacetina, Cafeína, Levamisol).
* **Diagnóstico de Fase y Estructura Dinámica:** Determinación de predominio en fase acuosa (forma ionizada/sal) u orgánica (base/ácido libre), alternando dinámicamente las estructuras moleculares de referencia.

### 3. Confirmación Instrumental
* **Espectroscopía Infrarroja con Transformada de Fourier (FTIR):** Despliegue del espectro de absorción infrarroja con tabla analítica de bandas características ($P_1 - P_6 \text{ en cm}^{-1}$) y asignaciones vibracionales moleculares ($S_1 - S_6$).
* **Cromatografía de Gases acoplada a Espectrometría de Masas (GC-MS):** Presentación del perfil de fragmentación por impacto electrónico ($70\text{ eV}$), especificando la relación masa/carga ($m/z$) para el ion base, ion molecular y fragmentos diagnósticos ($I_1 - I_8$ / $D_1 - D_8$).

---

## 💻 Arquitectura Técnica

* **Framework de Interfaz:** Streamlit
* **Motor de Datos y Cálculo:** Python 3 nativo (`csv`, `math`, `os`, `re`, `json`). Diseñado para operar sin dependencias pesadas compiladas en C (`pandas`/`numpy`), garantizando total compatibilidad con directivas estrictas de seguridad (AppLocker / Smart App Control).
* **Renderizado Gráfico:** Altair y estilos CSS periciales integrados en modo laboratorio sobrio.

---

## 📁 Estructura del Repositorio

```text
analisisquimico/
│
├── app.py                                   # Aplicación principal de Streamlit
├── requirements.txt                         # Dependencias del proyecto
├── pH_vs_Ionizacion_Comparada_Datos.csv     # Base de datos analítica y fisicoquímica
├── README.md                                # Documentación pericial y técnica
│
└── Imágenes estructura/                     # Acervo iconográfico y espectroscópico
    ├── {sustancia}_base.png                 # Estructura molecular neutra
    ├── {sustancia}_ion.png                  # Estructura molecular ionizada/protonada
    ├── {sustancia}_Espectro_IR.png          # Espectro FTIR de referencia
    └── {sustancia}_GS-MS.png                # Espectro de masas GC-MS
```

---

## 🚀 Despliegue y Ejecución Local

### Requisitos Previos
* Python 3.9 o superior instalado.

### Instalación
1. Clonar el repositorio:
   ```bash
   git clone https://github.com/edgardiazandrade/analisisquimico.git
   cd analisisquimico
   ```

2. Crear y activar un entorno virtual:
   ```powershell
   # En Windows (PowerShell):
   python -m venv venv
   .\venv\Scripts\Activate.ps1

   # En Linux / macOS:
   python3 -m venv venv
   source venv/bin/activate
   ```

3. Instalar las dependencias mínimas:
   ```bash
   pip install -r requirements.txt
   ```

4. Ejecutar la plataforma localmente:
   ```bash
   streamlit run app.py
   ```

---

## 👨‍🔬 Autoría y Créditos

* **Desarrollo y Fundamentación Analítica:**  
  **QFB Edgar Oswaldo Díaz Andrade**  
  Química Forense y Toxicología Analítica

---

## 📚 Referencias Bibliográficas

1. Moffat AC, Osselton MD, Widdop B, Watts J, editores. *Clarke's Analysis of Drugs and Poisons: In pharmaceuticals, body fluids and postmortem material*. 4a ed. Londres: Pharmaceutical Press; 2011.
2. Oficina de las Naciones Unidas contra la Droga y el Delito (UNODC). *Métodos recomendados para el ensayo de drogas: Pruebas rápidas para la identificación de drogas de uso indebido e incautadas*. Manual para uso de los laboratorios nacionales de estupefacientes. Viena: Naciones Unidas; 1995.
3. National Center for Biotechnology Information (NCBI). *PubChem Compound Summary*. Bethesda (MD): National Library of Medicine (US); 2026.