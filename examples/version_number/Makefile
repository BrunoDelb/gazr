update-version:
	BUILD_NUMBER=`cat ./next-version.txt`
	echo $$(($(BUILD_NUMBER) + 1)) > ./next-version.txt
	git add ./next-version.txt
	git commit -m "Version updated"
	git push

get-version:
	BUILD_NUMBER=`cat ./next-version.txt`
	VERSION=`date +%y.%m.%d`.$(BUILD_NUMBER)
	@echo "Build number: $(BUILD_NUMBER)"
	@echo "Version: $(VERSION)"

.PHONY: update-version get-version
