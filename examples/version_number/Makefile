.PHONE: update-version

version = `date +%y.%m.%d`.$(number)

update-version:
	number=`cat ./next-version.txt`
	echo $$(($(number) + 1)) > ./next-version.txt
	git add ./next-version.txt
	git commit -m "Bump version"
	git push

version:
	@echo $(version)

