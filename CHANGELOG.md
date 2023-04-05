# Change Log

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/)
and this project adheres to [Semantic Versioning](http://semver.org/).

## [Unreleased]

## [0.0.2] - 2023-04-05

### Added

### Changed

- Changed the postgres docker image to use the lighter `alpine version`
- Permanently set the `MB_DB_HOST` env variable to `db` which is the host for the postgres service on the default docker-compose network formed.
- Changed the names of the services and container names in the docker-compose file to more aesthetic ones.

### Fixed

## [0.0.1] - 2019-03-15

### Added

- Initial set up of docker-compose file with the default postgres image and default metabase image 

### Changed

### Fixed
