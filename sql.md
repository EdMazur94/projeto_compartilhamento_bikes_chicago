# Consultas SQL – Como Transformar Usuários Casuais em Assinantes: Uma Análise de Dados do Sistema de Bicicletas Compartilhadas em Chicago

Este arquivo reúne as principais consultas SQL utilizadas durante a análise exploratória do sistema de bicicletas compartilhadas da cidade de Chicago. As consultas foram desenvolvidas no PgAdmin 4 utilizando PostgreSQL.

---

##  1. Criação da Tabela (Importação do CSV)

```sql
CREATE TABLE trips_07_2025 (
  ride_id TEXT,
  rideable_type TEXT,
  started_at TIMESTAMP,
  ended_at TIMESTAMP, 
  start_station_name TEXT, 
  start_station_id TEXT,
  end_station_name TEXT,
  end_station_id TEXT,
  start_lat DOUBLE PRECISION,
  start_lng DOUBLE PRECISION,
  end_lat DOUBLE PRECISION,
  end_lng DOUBLE PRECISION,
  member_casual TEXT
);
```
## 2. Consolidação dos Meses na Tabela all_trips

```sql
INSERT INTO all_trips SELECT * FROM trips_04_2024;
INSERT INTO all_trips SELECT * FROM trips_05_2024;
INSERT INTO all_trips SELECT * FROM trips_06_2024;
INSERT INTO all_trips SELECT * FROM trips_07_2024;
INSERT INTO all_trips SELECT * FROM trips_08_2024;
INSERT INTO all_trips SELECT * FROM trips_09_2024;
INSERT INTO all_trips SELECT * FROM trips_10_2024;
INSERT INTO all_trips SELECT * FROM trips_11_2024;
INSERT INTO all_trips SELECT * FROM trips_12_2024;
INSERT INTO all_trips SELECT * FROM trips_01_2025;
INSERT INTO all_trips SELECT * FROM trips_02_2025;
INSERT INTO all_trips SELECT * FROM trips_03_2025;
INSERT INTO all_trips SELECT * FROM trips_04_2025;
```
## 3. Análises Realizadas

### 3.1 Total de usuários por categoria (casual x assinante)

```sql
SELECT member_casual,
       COUNT(*) AS total_usuarios
FROM all_trips
GROUP BY member_casual;
```
### 3.2 Modelos de Bicicleta por tipo de usuário

```sql
SELECT rideable_type, 
       member_casual,
       COUNT(*) AS qtde_member_type
FROM all_trips
GROUP BY rideable_type, member_casual;
```
### 3.3 Média de Viagens por Dia por Tipo de Usuário

```sql
SELECT member_casual,
       ROUND(AVG(total_rides)::numeric) AS avg_rides_per_day
FROM (
    SELECT started_at::DATE AS date_travel,
           member_casual,
           COUNT(*) AS total_rides
    FROM all_trips
    GROUP BY started_at::DATE, member_casual
) AS daily_counts
GROUP BY member_casual
ORDER BY member_casual;
```
### 3.4 Tempo Médio de Viagem

```sql
SELECT member_casual,
       ROUND(AVG(EXTRACT(EPOCH FROM (ended_at - started_at))/60), 2) AS ride_length
FROM all_trips
GROUP BY member_casual;
```
### 3.5 Uso por Hora do Dia

```sql
SELECT EXTRACT(HOUR FROM started_at) AS hour,
       member_casual,
       COUNT(*) AS total
FROM all_trips
GROUP BY hour, member_casual
ORDER BY hour;
```
### 3.6 Sazonalidade: Uso por Mês

```sql
SELECT TO_CHAR(started_at, 'YYYY-MM') AS mes,
       member_casual,
       COUNT(*) AS total_viagens
FROM all_trips
GROUP BY mes, member_casual
ORDER BY mes;

```




.
