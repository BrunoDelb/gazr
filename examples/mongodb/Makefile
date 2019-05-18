MONGODB_FILE=""
MONGODB_USERNAME="my_username"
MONGODB_PASSWORD="my_password"
MONGODB_EXPORT_FILE="./mongodb_data"
MONGODB_DB="my_database"

mongodb:
	docker run --name mongodb -v $(PWD)/mongodb_db:/data/db -v $(PWD)/mongodb_conf:/etc/mongo -e MONGO_INITDB_ROOT_USERNAME=$(MONGODB_USERNAME) -e MONGO_INITDB_ROOT_PASSWORD=$(MONGODB_PASSWORD) -d mongo --config /etc/mongo/mongod.conf

mongodb-export:
	docker exec some-mongo sh -c "exec mongodump -d $(MONGODB_DB) --archive" > $(MONGODB_EXPORT_FILE)

.PHONY: mongodb mongodb-export
