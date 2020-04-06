FROM mongo

COPY init.json /init.json
# --host is name of container that houses db
# --authenticationDatabase must be configured in order to authenticate user and password
#   https://docs.mongodb.com/manual/reference/program/mongo/#mongo-shell-authentication-options
# --username username defined in container that houses db
# --password password defined in container that houses db
# --db set name of database
# --collection set name of collection to import data into
# --type data type to import
# --file file to import
CMD mongoimport --host narneso_mongo --authenticationDatabase admin --username root --password rootpassword --db test --collection srd --type json --file ./init.json --jsonArray
