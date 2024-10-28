export DOCKER_BUILDKIT := 0

PROJECT = umi-neo
command = docker compose -p $(PROJECT) \
     -f umi/docker/docker-compose.yml
ifneq (,$(wildcard docker-compose.override.yml))
  command += -f docker-compose.override.yml
endif
ifneq (,$(wildcard .env))
  command += --env-file .env
endif
ifneq ($(TERM),xterm)
  command += --ansi=never
endif

define goal =
$(1):
	$$(command) $(1)$(if $(filter-out up, $(1)),, -d)
endef

all: build

build: bootstrap

bootstrap:
	git submodule update --init --recursive

$(foreach verb, build config up down restart ps logs, $(eval $(call goal, $(verb))))

