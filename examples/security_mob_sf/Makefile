HOST_DEVOPS="0.0.0.0"
MOBSF_KEY=""

security-mob-sf:
	FILENAME="myfile.apl"
	@ HASH=$(curl -F "file=@./$FILENAME" http://${HOST_DEVOPS}/api/v1/upload -H "Authorization:$MOBSF_KEY" | python -c "import sys, json; print json.load(sys.stdin)['hash']")
	@ echo "hash=" $HASH
	@ curl -X POST --url http://${HOST_DEVOPS}/api/v1/scan --data "scan_type=apk&file_name=$FILENAME&hash=$HASH" -H "Authorization:$AUTH"
	@ curl -X POST --url http://${HOST_DEVOPS}/api/v1/download_pdf --data "hash=$HASH&scan_type=apk" -H "Authorization:$AUTH" > report.pdf
	ls -l report.pdf

.PHONY: security-mob-sf
