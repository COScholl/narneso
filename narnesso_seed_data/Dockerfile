FROM mongo

COPY init.json /init.json
# explicitly define mongodb:<host>, otherwise cannot find connection
CMD mongoimport --host narneso_mongodb_container --authenticationDatabase admin --username root --password rootpassword --db test --collection srd --type json --file ./init.json --jsonArray
