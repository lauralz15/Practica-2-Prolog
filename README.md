# Practica-2-Prolog
Catálogo de Vehículos en Prolog  
Autores: Laura Sofía Lizarazo y Juan José Sierra  

## Objetivos
- Implementar un catálogo de vehículos en Prolog.
- Consultar por presupuesto, marca, tipo y año.
- Generar reportes con límite de presupuesto total.

## Archivos incluidos
- `Practica22.pl`: código fuente en Prolog.
- Capturas de pantalla de los casos de prueba.
- `README.md`: explicación del proyecto.

## Predicados principales
- `cumple_presupuesto/2` → Filtra vehículos por presupuesto.
- `vehiculos_por_marca/2` → Lista vehículos de una marca.
- `vehiculos_por_tipo_fecha/3` → Agrupa vehículos por tipo y fecha.
- `generar_reporte/5` → Genera reportes con restricción de presupuesto.

## Casos de prueba

Caso 1: Toyota SUV < $30,000
```prolog
?- findall(Ref, (vehiculo(toyota, Ref, suv, Precio, _), Precio < 30000), R).
R = [rav4].
```

Caso 2: Nissan agrupados por tipo y año
```prolog
?- bagof((Tipo, Anio, Ref), vehiculo(nissan, Ref, Tipo, Precio, Anio), R).
R = [(sedan, 2023, sentra), (pickup, 2022, frontier), (deportivo, 2021, '370z')].
```

Caso 3: Sedanes sin superar $500,000
```prolog
?- findall((Ref, Precio), vehiculo(_, Ref, sedan, Precio, _), Vs),
   ordenar_por_precio(Vs, Ord),
   ajustar_inventario(Ord, 500000, Ajustados),
   sumar_precios(Ajustados, Total).
Vs = [(corolla, 24000), (civic, 25000), (sentra, 23000),
      (jetta, 26000), (mazda3, 24500), (serie3, 40000)],
Ajustados = [(sentra, 23000), (corolla, 24000), (civic, 25000),
             (mazda3, 24500), (jetta, 26000), (serie3, 40000)],
Total = 162500.
```




