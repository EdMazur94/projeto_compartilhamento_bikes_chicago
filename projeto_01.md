# Como Transformar Usuários Casuais em Assinantes: Uma Análise de Dados do Sistema de Bicicletas Compartilhadas em Chicago

*O projeto em questão foi desenvolvido como parte do programa de Certificação Google Data Analytics Certificate. O objetivo é a aplicação prática da análise, extração, limpeza e geração de insights voltados a um problema realista.*

## 1. Cenário
  
Uma empresa fictícia de compartilhamento de bicicletas que opera 24 horas por dia na cidade de Chicago, oferece diferentes tipos de bicicleta e modalidades de  contratação do seu serviço. Com o objetivo de analisar o comportamento de seus usuários, a empresa disponiblizou os dados de suas viagens entre os meses de **abril de 2024 e abril de 2025** 

Este projeto busca gerar insights que ajudem a equipe de marketing da empresa a compreender as diferenças no comportamento de uso entre usuários casuais e membros anuais, e propor estratégias de marketing que incentivem a conversão de usuários eventuais em assinantes.

## 2. Objetivo do projeto

Embasado na análise dos dados, as seguintes perguntas de negócio devem ser respondidas aos *stakeholders*

- Como os membros anuais e os usuários casuais utilizam as bicicletas?
- Por que os usuários casuais comprariam assinaturas anuais?
- Como se pode usar a mídia digital para influenciar os usuários casuais a se tornarem membros?

## 3. Base de dados

**Fonte** https://divvy-tripdata.s3.amazonaws.com/index.html;

**Período de Análise:** abril de 2024 e abril de 2025;

**Total de Registros** 6.150.909 viagens; 

**Formato** arquivos separados mensalmente em CSV

**Campos utilizdos para análise**: Os seguintes campos foram utilizados para as análises efetuadas neste projeto:

```
- rideable_type: modelo da bicicleta utilizada; 
- started_at: hora e data de ínicio do uso da bicicleta;
- ended_at: hora e data de finalização do uso da bicicleta;
- start_lat: latitude de ínicio do uso da bicicleta; 
- start_lng: longitide de ínicio do uso da bicicleta;
- end_lat: latitude de finalização de uso da bicicleta;
- end_lng: longitude de finalização de uso da bicicleta; 
- member_casual: tipo de usuário da bicicleta.
```
## 4. Metodologia

### 4.1 Estruturação da Abordagem Analítica

Seguindo o proposto no curso *Google Data Analytics Certificate*, o estudo do projeto foi estruturado em  seis etapas principais:

- **Perguntar:** Entender clarmaente as perguntas que precisam ser respondidas por meio desta análise. Levantar novas questões alinhadas às demandas dos *stakeholders* 
- **Preparar:** Coletar os dados disponíveis, compreender as suas características e avaliar e qual será a ferramenta mais adequada para a análise.
- **Processar:** Limpar, transformar e coletar dados com consistência e qualidade.
- **Analisar:** Criar consultas na base para explorar os daods e buscar respostas para as perguntas formuladas.
- **Compartilhar:** Comunicar os achados por meio de visualizações e de narrativa, visando facilitar o entendimento por diferentes perfis de público
- **Agir:** Gerar recomendações práticas baseadas em dados. 

### 4.2 Ferramentas Utiilzadas

- SQL (PostgreSQL PgAdmin4);
- Excel;
- Google Sheets.

### 4.3 Consultas SQL

As consultas SQL criadas para esta análise estão disponíveis neste [arquivo complementar](./sql.md)

## 5. Análise Exploratória e Resultados

### 5.1 Visão Geral

- Aproximadamente 63,5% dos usuários são assinantes, enquanto 36,5% são usuários casuais; 
- O tempo médio por viagem é de 12 minutos para assinantes e 24 minutos para casuais;
- A maior concentração de viagens para assinantes ocorre durante a semana e em horários de deslocamento padrão. Já para os casuais, aos finais de semana e no final da tarde;
- O modelo elétrico é o mais usado por ambos os grupos;
- As estações climáticas afetam o uso do serviço para ambas as modalidades.

