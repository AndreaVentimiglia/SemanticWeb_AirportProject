# Semantic Web - OWL Ontology in Protege - AirportProject

## Collaboratori
- **Arena Gabriele**
- **Corsaro Miriana**
- **Ventimiglia Andrea Paolo**

## Ontology domain: Airport
Our goal is to develop an ontology that accurately and comprehensively represents the various entities and relationships that occur in an **Airport context**.  
The ontology will help us better understand the structure, operations and processes involved in an airport.

For a detailed explanation of how the project works, see the documentation:
- ENG: [qui](Docs/Documentation.pdf).

## Classes and properties
Our ontology will consist of several key concepts modelled by the following classes:
- **Aeroporto**: represents an airport, a place where planes take off and land, equivalent to RDF data “Internation_airport”.
- **Compagnia**: represents an airline company that operates flights. 
- **Passeggero**: represents an individual who travels on an aircraft, related to FOAF ontology.
- **Volo**: represents a specific flight between two airports. It can have several properties that describe departure and arrival times, departure and destination airports, and operating airline company.
- **Aereo**: represents an aircraft used for passenger transportation, composed of “ComponentiAereo” (Part-Whole ODF).
- **Nazione**: represents a sovereign nation.
- **Città**: represents a city or urban settlement. 
- **Evento**: represents an event that can be associated with an airport or a flight, such as flight cancellation or delay. It has these attributes: startDate and endDate (Time ODF).
- **Stato**: represents flight status as “isDeparting”, “inArriving”, “cancelled”, “deleyed”, “scheduled” and “landed” (State ODF).
![image](https://github.com/AndreaVentimiglia/SemanticWeb_AirportProject/assets/63006903/37bacc5c-f5c4-4da4-ad7d-b8c7b97943f2)
