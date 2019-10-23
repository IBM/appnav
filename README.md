# IBM Application Navigator

IBM Application Navigator is a tool that extends the Kubernetes® console to provide display, inspection, understanding, and
navigation of applications comprised of Kubernetes resources and existing middleware, such as WebSphere Application Server.
AppNav extends the open source [Kubernetes Application Navigator (kAppNav)](http://kappnav.io) by providing integration to
WebSphere ND Cells and Liberty Collectives, providing visibility to existing and containerized applications.

## Documentation

This repository is the primary source of documentation IBM Application Navigator, bundeled as part of the Cloud Pak for Applications.

Critical install documentation is available in Knowledge Center.

## Documentation Strategy

Because IBM Application Navigator (AppNav) extends Kubernetes Application Navigator (kAppNav),
a sound documentation strategy is required to ensure minimial duplication and promote reuse of existing documentation.
Before contributing documentation for AppNav, consider whether the documentation is better provided in kAppNav.

### Goals:
- Reduce duplication, promote re-use and cross linking
- Demonstrate inheritance from the open source
- Each ‘tier’ of documentation is sufficient for the audience but can rely on a ‘lower tier’ for elaboration of details

### Non-goals:
- Upsell from kAppNav to AppNav

## Documentation Structure
- IBM Application Navigator
  - Installation documentation: Knowledge Center (link TBD)
  - Usage documentation: https://github.com/IBM/appnav
- Kabanero
  - kabanero.io guide for Application Navigator + Kabanero Collections ([appsody](http://appsody.dev) + [kappnav](http://kappnav.io))
- Kubernetes Application Navigator
  - See kappnav.io and https://github.com/kappnav/README

