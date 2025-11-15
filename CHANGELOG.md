# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.0] - 2025-01-08

### Added
- Initial Helm chart release for the Arr stack applications
- Support for Sonarr deployment with StatefulSet, Service, ServiceAccount, and Certificate
- Support for Radarr deployment with StatefulSet, Service, ServiceAccount, and Certificate
- Support for Overseerr deployment with StatefulSet, Service, ServiceAccount, and Certificate
- Support for SABnzbd deployment with StatefulSet, Service, ServiceAccount, and Certificate
- Configurable Ingress with support for multiple applications and TLS
- Node affinity, tolerations, and node selector support for all applications
- Resource limits and requests configuration for all applications
- Persistent storage configuration with PersistentVolumeClaims
- Service annotations and port customization
- Certificate management support via cert-manager
- Configurable SABnzbd scripts via ConfigMap
- Comprehensive values.yaml with sensible defaults for all applications

### Configuration
- Support for custom image repositories and tags
- Configurable replicas and service types
- Environment variable configuration per application
- Storage class and size configuration
- Ingress host and path configuration with optional TLS

[Unreleased]: https://github.com/yourusername/arr-helm/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/yourusername/arr-helm/releases/tag/v0.1.0
