.PHONY: test-cypress

test-cypress:
	@ docker run -v $(PWD)/report:/report -v $(PWD)/input/test_cypress:/app -e REPORT_FILE=result.xml -e CYPRESS_videosFolder=/report -e CYPRESS_screenshotsFolder=/report cypress_test run_cypress
