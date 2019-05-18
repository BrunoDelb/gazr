DOCKER_FILE=Dockerfile
RULE_FILE=./input/lint_docker/rules.yml

lint-docker:
	@ docker run --rm -i lukasmartinelli/hadolint < $(DOCKER_FILE)

lint-ansible:
	@ docker run --rm -v ${PWD}:/work -w /work agilelabtest/lint_ansible sh -c 'find . -name "*.yml" | xargs -r ansible-lint --force-color'

lint-css:
	@ docker run --rm -v ${PWD}:/app agilelabtest/lint_css # /root/stylelint.sh "foo/*.css"

lint-docker2:
	# For more information : https://github.com/projectatomic/dockerfile_lint/
	@ docker run -it --rm --privileged -v $PWD:/root/ projectatomic/dockerfile-lint dockerfile_lint -f ${DOCKER_FILE} -r ${RULE_FILE}
	# docker run -it --rm --privileged -v $PWD:/root/ -v /var/run/docker.sock:/var/run/docker.sock projectatomic/dockerfile-lint dockerfile_lint  image <imageid>

lint-sonar:
	@ docker run --rm -it -v $(PWD)/src:/code -v $(PWD)/report:/report sonarlint --html-report /report/sonar.html

.PHONY: lint-docker lint-ansible lint-css lint-docker2 lint-sonar
