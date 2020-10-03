set-http:
	echo COMPOSE_FILE=docker-compose-http.yml > .env
	docker-compose config

set-https-cloudflare:
	# https://stackoverflow.com/a/56193440
	@[ "${LE_ACME_EMAIL}" ] || ( echo "Set variable LE_ACME_EMAIL with you email, eg. LE_ACME_EMAIL=your@email.com"; exit 1 )
	echo COMPOSE_FILE=docker-compose-https-cloudflare.yml > .env
	echo LE_ACME_EMAIL=${LE_ACME_EMAIL} >> .env
	docker-compose config
