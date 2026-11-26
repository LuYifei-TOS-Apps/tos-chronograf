# Chronograf on TOS privacy policy

This policy covers the self-hosted TOS package for Chronograf. The NAS administrator operates the installation and controls its data and backups.

## Data and purpose

Chronograf stores dashboards and connection settings, which can include database credentials, in the TOS data directory mounted at `/var/lib/chronograf`. Time-series records are managed by the connected InfluxDB instance.

## Sharing and external services

Queries and connection credentials go to the InfluxDB and Kapacitor endpoints that the operator configures. Those systems can be on the NAS or on another host. This package disables Chronograf usage reporting.

Installation and updates can contact TOS distribution services and container registries to obtain packages and images. Requests to external services are handled according to the services and locations selected by the operator.

## Retention, access, correction and deletion

Dashboards and connections persist until edited, deleted or removed by the NAS administrator. Users can manage them from Chronograf. To delete stored measurements, use the controls on the connected InfluxDB instance.

To remove an entire instance, stop it and identify the app-owned storage in Docker Manager before deleting it. The NAS administrator should handle retained backups separately and verify the effects of the TOS uninstall options. Contact the NAS administrator to request access, correction or deletion of data held by the instance.

## Security and support

Restrict access to the Chronograf HTTP port and protect the data directory and its backups. The initial service is intended for a trusted network.

For questions about the TOS package, use the repository's issue tracker. Omit private data, credentials and unredacted logs from public reports.
