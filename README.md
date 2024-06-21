# Semantic Web - OWL Ontology in Protege - AirportProject


## Ontology domain: Airport
Our goal is to develop an ontology that accurately and comprehensively represents the various entities and relationships that occur in an **Airport context**.  
The ontology will help us better understand the structure, operations and processes involved in an airport.

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

## Pattern ODP
### Part-Whole ODP
**Definition**: the Part-Whole ODP is a design pattern that helps represent the relationships between an entity and its constituent parts. It is based on concepts such as aggregation, composition and mereology and can be used in different fields, such as biology and computer science.
Use: 
![image](https://github.com/AndreaVentimiglia/SemanticWeb_AirportProject/assets/63006903/b0cac88c-33ed-42c3-9fc9-93f62d0f5e80)

### State ODP
**Definition**: the State Patterns ODP is a design pattern that helps represent entities and their states. It is based on concepts such as state, state transition, event and action and can be used in different fields, such as healthcare and finance.
Use:
![image](https://github.com/AndreaVentimiglia/SemanticWeb_AirportProject/assets/63006903/22ed5bde-6c8d-47ad-9eba-6b333eb63e4f)

### TimeODP 
**Definition**:
Definition: the Time ODP is a design pattern that helps represent time and the temporal relationships between events and objects. It is based on concepts such as event, instant, interval, duration and time zone and can be used in different fields, such as science and medicine.
Use:
![image](https://github.com/AndreaVentimiglia/SemanticWeb_AirportProject/assets/63006903/a54536cc-296e-48ca-bdfa-253b3dafa641)

## RDF data from an external source
![image](https://github.com/AndreaVentimiglia/SemanticWeb_AirportProject/assets/63006903/0f9b156b-3a8d-4df9-b8b2-b224397dceff)
Source: https://dbpedia.org/page/International_airport

## Use of existing ontology
We use as existing ontology FOAF, related to «Passeggero» class.
![image](https://github.com/AndreaVentimiglia/SemanticWeb_AirportProject/assets/63006903/2c136901-5c1d-4868-95f9-e79f1f97c1d7)

## Use Case
### UC 1
Airtraffic of an Aeroport: list of flights that are scheduled to take off from a given Aeroporto.

SELECT ?volo ?status ?aeroportoPartenza
WHERE {	
	?volo rdf:type airport:Volo .
	?volo airport:status ?status .
	?volo airport:parteDa ?aeroportoPartenza
	FILTER (?status = airport:InPartenza)
	FILTER (?aeroportoPartenza = airport:Tegel)
}

![image](https://github.com/AndreaVentimiglia/SemanticWeb_AirportProject/assets/63006903/9a515007-3fc1-49ae-9dcd-773fa62022f9)

### UC 2
Find scheduled flights that have airports of departure or arrival associated with an event causing its closure on those days.

SELECT ?Evento ?aeroportoPartenza ?aeroportoArrivo ?inizio ?fine 
WHERE { ?Volo airport:haEventoPA ?Evento .
	?Evento airport:dataInizio ?inizio .
	?Evento airport:dataFine ?fine .
	FILTER(?inizio > "2023-07-05T00:00:00"^^xsd:dateTime && ?fine < "2023-07 	05T23:59:59"^^xsd:dateTime)
	?Volo airport:parteDa ?aeroportoPartenza .
	?Volo airport:arrivaIn ?aeroportoArrivo .
	FILTER(?aeroportoArrivo=airport:Fontanarossa || ?aeroportoPartenza=airport:Fontanarossa)
}

![image](https://github.com/AndreaVentimiglia/SemanticWeb_AirportProject/assets/63006903/94e60046-13d7-4e6a-ae50-a7ab23088636)

### UC 3
Select the names of all passengers who are children bound for Fontanarossa.

SELECT ?Passeggero ?Volo ?age
WHERE {
  	?Volo airport:parteDa ?AeroportoPartenza .
	FILTER (?AeroportoPartenza = airport:Fontanarossa) .
	?Passeggero airport:passeggeroDi ?Volo .
	?Passeggero foaf:age ?age
	FILTER(?age<18)
}

![image](https://github.com/AndreaVentimiglia/SemanticWeb_AirportProject/assets/63006903/58b4e224-d67a-4505-938b-8b9a4ac8ff35)


