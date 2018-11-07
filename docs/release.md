A "FIWARE release" contains versioned releases of all Generic Enablers found
within the [catalogue](https://www.fiware.org/developers/catalogue/). All
components must work seamlessly with the
[current context broker](https://github.com/telefonicaid/fiware-orion/releases/latest)
and each other.

The following timetable is proposed for a typical FIWARE release cycle, where it
is assumed that releases will follow at most a monthly cadence.

## Release Prerequisites

Additional GE development for each release cycle should close by the beginning
of the month - ideally this should mean that all code the development team
wishes to include in the FIWARE release has been:

-   Written
-   Tested
-   Documented
-   Labelled as a [SemVer release](GE_Requirements.md#releases) on **GitHub**

Any proposed [new entries](GE_Checklist.md#new-generic-enablers) to the
catalogue **MUST** have been presented to the TSC

Any component
[transitioning to a full member](GE_Checklist.md#transition-to-full-membership)
of the catalogue **MUST** have completed all "Must" requirements and have been
presented as such to the TSC

## Release timetable

#### Week 1

**Day 1** - The formal commencement of the release process will be announced
during the **first** TSC meeting of the month.

-   A list of release candidates will be collated for the TSC and created in a
    prerelease candidate list on
    [GitHub](https://github.com/Fiware/catalogue/releases)
-   For each Generic Enabler
    -   The latest tagged **GitHub** release is assumed to part of the current
        release cycle unless explicitly informed otherwise in writing.
    -   Where no release is found, the latest tag will be proposed.
    -   Where no tags are found, the latest hash will be proposed.
-   On this basis all GE Owners should immediately either:
    -   Double tag their **existing** approved release version in their GitHub
        repository with `FIWARE_<major>.<minor>`
    -   Send an eMail to FF staff requesting a time extension and propose a new
        version number for inclusion in the release.

#### Week 2

**Day 8** - Any changes to the list created above must be received no later than
the **second** TSC meeting of the month.

-   Proposed new catalogue additions.
-   Proposed transitions to full member status etc.
-   Alterations to the version numbers listed.

Where any further adjustments have been requested, they must be completed within
**three days** of the **second** TSC meeting of the month - i.e. **Day 11**. -
for example:

-   For new entrants, the
    [Minimal Checklist](GE_Checklist.md#new-generic-enablers) for new Generic
    Enablers to be completed.
-   For all Generic Enablers, any missing **GitHub** release tags a new version
    number added.
-   Any other alterations to the codebase completed.

#### Week 3

**Day 15** - The release will be closed with final fixed versions on the
**third** TSC meeting of the month.

-   The finalized list of release enablers for release `FIWARE_<major>.<minor>`
    will added as a tagged release on
    [GitHub](https://github.com/Fiware/catalogue/releases).
-   The prerelease candidates list on **GitHub** will be deleted.
-   Generic Enabler owners who had requested more time should double tag the
    release version in their **GitHub** repository with
    `FIWARE_<major>.<minor>`.
