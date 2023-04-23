AWS_PROFILE ?= default

-include Makefile.local


build:
	mkdir -p dist/
	zip -j dist/logzio-cloudwatch-`date +"%Y%m%d-%H%M"`.zip src/lambda_function.py ../shipper/shipper.py

upload:
	aws --profile $(AWS_PROFILE) s3 cp dist/* s3://$(TARGET_BUCKET)/$(TARGET_PATH)

clean:
	rm -rf dist/