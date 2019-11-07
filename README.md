# IBM Application Navigator

IBM Application Navigator is a tool that extends the Kubernetes® console to provide display, inspection, understanding and expose day 2 operations of applications comprised of Kubernetes resources and existing middleware, such as WebSphere Application Server. AppNav extends the open source [Kubernetes Application Navigator (kAppNav)](https://kappnav.io) by providing integration to WebSphere ND Cells and Liberty Collectives, enabling visibility to existing and containerized applications.

## [Documentation](https://ibm.github.io/appnav/)

This repository is the primary source of documentation IBM Application Navigator. The actual documentation starts [here: https://ibm.github.io/appnav/](https://ibm.github.io/appnav/). IBM Application Navigator is installed as part of IBM Cloud Pak for Applications.  The installation documentation is available in [Knowledge Center](https://www.ibm.com/support/knowledgecenter/SSCSJL/install-icpa.html).

## Documentation Issues

If you find any issues with the documentation, please [open an issue](https://github.com/IBM/appnav/issues/new). Functional issues should be reported using IBM's support ticket process.

## Documentation Strategy

Because IBM Application Navigator (AppNav) extends Kubernetes Application Navigator (kAppNav),
a sound documentation strategy is required to ensure minimal duplication and to reuse existing documentation and to promote the kAppNav project.
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
  - Installation documentation: [Knowledge Center](https://www.ibm.com/support/knowledgecenter/SSCSJL/install-icpa.html)
  - Usage documentation: https://ibm.github.io/appnav/
- Kabanero
  - kabanero.io guide for Application Navigator + Kabanero Collections ([appsody](https://appsody.dev) + [kappnav](https://kappnav.io))
- Kubernetes Application Navigator
  - See kappnav.io and https://github.com/kappnav/README

## Notes for Creating Documentation

The goal of the UI is to be as intuitive as possible. Similarly, the goal of the documentation is to be as instructive as possible, without being overly burdensome. The documentation should assume minimal knowledge on the part of the user, while still being quick to follow for experienced users (i.e. next steps are obvious, clearly indicated, and an experienced user can skip ahead quickly). To that end, augment the documentation with screenshots, command examples and code (YAML) examples.

### Guidance for creating screenshots

1. Screenshots should include as much of the UI as is necessary for context. Unless important, the browser URL bar does not need to be included.
  * Annotated screenshots should use the "Bradley Hand" font (available by default on MacOS) and dark blue shape outlines.
1. Small, focused screenshots are encouraged when filling in forms

