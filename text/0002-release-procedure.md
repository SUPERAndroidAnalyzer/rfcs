- Feature Name: SUPER Release procedure
- Start Date: 2016-10-07
- RFC PR: [rfcs/#2](https://github.com/SUPERAndroidAnalyzer/rfcs/pull/2)
- Code Repo Issue: [SUPER/#68](https://github.com/SUPERAndroidAnalyzer/super/issues/68)

# Summary
[summary]: #summary

For a correct release system, with reasonable periods, a release system is proposed, where the
release cycle is meant to be 6 weeks, and in that period feature-flagged features will be
stabilized, by using a 3-channel system, with *unstable*, *beta* and *stable* features. This enables
SUPER developers to develop complex features in periods longer than 6 weeks, and gives much more
stable releases.

# Motivation
[motivation]: #motivation

Even if the SUPER team has decided to release a new version of SUPER every 6 weeks, SUPER doesn't
have a protocol that explains how dependencies are updated, how unstable feature development is
managed, or how those 6 weeks are divided. SUPER needs a simple protocol that explains the
procedure to release a new version of SUPER, that is simple enough to be followed and that makes
sure that the releases are as stable and as useful as they can be.

SUPER also needs some way to develop complex features for a longer than a 6 week period. Those
features could require complex tests that can be developed in parallel before integration in final
releases. Furthermore, some features could require big changes that could make final releases
unstable if they are not properly tested during a period bigger than the 6 week release period. This
means that there is also a need for a way to indicate if portions of code should be released in
stable, beta or unstable channels.

The need for three channels comes from the need of having an intermediate channel where unstable
features that are being prepared for final release can be tested. Nevertheless, this option makes
no sense while SUPER is still under version 1.0.0. The main purpose of a stable channel is giving
users backwards compatible changes, which only makes sense once the final version gets released.

This RFC presents a procedure to stabilize features, using *[semver](http://semver.org/)* specially
once SUPER reaches version 1.0.0, and how before that period SUPER releases new features every 6
week period.

# Detailed design
[design]: #detailed-design

In this section, the RFC presents how the design of the new release process is.

## Versioning
[versioning]: #versioning

SUPER versions are divided in two period: pre-1.0.0 and post-1.0.0. All versions lower than version
1.0.0, using *[semver](http://semver.org/)*, are considered pre-releases, while every version after
it is considered a release. Pre-release versions will have its major version number set to 0, while
the minor version will be updated every 6 weeks adding 1 (one) to it. So, 6 weeks after SUPER 0.1.0
is released, version 0.2.0 will be released. Those versions are considered beta versions.

Releases after 1.0.0, starting with 1.0.0 itself are no longer considered beta versions, and will
not contain any feature, explained [below](#features). As with pre-releases, they will be released
every 6 weeks, adding 1 (one) to the minor version. So, 6 weeks after releasing SUPER 1.0.0,
version 1.1.0 will be released. Along with each release, a beta release will be released,
representing the features that will be stabilized in the future release. So, at the same time that
SUPER 1.0.0 is released, beta version for 1.1.0 will be released.

Once in post-1.0.0 period, beta versions will be released every 3 weeks. One at the same time of
the stable release, and one 3 weeks after. Features can only change between the first and the
second beta release in the same 6 week cycle, and no new features can be added once the first beta
version for the cycle is released. So, if 1.0.0 version is released, and 1.1.0 beta is released
with features A, B and C, for stabilization for 1.1.0, the beta release 3 weeks after cannot
contain a feature that is not in A, B or C, but it can reject stabilization of some of all of them.

Stabilizations are decided in the weekly meeting every 3 weeks, before each beta release. All
features that come in the second beta release of the period must be stabilized before the final
release.

Pre-release versions will contain unstable features, but they are meant to be stable enough for
daily use, even if they might change in the future. Features that are not stable enough for
everyday use, in the pre-1.0.0 period will not be released.

## Features
[features]: #features

Every minor change that is not a patch must come with its own feature flag. Features must be listed
in the `Cargo.toml` file, and added to the `unstable` feature as a dependency. Unstable features
will be stabilized by adding them to the `beta` feature as a dependency after the 1.0.0 release
first, and then removing them directly (as the `default` feature will not have dependencies
post-1.0.0). Feature flags will need to be removed once stabilized. Before 1.0.0 version, `default`
features will depend on the `beta` feature.

## Release calendar
[calendar]: #release-calendar

New versions will be tagged on Saturdays every 6 weeks, and released the day after, on Sunday. A
go/no-go meeting will be held the release week, before Saturday, where the release can be postponed
by one week. A new go/no-go meeting will be held next week if this happens.

Beta versions post-1.0.0 will be released the same Sunday of stable releases, and the second beta
version of each cycle will be released 3 weeks after. On the same go/no-go meeting of the stable
release, features to stabilize in the next release will be decided. The week of the second beta
release a go/no-go meeting will be held, before Saturday, and final features to stabilize will be
decided. A no-go decision could be taken, that would postpone the beta release by one week,
requiring a new go/no-go meeting the next week. In this case, next stable release will be postponed
by one week.

No-go decisions must be avoided if possible, specially after the 1.0.0 version. In the case of a
mid-cycle beta release, is preferable to drop a feature stabilization over a no-go decision.
Mid-cycle beta released are not applicable in he pre-1.0.0 period.

# Drawbacks
[drawbacks]: #drawbacks

This release cycle presents some extra work for SUPER developers. It would mean that the team will
probably require to spend more time working in SUPER than what the team has been spending before,
and it will require decisions on stabilizations that could be difficult to take.

# Alternatives
[alternatives]: #alternatives

An alternative would be to make release cycles bigger or smaller. Have more or less release
channels, or have a non-versioned release system.

Not implementing this RFC would mean that our releases are less predictable in time and in
stability.

# Unresolved questions
[unresolved]: #unresolved-questions

 - Is the 6-week release cycle big enough for SUPER developers to develop and stabilize new
   features?
 - Is this process flexible enough to enable new features to be added to the codebase?
