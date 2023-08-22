FROM ckan/ckan-base:2.10.1
#FROM ckan/ckan-base:2.9.9

# Set up environment variables
ENV APP_DIR=/srv/app
ENV TZ=UTC
RUN echo ${TZ} > /etc/timezone

# Make sure both files are not exactly the same
RUN if ! [ /usr/share/zoneinfo/${TZ} -ef /etc/localtime ]; then \
        cp /usr/share/zoneinfo/${TZ} /etc/localtime ;\
    fi ;


COPY nfwf-ckan-extensions/ckanext-nfwf_theme ${APP_DIR}/ckanext-nfwf_theme

RUN pip3 install -e ${APP_DIR}/ckanext-nfwf_theme

COPY nfwf-ckan-extensions/ckanext-nfwf_fields ${APP_DIR}/ckanext-nfwf_fields

RUN pip3 install -e ${APP_DIR}/ckanext-nfwf_fields
