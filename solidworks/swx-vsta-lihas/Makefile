WGET_COMMON_OPTIONS  = -q -N

PACKAGE_NAME         = swx-vsta-lihas
VERSION              = 1
OPSI_PACKAGE_VERSION = 1

TARGET               = $(PACKAGE_NAME)_$(VERSION)-$(OPSI_PACKAGE_VERSION).opsi

all: checkpresence build install

checkpresence: md5sums.txt CLIENT_DATA/files
	md5deep -r -n -l -X md5sums.txt CLIENT_DATA/files/*

$(TARGET): checkpresence
	opsi-makeproductfile

build: $(TARGET)

$(TARGET).uploaded:
	opsi-package-manager -i $(TARGET)
	touch $(TARGET).uploaded

install: $(TARGET).uploaded

clean:
	rm -rf CLIENT_DATA/files/*
	rm -f $(TARGET) $(TARGET).uploaded
