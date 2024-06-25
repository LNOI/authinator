FROM quay.io/keycloak/keycloak:24.0 as builder

# Enable health and metrics support
ENV KC_HEALTH_ENABLED=true
ENV KC_METRICS_ENABLED=true

# Configure a database vendor
ENV KC_DB=postgres

WORKDIR /opt/keycloak
# for demonstration purposes only, please make sure to use proper certificates in production instead
RUN /opt/keycloak/bin/kc.sh build --features=preview

FROM quay.io/keycloak/keycloak:24.0
COPY --from=builder /opt/keycloak/ /opt/keycloak/

# change these values to point to a running postgres instance
ENV KC_DB=postgres
ENV KC_DB_URL=jdbc:postgresql://keycloak-database:5432/keycloak-db
ENV KC_DB_USERNAME=keycloak
ENV KC_DB_PASSWORD=wieBeu1Kohk2eeBiez6qui8eekohtaht
ENV KC_HOSTNAME=sso.authinator.io
ENTRYPOINT ["/opt/keycloak/bin/kc.sh"]
