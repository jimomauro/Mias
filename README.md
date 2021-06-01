# Mias
Codigo desarrollo personal Oracle


CREATE TABLE GCCO_INH_ASCARD_DIARIO  AS (
SELECT ROW_NUMBER() OVER (ORDER BY date DESC) ID_TERADATA,
A.NUMERO_CREDITO, 
A.CUSTCODE_DEL_SERVICIO, 
B.NUMERO_IDENTIFICACION, 
A.SALDO_FINANCIAR, 
A.FECHA_CREACION,
A.TIPO_PROCESO, 
A.IMEI, 
A.REFERENCIA_EQUIPO, 
B.CIUDAD, 
B.DEPARTAMENTO, 
A.CUOTAS_PACTADAS, 
A.CODIGO_DISTRIBUIDOR, 
B.TIPO_IDENTIFICACION, 
C.FECHA_ACTIVACION_BSCS, 
C.COMPORTAMIENTO_PAGO,
J.CREDITO EXTRANET_ACTIVACIONES,
E.PRODUCTO EXTRANET_CREDITO,
F.RATINGCREDIT POLIEXP_REPOS,
G.RATINGCREDIT POLIEXP_TECNO,
D.CALIFICACION_FINAL PERFILAMIENTO,
CASE WHEN J.CREDITO = 'E - Postpago.' THEN 'E'
     WHEN J.CREDITO = 'A - Postpago.' THEN 'A'
     WHEN J.CREDITO = 'B - Postpago.' THEN 'B'
     WHEN E.PRODUCTO = 'E - Postpago.' THEN 'E'
     WHEN E.PRODUCTO = 'A - Postpago.' THEN 'A'
     WHEN E.PRODUCTO = 'B - Postpago.' THEN 'B'
     WHEN F.RATINGCREDIT = 'E - Postpago.' THEN 'E'
     WHEN F.RATINGCREDIT = 'A - Postpago.' THEN 'A'
     WHEN F.RATINGCREDIT = 'B - Postpago.' THEN 'B'     
     WHEN G.RATINGCREDIT = 'E - Postpago.' THEN 'E'
     WHEN G.RATINGCREDIT = 'A - Postpago.' THEN 'A'
     WHEN G.RATINGCREDIT = 'B - Postpago.' THEN 'B'     
     WHEN D.CALIFICACION_FINAL = 'E' AND J.CREDITO IS NULL THEN 'E'
     WHEN D.CALIFICACION_FINAL = 'A' AND J.CREDITO IS NULL THEN 'A'
     WHEN D.CALIFICACION_FINAL = 'B' AND J.CREDITO IS NULL THEN 'B'
     WHEN D.CALIFICACION_FINAL = 'C' AND J.CREDITO IS NULL THEN 'SCD'
     WHEN D.CALIFICACION_FINAL = 'P' AND J.CREDITO IS NULL THEN 'SCD'       
     WHEN D.CALIFICACION_FINAL = 'E' AND E.PRODUCTO IS NULL THEN 'E'
     WHEN D.CALIFICACION_FINAL = 'A' AND E.PRODUCTO IS NULL THEN 'A'
     WHEN D.CALIFICACION_FINAL = 'B' AND E.PRODUCTO IS NULL THEN 'B'
     WHEN D.CALIFICACION_FINAL = 'C' AND E.PRODUCTO IS NULL THEN 'SCD'
     WHEN D.CALIFICACION_FINAL = 'P' AND E.PRODUCTO IS NULL THEN 'SCD'     
     WHEN D.CALIFICACION_FINAL = 'E' AND F.RATINGCREDIT IS NULL THEN 'E'
     WHEN D.CALIFICACION_FINAL = 'A' AND F.RATINGCREDIT IS NULL THEN 'A'
     WHEN D.CALIFICACION_FINAL = 'B' AND F.RATINGCREDIT IS NULL THEN 'B'
     WHEN D.CALIFICACION_FINAL = 'C' AND F.RATINGCREDIT IS NULL THEN 'SCD'
     WHEN D.CALIFICACION_FINAL = 'P' AND F.RATINGCREDIT IS NULL THEN 'SCD'     
     WHEN D.CALIFICACION_FINAL = 'E' AND G.RATINGCREDIT IS NULL THEN 'E'
     WHEN D.CALIFICACION_FINAL = 'A' AND G.RATINGCREDIT IS NULL THEN 'A'
     WHEN D.CALIFICACION_FINAL = 'B' AND G.RATINGCREDIT IS NULL THEN 'B'
     WHEN D.CALIFICACION_FINAL = 'C' AND G.RATINGCREDIT IS NULL THEN 'SCD'
     WHEN D.CALIFICACION_FINAL = 'P' AND G.RATINGCREDIT IS NULL THEN 'SCD'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND E.PRODUCTO = 'E - Postpago.' THEN 'E'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND E.PRODUCTO = 'A - Postpago.' THEN 'A'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND E.PRODUCTO = 'B - Postpago.' THEN 'B'     
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND G.RATINGCREDIT = 'E - Postpago.' THEN 'E'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND G.RATINGCREDIT = 'A - Postpago.' THEN 'A'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND G.RATINGCREDIT = 'B - Postpago.' THEN 'B'
     WHEN D.CALIFICACION_FINAL =  'A' THEN 'A'
     WHEN D.CALIFICACION_FINAL =  'B' THEN 'B'
     WHEN D.CALIFICACION_FINAL =  'C' THEN 'SCD'
     WHEN D.CALIFICACION_FINAL =  'P' THEN 'SCD'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
     WHEN E.PRODUCTO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
     WHEN G.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'E' THEN 'E'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'A' THEN 'A'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'B' THEN 'B'     
     WHEN E.PRODUCTO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'E' THEN 'E'
     WHEN E.PRODUCTO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'A' THEN 'A'
     WHEN E.PRODUCTO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'B' THEN 'B'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'E' THEN 'E'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'A' THEN 'A'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'B' THEN 'B'
     WHEN G.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'E' THEN 'E'
     WHEN G.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'A' THEN 'A'
     WHEN G.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'B' THEN 'B'
     WHEN J.CREDITO IS NULL AND G.RATINGCREDIT IS NULL AND F.RATINGCREDIT IS NULL AND G.RATINGCREDIT IS NULL AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
END CALIFICACION,
CASE WHEN J.CREDITO = 'E - Postpago.' THEN 'EXTRANET_ACTIVACIONES'
     WHEN J.CREDITO = 'A - Postpago.' THEN 'EXTRANET_ACTIVACIONES'
     WHEN J.CREDITO = 'B - Postpago.' THEN 'EXTRANET_ACTIVACIONES'
     WHEN E.PRODUCTO = 'E - Postpago.' THEN 'EXTRANET_CREDITO'
     WHEN E.PRODUCTO = 'A - Postpago.' THEN 'EXTRANET_CREDITO'
     WHEN E.PRODUCTO = 'B - Postpago.' THEN 'EXTRANET_CREDITO'
     WHEN F.RATINGCREDIT = 'E - Postpago.' THEN 'POLIEXP_REPOS'
     WHEN F.RATINGCREDIT = 'A - Postpago.' THEN 'POLIEXP_REPOS'
     WHEN F.RATINGCREDIT = 'B - Postpago.' THEN 'POLIEXP_REPOS'     
     WHEN G.RATINGCREDIT = 'E - Postpago.' THEN 'POLIEXP_TECNO'
     WHEN G.RATINGCREDIT = 'A - Postpago.' THEN 'POLIEXP_TECNO'
     WHEN G.RATINGCREDIT = 'B - Postpago.' THEN 'POLIEXP_TECNO'     
     WHEN D.CALIFICACION_FINAL = 'E' AND J.CREDITO IS NULL THEN 'PERFILADO'
     WHEN D.CALIFICACION_FINAL = 'A' AND J.CREDITO IS NULL THEN 'PERFILADO'
     WHEN D.CALIFICACION_FINAL = 'B' AND J.CREDITO IS NULL THEN 'PERFILADO'
     WHEN D.CALIFICACION_FINAL = 'C' AND J.CREDITO IS NULL THEN 'SCD'
     WHEN D.CALIFICACION_FINAL = 'P' AND J.CREDITO IS NULL THEN 'SCD'       
     WHEN D.CALIFICACION_FINAL = 'E' AND E.PRODUCTO IS NULL THEN 'PERFILADO'
     WHEN D.CALIFICACION_FINAL = 'A' AND E.PRODUCTO IS NULL THEN 'PERFILADO'
     WHEN D.CALIFICACION_FINAL = 'B' AND E.PRODUCTO IS NULL THEN 'PERFILADO'
     WHEN D.CALIFICACION_FINAL = 'C' AND E.PRODUCTO IS NULL THEN 'SCD'
     WHEN D.CALIFICACION_FINAL = 'P' AND E.PRODUCTO IS NULL THEN 'SCD'     
     WHEN D.CALIFICACION_FINAL = 'E' AND F.RATINGCREDIT IS NULL THEN 'PERFILADO'
     WHEN D.CALIFICACION_FINAL = 'A' AND F.RATINGCREDIT IS NULL THEN 'PERFILADO'
     WHEN D.CALIFICACION_FINAL = 'B' AND F.RATINGCREDIT IS NULL THEN 'PERFILADO'
     WHEN D.CALIFICACION_FINAL = 'C' AND F.RATINGCREDIT IS NULL THEN 'SCD'
     WHEN D.CALIFICACION_FINAL = 'P' AND F.RATINGCREDIT IS NULL THEN 'SCD'     
     WHEN D.CALIFICACION_FINAL = 'E' AND G.RATINGCREDIT IS NULL THEN 'PERFILADO'
     WHEN D.CALIFICACION_FINAL = 'A' AND G.RATINGCREDIT IS NULL THEN 'PERFILADO'
     WHEN D.CALIFICACION_FINAL = 'B' AND G.RATINGCREDIT IS NULL THEN 'PERFILADO'
     WHEN D.CALIFICACION_FINAL = 'C' AND G.RATINGCREDIT IS NULL THEN 'SCD'
     WHEN D.CALIFICACION_FINAL = 'P' AND G.RATINGCREDIT IS NULL THEN 'SCD'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND E.PRODUCTO = 'E - Postpago.' THEN 'EXTRANET_CREDITO'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND E.PRODUCTO = 'A - Postpago.' THEN 'EXTRANET_CREDITO'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND E.PRODUCTO = 'B - Postpago.' THEN 'EXTRANET_CREDITO'     
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND G.RATINGCREDIT = 'E - Postpago.' THEN 'POLIEXP_TECNO'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND G.RATINGCREDIT = 'A - Postpago.' THEN 'POLIEXP_TECNO'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND G.RATINGCREDIT = 'B - Postpago.' THEN 'POLIEXP_TECNO'
     WHEN D.CALIFICACION_FINAL =  'A' THEN 'PERFILADO'
     WHEN D.CALIFICACION_FINAL =  'B' THEN 'PERFILADO'
     WHEN D.CALIFICACION_FINAL =  'C' THEN 'SCD'
     WHEN D.CALIFICACION_FINAL =  'P' THEN 'SCD'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
     WHEN E.PRODUCTO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
     WHEN G.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'E' THEN 'PERFILADO'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'A' THEN 'PERFILADO'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'B' THEN 'PERFILADO'     
     WHEN E.PRODUCTO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'E' THEN 'PERFILADO'
     WHEN E.PRODUCTO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'A' THEN 'PERFILADO'
     WHEN E.PRODUCTO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'B' THEN 'PERFILADO'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'E' THEN 'PERFILADO'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'A' THEN 'PERFILADO'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'B' THEN 'PERFILADO'
     WHEN G.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'E' THEN 'PERFILADO'
     WHEN G.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'A' THEN 'PERFILADO'
     WHEN G.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'B' THEN 'PERFILADO'
     WHEN J.CREDITO IS NULL AND G.RATINGCREDIT IS NULL AND F.RATINGCREDIT IS NULL AND G.RATINGCREDIT IS NULL AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
END TIPO,
CASE WHEN J.CREDITO = 'E - Postpago.' THEN 'BURO'
     WHEN J.CREDITO = 'A - Postpago.' THEN 'BURO'
     WHEN J.CREDITO = 'B - Postpago.' THEN 'BURO'
     WHEN E.PRODUCTO = 'E - Postpago.' THEN 'BURO'
     WHEN E.PRODUCTO = 'A - Postpago.' THEN 'BURO'
     WHEN E.PRODUCTO = 'B - Postpago.' THEN 'BURO'
     WHEN F.RATINGCREDIT = 'E - Postpago.' THEN 'BURO'
     WHEN F.RATINGCREDIT = 'A - Postpago.' THEN 'BURO'
     WHEN F.RATINGCREDIT = 'B - Postpago.' THEN 'BURO'     
     WHEN G.RATINGCREDIT = 'E - Postpago.' THEN 'BURO'
     WHEN G.RATINGCREDIT = 'A - Postpago.' THEN 'BURO'
     WHEN G.RATINGCREDIT = 'B - Postpago.' THEN 'BURO'     
     WHEN D.CALIFICACION_FINAL = 'E' AND J.CREDITO IS NULL THEN 'PERFILAMIENTO'
     WHEN D.CALIFICACION_FINAL = 'A' AND J.CREDITO IS NULL THEN 'PERFILAMIENTO'
     WHEN D.CALIFICACION_FINAL = 'B' AND J.CREDITO IS NULL THEN 'PERFILAMIENTO'
     WHEN D.CALIFICACION_FINAL = 'C' AND J.CREDITO IS NULL THEN 'SCD'
     WHEN D.CALIFICACION_FINAL = 'P' AND J.CREDITO IS NULL THEN 'SCD'       
     WHEN D.CALIFICACION_FINAL = 'E' AND E.PRODUCTO IS NULL THEN 'PERFILAMIENTO'
     WHEN D.CALIFICACION_FINAL = 'A' AND E.PRODUCTO IS NULL THEN 'PERFILAMIENTO'
     WHEN D.CALIFICACION_FINAL = 'B' AND E.PRODUCTO IS NULL THEN 'PERFILAMIENTO'
     WHEN D.CALIFICACION_FINAL = 'C' AND E.PRODUCTO IS NULL THEN 'SCD'
     WHEN D.CALIFICACION_FINAL = 'P' AND E.PRODUCTO IS NULL THEN 'SCD'     
     WHEN D.CALIFICACION_FINAL = 'E' AND F.RATINGCREDIT IS NULL THEN 'PERFILAMIENTO'
     WHEN D.CALIFICACION_FINAL = 'A' AND F.RATINGCREDIT IS NULL THEN 'PERFILAMIENTO'
     WHEN D.CALIFICACION_FINAL = 'B' AND F.RATINGCREDIT IS NULL THEN 'PERFILAMIENTO'
     WHEN D.CALIFICACION_FINAL = 'C' AND F.RATINGCREDIT IS NULL THEN 'SCD'
     WHEN D.CALIFICACION_FINAL = 'P' AND F.RATINGCREDIT IS NULL THEN 'SCD'     
     WHEN D.CALIFICACION_FINAL = 'E' AND G.RATINGCREDIT IS NULL THEN 'PERFILAMIENTO'
     WHEN D.CALIFICACION_FINAL = 'A' AND G.RATINGCREDIT IS NULL THEN 'PERFILAMIENTO'
     WHEN D.CALIFICACION_FINAL = 'B' AND G.RATINGCREDIT IS NULL THEN 'PERFILAMIENTO'
     WHEN D.CALIFICACION_FINAL = 'C' AND G.RATINGCREDIT IS NULL THEN 'SCD'
     WHEN D.CALIFICACION_FINAL = 'P' AND G.RATINGCREDIT IS NULL THEN 'SCD'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND E.PRODUCTO = 'E - Postpago.' THEN 'BURO'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND E.PRODUCTO = 'A - Postpago.' THEN 'BURO'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND E.PRODUCTO = 'B - Postpago.' THEN 'BURO'     
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND G.RATINGCREDIT = 'E - Postpago.' THEN 'BURO'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND G.RATINGCREDIT = 'A - Postpago.' THEN 'BURO'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND G.RATINGCREDIT = 'B - Postpago.' THEN 'BURO'
     WHEN D.CALIFICACION_FINAL =  'A' THEN 'PERFILAMIENTO'
     WHEN D.CALIFICACION_FINAL =  'B' THEN 'PERFILAMIENTO'
     WHEN D.CALIFICACION_FINAL =  'C' THEN 'SCD'
     WHEN D.CALIFICACION_FINAL =  'P' THEN 'SCD'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
     WHEN E.PRODUCTO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
     WHEN G.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'E' THEN 'PERFILAMIENTO'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'A' THEN 'PERFILAMIENTO'
     WHEN J.CREDITO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'B' THEN 'PERFILAMIENTO'     
     WHEN E.PRODUCTO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'E' THEN 'PERFILAMIENTO'
     WHEN E.PRODUCTO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'A' THEN 'PERFILAMIENTO'
     WHEN E.PRODUCTO IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'B' THEN 'PERFILAMIENTO'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'E' THEN 'PERFILAMIENTO'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'A' THEN 'PERFILAMIENTO'
     WHEN F.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'B' THEN 'PERFILAMIENTO'
     WHEN G.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'E' THEN 'PERFILAMIENTO'
     WHEN G.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'A' THEN 'PERFILAMIENTO'
     WHEN G.RATINGCREDIT IN ('D - Postpago.','C - Postpago.','P - Prepago.','5 - Postpago Tipo 5.','7 - Postpago Tipo 7.','Act. Sin Est. Credito - 7','Act. Sin estudio crediticio') AND D.CALIFICACION_FINAL = 'B' THEN 'PERFILAMIENTO'
     WHEN J.CREDITO IS NULL AND G.RATINGCREDIT IS NULL AND F.RATINGCREDIT IS NULL AND G.RATINGCREDIT IS NULL AND D.CALIFICACION_FINAL IS NULL THEN 'SCD'
END TIPO_REAL,
TO_CHAR(A.FECHA_CREACION, 'YYYYMMDD') A_MES_SERV,
TO_CHAR(A.FECHA_CREACION, 'YYYYMM') AMES,
TO_CHAR(A.FECHA_CREACION, 'DD') DIA,
CASE WHEN A.SALDO_FINANCIAR <= '169999' THEN '00 < 170.000'
     WHEN A.SALDO_FINANCIAR >= '170000' AND A.SALDO_FINANCIAR <= '299999' THEN '01 170.000 A 299.999'
     WHEN A.SALDO_FINANCIAR >= '300000' AND A.SALDO_FINANCIAR <= '399999' THEN '02 300.000 A 399.999'
     WHEN A.SALDO_FINANCIAR >= '400000' AND A.SALDO_FINANCIAR <= '499999' THEN '03 400.000 A 499.999'
     WHEN A.SALDO_FINANCIAR >= '500000' AND A.SALDO_FINANCIAR <= '599999' THEN '04 500.000 A 599.999'
     WHEN A.SALDO_FINANCIAR >= '600000' AND A.SALDO_FINANCIAR <= '699999' THEN '06 600.000 A 699.999'
     WHEN A.SALDO_FINANCIAR >= '700000' AND A.SALDO_FINANCIAR <= '759999' THEN '07 700.000 A 759.999'
     WHEN A.SALDO_FINANCIAR >= '760000' AND A.SALDO_FINANCIAR <= '899999' THEN '08 760.000 A 899.999'
     WHEN A.SALDO_FINANCIAR >= '900000' AND A.SALDO_FINANCIAR <= '999999' THEN '09 900.000 A 999.999'
     WHEN A.SALDO_FINANCIAR >= '1000000' AND A.SALDO_FINANCIAR <= '1199999' THEN '10 1.000.000 A 1.199.999'
     WHEN A.SALDO_FINANCIAR >= '1200000' AND A.SALDO_FINANCIAR <= '1399999' THEN '11 1.200.000 A 1.399.999'
     WHEN A.SALDO_FINANCIAR >= '1400000' AND A.SALDO_FINANCIAR <= '1999999' THEN '12 1.400.000 A 1.999.999'
     WHEN A.SALDO_FINANCIAR >= '2000000' AND A.SALDO_FINANCIAR <= '3999999' THEN '13 2.000.000 A 3.999.999'
     WHEN A.SALDO_FINANCIAR >= '4000000' THEN '14 >= 4.000.000'
END RANGO,
CASE WHEN A.SALDO_FINANCIAR <= '169999' THEN '1 ULTRA_BAJA'
     WHEN A.SALDO_FINANCIAR >= '170000' AND A.SALDO_FINANCIAR <= '299999' THEN '2 BAJA'
     WHEN A.SALDO_FINANCIAR >= '300000' AND A.SALDO_FINANCIAR <= '399999' THEN '2 BAJA'
     WHEN A.SALDO_FINANCIAR >= '400000' AND A.SALDO_FINANCIAR <= '499999' THEN '3 MEDIA'
     WHEN A.SALDO_FINANCIAR >= '500000' AND A.SALDO_FINANCIAR <= '599999' THEN '3 MEDIA'
     WHEN A.SALDO_FINANCIAR >= '600000' AND A.SALDO_FINANCIAR <= '699999' THEN '3 MEDIA'
     WHEN A.SALDO_FINANCIAR >= '700000' AND A.SALDO_FINANCIAR <= '759999' THEN '3 MEDIA'
     WHEN A.SALDO_FINANCIAR >= '760000' AND A.SALDO_FINANCIAR <= '899999' THEN '4 ALTA'
     WHEN A.SALDO_FINANCIAR >= '900000' AND A.SALDO_FINANCIAR <= '999999' THEN '4 ALTA'
     WHEN A.SALDO_FINANCIAR >= '1000000' AND A.SALDO_FINANCIAR <= '1199999' THEN '4 ALTA'
     WHEN A.SALDO_FINANCIAR >= '1200000' AND A.SALDO_FINANCIAR <= '1399999' THEN '4 ALTA'
     WHEN A.SALDO_FINANCIAR >= '1400000' AND A.SALDO_FINANCIAR <= '1999999' THEN '5 PREMIUM'
     WHEN A.SALDO_FINANCIAR >= '2000000' AND A.SALDO_FINANCIAR <= '3999999' THEN '5 PREMIUM'
     WHEN A.SALDO_FINANCIAR >= '4000000' THEN '5 PREMIUM'
END GAMA,
CASE WHEN A.TIPO_PROCESO = '0' THEN 'VENTA'
     WHEN A.TIPO_PROCESO = '1' THEN 'KIT'
     WHEN A.TIPO_PROCESO = '2' THEN 'REPOSICION'
     WHEN A.TIPO_PROCESO = '3' THEN 'MOVIL_TECNOLOGIA'
     WHEN A.TIPO_PROCESO = '4' THEN 'MOVIL_TERMINALES'
     WHEN A.TIPO_PROCESO = '5' THEN 'FIJA_TECNOLOGIA'
     WHEN A.TIPO_PROCESO = '6' THEN 'FIJA_TERMINALES'
END TIPO_PROCESO_HOMO,
NVL (TRUNC (A.FECHA_CREACION) - TRUNC (C.FECHA_ACTIVACION_BSCS),0) DIAS_DIF,
CASE WHEN TRUNC (C.FECHA_ACTIVACION_BSCS) IS NULL THEN '1) 0 meses'
     WHEN TRUNC (A.FECHA_CREACION) - TRUNC (C.FECHA_ACTIVACION_BSCS) BETWEEN 0 AND 29 THEN '1) 0 meses'
     WHEN TRUNC (A.FECHA_CREACION) - TRUNC (C.FECHA_ACTIVACION_BSCS) BETWEEN 30 AND 180 THEN '2) 1 a 6 meses'
     WHEN TRUNC (A.FECHA_CREACION) - TRUNC (C.FECHA_ACTIVACION_BSCS) BETWEEN 181 AND 360 THEN '3) 7 a 12 meses'
     WHEN TRUNC (A.FECHA_CREACION) - TRUNC (C.FECHA_ACTIVACION_BSCS) BETWEEN 361 AND 720 THEN '4) 13 a 24 meses'
     WHEN TRUNC (A.FECHA_CREACION) - TRUNC (C.FECHA_ACTIVACION_BSCS) BETWEEN 721 AND 99999999 THEN '5) > 24 meses'
ELSE 'PENDIENTE'
END ANTIGUEDAD
from (SELECT *
       FROM CASOS_USO.V_GCCO_COB_CREDITO
       --WHERE TRUNC (FECHA_CREACION) >='2021-04-01'
       --AND TRUNC (FECHA_CREACION) <'2021-05-01'
        WHERE TRUNC (FECHA_CREACION) >=TO_DATE (TO_CHAR (ADD_MONTHS(DATE, - 0), 'YYYY-MM')||'-01', 'YYYY-MM-DD')
        ) A
INNER JOIN CASOS_USO.GCCO_COB_CLIENTES B
ON A.NUMERO_CREDITO = B.NUMERO_CREDITO
LEFT JOIN ( select *
            from CASOS_USO.GCCO_EXTRANET_ACTIVACIONES_ASCARD
            WHERE (NUMERO_DOCUMENTO, ID_TERADATA) IN (SELECT NUMERO_DOCUMENTO,MAX(ID_TERADATA)
            FROM CASOS_USO.GCCO_EXTRANET_ACTIVACIONES_ASCARD
            GROUP BY NUMERO_DOCUMENTO)
            ) J
ON B.NUMERO_IDENTIFICACION = J.NUMERO_DOCUMENTO
LEFT JOIN ( SELECT *
            FROM CASOS_USO.GCCO_LOGS_BURO
            WHERE (NUMERO_DOCUMENTO, ID_TERADATA) IN (SELECT NUMERO_DOCUMENTO,MAX(ID_TERADATA) FECHA_CONSULTA
            FROM CASOS_USO.GCCO_LOGS_BURO
            GROUP BY NUMERO_DOCUMENTO)
            ) E
ON B.NUMERO_IDENTIFICACION = E.NUMERO_DOCUMENTO
LEFT JOIN ( SELECT *
            FROM CASOS_USO.GCCO_POLIEXP_REPOS
            WHERE (DOCUMENTNUMBER, ID_TERADATA) IN ( SELECT DOCUMENTNUMBER,MAX(ID_TERADATA)
            FROM CASOS_USO.GCCO_POLIEXP_REPOS 
            GROUP BY DOCUMENTNUMBER)
            ) F
ON B.NUMERO_IDENTIFICACION = F.DOCUMENTNUMBER
LEFT JOIN ( SELECT *
            FROM CASOS_USO.GCCO_POLIEXP_TECNOLOGIA
            WHERE (DOCUMENTNUMBER, ID_TERADATA) IN (SELECT DOCUMENTNUMBER,MAX(ID_TERADATA)
            FROM CASOS_USO.GCCO_POLIEXP_TECNOLOGIA
            GROUP BY DOCUMENTNUMBER)
            ) G
ON B.NUMERO_IDENTIFICACION = G.DOCUMENTNUMBER
LEFT JOIN CASOS_USO.GCCO_PERFILAMIENTO_TOTAL D
ON B.NUMERO_IDENTIFICACION = D.IDENTIFICACION
LEFT JOIN CASOS_USO.V_GCCO_INH_SEG_BSCS_CLIENTES C
ON A.CUSTCODE_DEL_SERVICIO = C.CUSTCODE
)WITH DATA
