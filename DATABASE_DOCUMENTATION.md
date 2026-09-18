The Land Record Database is designed to store and manage digitized land records, land parcels, ownership information, supporting documents, and land transactions.
The database is implemented using PostgreSQL and consists of six main tables:
1. tbl_land_parcel
2. tbl_owner_entity
3. tbl_ownership_share
4. tbl_transactions
5. tbl_documents
6. tbl_digitization_queue


## tbl_land_parcel
Stores information about land parcels. Important field includes: 
parcel_id - (primary key) unique ID of the land parcels 
survey_number - survey number of the land
total_area - total area of the land
unit_of_measurement - unit in which area is measured 
village_code - code of the village
land_type - type of land

## tbl_owner_entity
Stores information about owner of the land. Important field includes: 
owners_id - (primary key) unique ID of the owner 
full_name - full name of the owner 
father's_name - father's name of the owner 
aadhar_hash - (unique constraints) 
contact_info - contact information of the owner 

## tbl_ownership_share
Represents the ownership relationship between owners and land parcels.
ownership_id - (primary key) unique identifier for the ownership record 
parcel_id - (foreign key) reference from tbl_land_parcel
owners_id - (foreign key) reference from tbl_owner_entity
share_percentage - owner of how many percentage of total area 
tenure_type - time of ownership 

## tbl_transaction
Stores information about transactions involving land parcels.
transaction_id - (primary key) unique ID for transaction 
parcel_id - (foreign key) reference from tbl_land_parcel
seller_id - (foreign key) reference from tbl_owner_entity. who sells the land
buyer_id - (foreign key) reference from tbl_owner_entity. who buys the land
transaction_date - date of transaction 
sale_value - value of transaction 
deed_type - Type of deed associated with the transaction

## tbl_documents
Stores information about digitized land-related documents.
documents_id - (primary key) unique ID for documents 
file_url - location of the document file
document_type - type of document 
upload_timestamp - date and time when the document was updated 

## tbl_digitization_queue
queue_id - (primary key) unique ID for the queue record 
document_id - (foreign key) 
raw_ai_json - AI generated
validation_status - current validation status 
operator_comments - comment added by the operator 
last_updated - last update timestamp 
