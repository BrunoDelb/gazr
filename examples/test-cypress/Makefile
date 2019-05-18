CYPRESS_REPORT_DIR=$(PWD)/report
CYPRESS_REPORT_FILE=result.xml
CYPRESS_TESTS_DIR=$(PWD)/input/test_cypress

test-cypress:
	@ docker run -v $CYPRESS_REPORT_DIR:/report -v $CYPRESS_TESTS_DIR:/app -e REPORT_FILE=$CYPRESS_REPORT_FILE -e CYPRESS_videosFolder=/report -e CYPRESS_screenshotsFolder=/report cypress_test run_cypress

.PHONY: test-cypress
