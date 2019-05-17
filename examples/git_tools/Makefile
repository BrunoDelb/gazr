.PHONE: git-tools

BUILD_SOURCESDIRECTORY=$(PWD)/src
BUILD_BINARIESDIRECTORY=$(PWD)/report
PROJECT_PREFIX=demo_
DOCKER_GIT_TOOLS="0.24"
BRANCH="android-1.1.10"

git-cloc: # OK
	# Generate a Cloc report
	docker run --rm -v $(BUILD_SOURCESDIRECTORY):/src -v $(BUILD_BINARIESDIRECTORY):/report agilelabtest/git-tools:$(DOCKER_GIT_TOOLS) REPORTFILE=$(PROJECT_PREFIX)cloc_app.json get_cloc
	cat $(BUILD_BINARIESDIRECTORY)/$(PROJECT_PREFIX)cloc_app.json

git-big-picture:
	@ docker run --rm -v $(BUILD_SOURCESDIRECTORY):/data agilelabtest/git-big-picture /git-big-picture -o branching_graph.png
	ls -l $(BUILD_SOURCESDIRECTORY)/branching_graph.png

git-summary: # OK
	# Generate a Git summary report
	docker run --rm -v $(BUILD_SOURCESDIRECTORY):/src -v $(BUILD_BINARIESDIRECTORY):/report agilelabtest/git-tools:$(DOCKER_GIT_TOOLS) REPORTFILE=$(PROJECT_PREFIX)summary.json get_git_summary
	cat $(BUILD_BINARIESDIRECTORY)/$(PROJECT_PREFIX)git_summary.json

git-changelog: # OK
	# Generate a Changelog report
	docker run --rm -v $(BUILD_SOURCESDIRECTORY):/src -v $(BUILD_BINARIESDIRECTORY):/report agilelabtest/git-tools:$(DOCKER_GIT_TOOLS) REPORTFILE=$(PROJECT_PREFIX)changelog.txt get_git_changelog
	cat $(BUILD_BINARIESDIRECTORY)/$(PROJECT_PREFIX)git_changelog.txt

git-log: # OK
	# Generate a Git log report
	docker run --rm -v $(BUILD_SOURCESDIRECTORY):/src -v $(BUILD_BINARIESDIRECTORY):/report agilelabtest/git-tools:$(DOCKER_GIT_TOOLS) REPORTFILE=$(PROJECT_PREFIX)log.json get_git_log
	cat $(BUILD_BINARIESDIRECTORY)/$(PROJECT_PREFIX)git_log.json

git-stats: # OK
	# Generate a Git stats report
	docker run --rm -v $(BUILD_SOURCESDIRECTORY):/src -v $(BUILD_BINARIESDIRECTORY):/report agilelabtest/git-tools:$(DOCKER_GIT_TOOLS) REPORTFILE=$(PROJECT_PREFIX)stats.json get_git_stats
	cat $(BUILD_BINARIESDIRECTORY)/$(PROJECT_PREFIX)git_stats.json

git-effort: # OK
	# Generate a Git effort report
	docker run --rm -v $(BUILD_SOURCESDIRECTORY):/src -v $(BUILD_BINARIESDIRECTORY):/report agilelabtest/git-tools:$(DOCKER_GIT_TOOLS) REPORTFILE=$(PROJECT_PREFIX)effort.json get_git_effort
	cat $(BUILD_BINARIESDIRECTORY)/$(PROJECT_PREFIX)git_effort.csv

git-count: # OK
	# Generate a Git count report
	docker run --rm -v $(BUILD_SOURCESDIRECTORY):/src -v $(BUILD_BINARIESDIRECTORY):/report agilelabtest/git-tools:$(DOCKER_GIT_TOOLS) REPORTFILE=$(PROJECT_PREFIX)count.json get_git_count
	./prepare_count.sh
	cat $(BUILD_BINARIESDIRECTORY)/$(PROJECT_PREFIX)git_count.json

git-commits: # 
	# Get metrics to monitor the operations on Git
	docker run --rm -v $(BUILD_SOURCESDIRECTORY):/src -v $(BUILD_BINARIESDIRECTORY):/report agilelabtest/git-tools:$(DOCKER_GIT_TOOLS) REPORTFILE=$(PROJECT_PREFIX)commits.json get_count_commits_per_day
	cat report/${PROJECT_PREFIX}commits.json

git-updated-lines: # BUG !!!!!!
	docker run --rm -v $(BUILD_SOURCESDIRECTORY):/src -v $(BUILD_BINARIESDIRECTORY):/report agilelabtest/git-tools:$(DOCKER_GIT_TOOLS) REPORTFILE=$(PROJECT_PREFIX)updated_lines_per_day.json BRANCH=$(BRANCH) DURATION=365 get_count_updated_lines_per_day
	cat report/${PROJECT_PREFIX}updated_lines_per_day.json

git-branch-date:
	docker run --rm -v $(BUILD_SOURCESDIRECTORY):/src -v $(BUILD_BINARIESDIRECTORY):/report agilelabtest/git-tools:$(DOCKER_GIT_TOOLS) REPORTFILE=$(PROJECT_PREFIX)branches_per_date.json get_list_branch_per_date
	cat report/${PROJECT_PREFIX}branches_per_date.json

git-branch-not-merged:
	docker run --rm -v $(BUILD_SOURCESDIRECTORY):/src -v $(BUILD_BINARIESDIRECTORY):/report agilelabtest/git-tools:$(DOCKER_GIT_TOOLS) REPORTFILE=$(PROJECT_PREFIX)branches_not_merged.txt get_list_branch_not_merged
	cat report/${PROJECT_PREFIX}branches_not_merged.txt

git-repo-size:
	# Get the Git repo size
	docker run --rm -v $(BUILD_SOURCESDIRECTORY):/src -v $(BUILD_BINARIESDIRECTORY):/report agilelabtest/git-tools:$(DOCKER_GIT_TOOLS) REPORTFILE=$(PROJECT_PREFIX)repo_size.json get_git_repo_size
	cat report/${PROJECT_PREFIX}repo_size.json

git-sizer:
	# For more information: https://github.com/github/git-sizer
	@ docker run -it --rm -v $(PWD)/src:/app willhallonline/git-sizer:alpine

git-hours:
	@ docker run --rm -v $(PWD)/src:/code khor/git-hours
