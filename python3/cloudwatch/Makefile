AWS_PROFILE ?= default

-include Makefile.local

build:
	mkdir -p dist/python3/shipper
	cp -r ../shipper/shipper.py dist/python3/shipper
	cp src/lambda_function.py dist
	cd dist && zip -r logzio-cloudwatch-`date +"%Y%m%d-%H%M"`.zip lambda_function.py python3/shipper/*

upload:
	aws --profile $(AWS_PROFILE) s3 cp dist/logzio-cloudwatch-*.zip s3://$(TARGET_BUCKET)/$(TARGET_PATH)

clean:
	rm -rf dist/