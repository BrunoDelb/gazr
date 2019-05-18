FILENAME_APK="myapp.apk"
BUILD_ARTIFACTS=$(PWD)/artifacts

android-redex:
	@ docker run -v $(PWD)/src:/data/redex cortinico/redex redex ${FILENAME_APK} -o redex_${FILENAME_APK}
	@ ls -l redex_$(FILENAME_APK)

apk-analyzer:
	docker run --rm -e APK_FILE=$FILENAME_APK -e REPORT_FILE=analyze_apk.json -v $(BUILD_ARTIFACTS):/data -v $(PWD)/report:/report agilelabtest/apk_analyzer analyze_apk

.PHONY: android-redex apk-analyzer
