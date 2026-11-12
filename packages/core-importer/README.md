# Motor de Importación Transaccional (packages/core-importer)
Lógica pura desacoplada en 5 fases:
1. Parser: PapaParse (CSV) y SheetJS (XLSX) con detección de encoding y delimitadores.
2. Mapper: Detección heurística de columnas con ajuste manual.
3. Normalizer & Validator: Sanitización de precios multiformato y reporte de errores por fila.
4. Differ: Comparación contra catálogo actual y alertas de variación porcentual.
5. Transactional Engine: Ejecución atómica en base de datos y snapshot para reversión (undo).
