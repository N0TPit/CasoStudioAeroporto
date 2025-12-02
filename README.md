# CasoStudioAeroporto
# Gruppo di Lavoro: Michele Napoletano | Luca John Bowen | Michele Innamorato
use airport_management;

1. Inserimento Aeroporti (Include Gate)
db.aeroporti.insertMany([
  {
    "_id": "FCO",
    "nome_aeroporto": "Aeroporto Leonardo da Vinci",
    "citta": "Roma",
    "paese": "Italia",
    "fuso_orario": "Europe/Rome",
    "coordinate": { "latitudine": 41.7999, "longitudine": 12.2462 },
    "terminal_presenti": ["T1", "T3"],
    "gate": [
      { "numero": "E11", "terminal": "T3", "stato": "DISPONIBILE" },
      { "numero": "A01", "terminal": "T1", "stato": "MANUTENZIONE" }
    ]
  },
  {
    "_id": "JFK",
    "nome_aeroporto": "John F. Kennedy International Airport",
    "citta": "New York",
    "paese": "USA",
    "fuso_orario": "America/New_York",
    "coordinate": { "latitudine": 40.6413, "longitudine": -73.7781 },
    "terminal_presenti": ["T1", "T4", "T5"],
    "gate": [
      { "numero": "B20", "terminal": "T4", "stato": "DISPONIBILE" }
    ]
  }
]);

db.aeromobili.insertMany([
  {
    "_id": "EI-DTE",
    "modello": "Airbus A320",
    "produttore": "Airbus",
    "anno_produzione": 2015,
    "capacita_passeggeri": 180
  }
]);

db.personale.insertMany([
  { "_id": "M001", "nome": "Mario", "cognome": "Rossi", "ruolo": "PILOTA" },
  { "_id": "M002", "nome": "Luca", "cognome": "Bianchi", "ruolo": "ASSISTENTE_DI_VOLO" }
]);

db.voli_programmati.insertMany([
  {
    "_id": "AZ608",
    "codice_compagnia": "AZ",
    "aeroporto_partenza": "FCO",
    "aeroporto_arrivo": "JFK",
    "giorni_operativi": ["LUN", "MER", "VEN"],
    "orario_partenza": "10:00",
    "durata_stimata_min": 600
  }
]);

db.voli_operativi.insertMany([
  {
    "_id": "AZ608-20240315",
    "id_volo_programmato": "AZ608",
    "data_volo": ISODate("2024-03-15T10:00:00Z"),
    "stato": "IMBARCO",
    "id_aeromobile": "EI-DTE",
    "gate_assegnato": { "terminal": "T3", "numero": "E11" },
    "personale_bordo": ["M001", "M002"]
  }
]);
