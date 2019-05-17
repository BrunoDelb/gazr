.PHONY: code-maat

BUILD_SOURCESDIRECTORY=$(PWD)/src
FROM_DATE=2018-01-01

code-maat:
	@ docker run --rm -v $(BUILD_SOURCESDIRECTORY):/data agilelabtest/code_maat /code-maat.sh $FROM_DATE
	docker run --rm -v $(PWD)/src:/data agilelabtest/code_maat /code-maat.sh $FROM_DATE
	ls -l $(BUILD_SOURCESDIRECTORY)/report*.csv
