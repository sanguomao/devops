.PHONY: \
	ci \
	lint test build \
	docker-dev docker-dev-build docker-dev-push \
	docker-prod docker-prod-build docker-prod-push

VERSION ?= 1.0.`date +%Y%m%d`
BASE_COMMIT_ID ?= ""

ci:
	docker build --build-arg base_commit_id="origin/master" \
	-t harbor.longguikeji.com/ark-releases/template_repo_name:$(VERSION) .

test:
	test-template

lint:
	@if [ ${BASE_COMMIT_ID}x != ""x ]; \
	then \
		git reset ${BASE_COMMIT_ID}; \
		git add .; \
	fi

	lint-template

build: docker-dev-build

docker-dev: docker-dev-build docker-dev-push

docker-dev-build:
	docker build -t harbor.longguikeji.com/ark-releases/template_repo_name:$(VERSION) .

docker-dev-push:
	docker push harbor.longguikeji.com/ark-releases/template_repo_name:$(VERSION)

docker-prod: docker-prod-build docker-prod-push

docker-prod-build:
	docker build -t  harbor.longguikeji.com/ark-releases/template_repo_name:$(VERSION) .

docker-prod-push:
	docker push harbor.longguikeji.com/ark-releases/template_repo_name:$(VERSION)
