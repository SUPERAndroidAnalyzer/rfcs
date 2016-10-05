# SUPER RFCs
[SUPER RFCs]: #super-rfcs

Many changes, including bug fixes and documentation improvements can be implemented and reviewed
via the normal GitHub pull request workflow.

Some changes though are "substantial", and we ask that these be put through a bit of a design
process and produce a consensus among the SUPER community and the SUPER team.

The "RFC" (request for comments) process is intended to provide a consistent and controlled path
for new features to enter the software, or its surrounding libraries, so that all stakeholders can
be confident about the direction the software is evolving in.

## Table of Contents
[Table of Contents]: #table-of-contents
* [Opening](#super-rfcs)
* [Table of Contents]
* [When you need to follow this process]
* [Before creating an RFC]
* [What the process is]
* [The role of the shepherd]
* [The RFC life-cycle]
* [Reviewing RFC's]
* [Implementing an RFC]
* [RFC Postponement]
* [Help this is all too informal!]


## When you need to follow this process
[When you need to follow this process]: #when-you-need-to-follow-this-process

You need to follow this process if you intend to make "substantial" changes to SUPER, any of its
surrounding libraries, or the RFC process itself. What constitutes a "substantial" change is
evolving based on community norms and varies depending on what part of the ecosystem you are
proposing to change, but may include the following:

   - Any backwards incompatible change.
   - Any new dependency on external libraries, or dependency removal.
   - Any new module in the core software.
   - Substantial modifications to templates, or the creation of new templates.
   - Removing features of the software.
   - Changes in configuration files.

Some changes do not require an RFC:

   - Rephrasing, reorganizing, refactoring, or otherwise "changing shape does not change meaning".
   - Additions that strictly improve objective, numerical quality criteria (warning removal,
     speedup, better platform coverage, more parallelism, trap more errors, etc.)
   - Additions only likely to be *noticed by* other developers-of-SUPER, invisible to
     users-of-SUPER.

If you submit a pull request to implement a new feature without going through the RFC process, it
may be closed with a polite request to submit an RFC first.

## Before creating an RFC
[Before creating an RFC]: #before-creating-an-rfc

A hastily-proposed RFC can hurt its chances of acceptance. Low quality proposals, proposals for
previously-rejected features, or those that don't fit into the near-term roadmap, may be quickly
rejected, which can be demotivating for the unprepared contributor. Laying some groundwork ahead of
the RFC can make the process smoother.

Although there is no single way to prepare for submitting an RFC, it is generally a good idea to
pursue feedback from other project developers beforehand, to ascertain that the RFC may be
desirable: having a consistent impact on the project requires concerted effort toward
consensus-building.

As a rule of thumb, receiving encouraging feedback from long-standing project developers, and
particularly members of the SUPER team is a good indication that the RFC is worth pursuing.

## What the process is
[What the process is]: #what-the-process-is

In short, to get a major feature added to SUPER, one must first get the RFC merged into the RFC
repo as a markdown file. At that point the RFC is 'active' and may be implemented with the goal of
eventual inclusion into SUPER.

* Fork the RFC repo https://github.com/SUPERAndroidAnalyzer/rfcs
* Copy `0000-template.md` to `text/0000-my-feature.md` (where 'my-feature' is descriptive. don't
  assign an RFC number yet).
* Fill in the RFC. Put care into the details: RFCs that do not present convincing motivation,
  demonstrate understanding of the impact of the design, or are disingenuous about the drawbacks or
  alternatives tend to be poorly-received.
* Submit a pull request. As a pull request the RFC will receive design feedback from the larger
  community, and the author should be prepared to revise it in response.
* The SUPER team triages RFC PRs. The team will either close the PR (for RFCs that clearly will not
  be accepted) or assign it a *shepherd*. The shepherd is a trusted developer who is familiar with
  the RFC process, who will help to move the RFC forward, and ensure that the right people see and
  review it.
* Build consensus and integrate feedback. RFCs that have broad support are much more likely to make
  progress than those that don't receive any comments. The shepherd assigned to your RFC should
  help you get feedback from SUPER developers as well.
* The shepherd may schedule meetings with the author and/or relevant stakeholders to discuss the
  issues in greater detail.
* The team will discuss the RFC PR, as much as possible in the comment thread of the PR itself.
  Offline discussion will be summarized on the PR comment thread.
* RFCs rarely go through this process unchanged, especially as alternatives and drawbacks are
  shown. You can make edits, big and small, to the RFC to clarify or change the design, but make
  changes as new commits to the PR, and leave a comment on the PR explaining your changes.
  Specifically, do not squash or rebase commits after they are visible on the PR.
* Once both proponents and opponents have clarified and defended positions and the conversation has
  settled, the RFC will enter its *final comment period* (FCP). This is a final opportunity for the
  community to comment on the PR and is a reminder for all members of the team to be aware of the
  RFC.
* The FCP lasts one week. It may be extended if consensus between team members cannot be reached.
  At the end of the FCP,  the team will either accept the RFC by merging the pull request,
  assigning the RFC a number (corresponding to the pull request number), at which point the RFC is
  'active', or reject it by closing the pull request. How exactly the SUPER team decides on an RFC
  is up to the team.

## The role of the shepherd
[The role of the shepherd]: #the-role-of-the-shepherd

During triage, every RFC will either be closed or assigned a shepherd from the team. The role of
the shepherd is to move the RFC through the process. This starts with simply reading the RFC in
detail and providing initial feedback. The shepherd should also solicit feedback from people who
are likely to have strong opinions about the RFC. When this feedback has been incorporated and the
RFC seems to be in a steady state, the shepherd and/or team leader will announce an FCP. In
general, the idea here is to "front-load" as much of the feedback as possible before the point
where we actually reach a decision - by the end of the FCP, the decision on whether or not to
accept the RFC should usually be obvious from the RFC discussion thread. On occasion, there may not
be consensus but discussion has stalled. In this case, the SUPER team will make a decision.

## The RFC life-cycle
[The RFC life-cycle]: #the-rfc-life-cycle

Once an RFC becomes active then authors may implement it and submit the feature as a pull request
to the SUPER repo. Being 'active' is not a rubber stamp, and in particular still does not mean the
feature will ultimately be merged; it does mean that in principle all the major stakeholders have
agreed to the feature and are amenable to merging it.

Furthermore, the fact that a given RFC has been accepted and is 'active' implies nothing about what
priority is assigned to its implementation, nor does it imply anything about whether a SUPER
developer has been assigned the task of implementing the feature. While it is not *necessary* that
the author of the RFC also write the implementation, it is by far the most effective way to see an
RFC through to completion: authors should not expect that other project developers will take on
responsibility for implementing their accepted feature.

Modifications to active RFC's can be done in follow-up PR's. We strive to write each RFC in a
manner that it will reflect the final design of the feature; but the nature of the process means
that we cannot expect every merged RFC to actually reflect what the end result will be at the time
of the next major release.

In general, once accepted, RFCs should not be substantially changed. Only very minor changes should
be submitted as amendments. More substantial changes should be new RFCs, with a note added to the
original RFC. Exactly what counts as a "very minor change" is up to the SUPER team to decide.

## Reviewing RFC's
[Reviewing RFC's]: #reviewing-rfcs

While the RFC PR is up, the shepherd may schedule meetings with the author and/or relevant
stakeholders to discuss the issues in greater detail, and in some cases the topic may be discussed
at a SUPER team meeting. In either case a summary from the meeting will be posted back to the RFC
pull request.

The SUPER team makes final decisions about RFCs after the benefits and drawbacks are well
understood. These decisions can be made at any time, but the team will regularly issue decisions.
When a decision is made, the RFC PR will either be merged or closed. In either case, if the
reasoning is not clear from the discussion in thread, the team will add a comment describing the
rationale for the decision.

## Implementing an RFC
[Implementing an RFC]: #implementing-an-rfc

Some accepted RFC's represent vital features that need to be implemented right away. Other accepted
RFC's can represent features that can wait until some arbitrary developer feels like doing the
work. Every accepted RFC has an associated issue tracking its implementation in the SUPER
repository; thus that associated issue can be assigned a priority via the triage process that the
team uses for all issues in the SUPER repository.

The author of an RFC is not obligated to implement it. Of course, the RFC author (like any other
developer) is welcome to post an implementation for review after the RFC has been accepted.

If you are interested in working on the implementation for an 'active' RFC, but cannot determine if
someone else is already working on it, feel free to ask (e.g. by leaving a comment on the
associated issue).

## RFC Postponement
[RFC Postponement]: #rfc-postponement

Some RFC pull requests are tagged with the 'postponed' label when they are closed (as part of the
rejection process). An RFC closed with "postponed" is marked as such because we want neither to
think about evaluating the proposal nor about implementing the described feature until some time in
the future, and we believe that we can afford to wait until then to do so. Postponed PRs may be
re-opened when the time is right. We don't have any formal process for that, you should ask members
of the SUPER team.

Usually an RFC pull request marked as "postponed" has already passed an informal first round of
evaluation, namely the round of "do we think we would ever possibly consider making this change, as
outlined in the RFC pull request, or some semi-obvious variation of it." (When the answer to the
latter question is "no", then the appropriate response is to close the RFC, not postpone it.)

### Help this is all too informal!
[Help this is all too informal!]: #help-this-is-all-too-informal

The process is intended to be as lightweight as reasonable for the present circumstances. As usual,
we are trying to let the process be driven by consensus and community norms, not impose more
structure than necessary.
