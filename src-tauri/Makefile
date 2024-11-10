include .env

ENTITY_OUTPUT = src/entity

gen-entity:
	@echo "Generating entities..."
	@sea-orm-cli generate entity --with-serde both -u $(DATABASE_URL) -o $(ENTITY_OUTPUT)

migrate-init:
	@echo "Initializing migration directory..."
	@sqlx migrate add init

gen-migrate:
	@read -p "Enter migration name: " name; \
	sqlx migrate add -r $$name

migrate-up:
	@echo "Running migrations..."
	sqlx migrate run

migrate-down:
	@echo "Rolling back last migration..."
	sqlx migrate revert

migrate-status:
	sqlx migrate info
