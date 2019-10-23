# IBM Application Navigator

IBM Application Navigator is a tool that extends the Kubernetes® console to provide display, inspection, understanding, and
navigation of applications comprised of Kubernetes resources and existing middleware, such as WebSphere Application Server.
AppNav extends the open source [Kubernetes Application Navigator (kAppNav)](https://kappnav.io) by providing integration to
WebSphere ND Cells and Liberty Collectives, enabling visibility to existing and containerized applications.

## Documentation

This repository is the primary source of documentation IBM Application Navigator. Installation documentation is available in Knowledge Center (link TBD).

## Documentation Strategy

Because IBM Application Navigator (AppNav) extends Kubernetes Application Navigator (kAppNav),
a sound documentation strategy is required to ensure minimial duplication and to reuse existing documentation and to promote the kAppNav project.
Before contributing documentation for AppNav, consider whether the documentation is better provided in kAppNav.

### Goals:
- Reduce duplication and promote re-use of existing documentation
- Promote and cross-link to the kAppNav project
- Honor the inheritance from the open source
- Each ‘tier’ of documentation is sufficient for the audience but can rely on a ‘lower tier’ for elaboration of details

### Non-goals:
- Convert kAppNav users to AppNav users

## Documentation Structure
- IBM Application Navigator
  - Installation documentation: Knowledge Center (link TBD)
  - Usage documentation: https://github.com/IBM/appnav/blob/master/start-of-documentation.md
- Kabanero
  - kabanero.io guide for Application Navigator + Kabanero Collections ([appsody](https://appsody.dev) + [kappnav](https://kappnav.io))
- Kubernetes Application Navigator
  - See kappnav.io and https://github.com/kappnav/README