### 5.2 Comparação do Comportamento dos Usuários

- **Divisão do universo de análise, baseado nos dois tipos de usuários das bicicletas:**

![image](https://github.com/user-attachments/assets/71b83bb2-225d-459e-81a7-77871909d134)

- **Tempo médio e opção de bicicletas**

![image](https://github.com/user-attachments/assets/111b3e66-5cbb-4262-95c3-20f4bee46981)

- **Horários frequentes de uso das bicicletas**

![image](https://github.com/user-attachments/assets/913b3655-ab03-4e28-a1b2-22f88eebbbb3)

- **O comportamento de uso entre assinantes e casuais difere entre dias de semana e finais de semana:** 

![image](https://github.com/user-attachments/assets/d3cbc3a5-2508-4793-b864-c880b405dcc9)

- **A sazonalidade impacta o uso em ambos os grupos de clientes:**

![image](https://github.com/user-attachments/assets/70986fc6-0bbd-440c-9719-d87ec823cbeb)

## 6. Recomendações Estratégicas

Com base nos comportamentos de cada grupo de clientes constatados na análise, as recomendações abaixo podem contribuir para a conversão de clientes casuais em assinantes:

- **Campanhas promocionais aos finais de semana**: Considerando a grande procura aos finais de semana pelos usuários casuais, pode ser criado um *plano gratuito de 03 dias* ou *planos para uso ilimitado no final de semana*. Isso gera a experiência de ser assinante, e uma possível conversão para este público;

- **Planos para turistas**: Criação de modalidade de assinatura a curto prazo voltada para visitantes da cidade; 

- **Notificações no Aplicativo**: Incluir mensagens e notificações dentro do aplicativo com comparações sobre a economia na adesão do plano por assinatura.

- **Incentivos no horário de pico**: Aproveitar o horário de pico do uso de bicicletas pelos casuais o oferecer recompensas pelo uso das mesmas com frequência pode estimular o uso regular e consequentemente, a adesão. 

- **Sazonalidade Climática**: O uso das bicicletas caí significativamente nos meses mais frios. Nestes períodos, aplicar estratégias de retenção (desafios, pontos, descontos para uso regular).

## 7. Limitações da Análise

- **Ausência de dados do usuário:** As informações disponíveis não incluem idade, gênero ou profissão dos usuários. Isso limita a personalização de campanhas específicas para grupos que possam gerar mais relevância na conversão para assinantes;
  
- **Informação sobre motivo de viagem:** As interpretações sobre o uso rotineiro ou lazer foram feitas com base em padrões de horários e dia da semana. Não é possível saber exatamente qual é o motivo de cada um dos deslocamentos; 

- **Informações Climáticas Específicas**: Apesar da análise do uso em detrimento da estação do ano, não se têm dados robustos sobre períodos chuvosos ou com intempéries que possam impactar significativamente no uso da bicicleta. 

## 8. Conclusão

A análise dos dados do sistema de Bicicletas Compartilhadas em Chicago permitiu identificar padrões distintos de comportamento entre os assinantes e usuários casuais. 

Fica evidente que a utilização das bicicletas é mais recorrente pelos assinantes e em especial em dias úteis e nos horários de pico, demonstrando que o sistema é atuante em mobilidade. Já para os usuários casuais, o uso é mais frequente em finais de semana e ao fim da tarde, demonstrando um perfil de uso para lazer ou turismo. 

As diferenças aqui citadas abrem oportunidades estratégicas para a empresa desenvolver ações para a conversão dos usuários casuais para assinantes. A sugestão de campanhas promocionais segmentadas a este público, planos flexíveis e propagandas no app são os pontos focais para a conversão destes ciclistas para assinantes. 
