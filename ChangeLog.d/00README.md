# Pending changelog entry directory

This directory contains changelog entries that have not yet been merged
to the changelog file ([`../ChangeLog`](../ChangeLog)).

## What requires a changelog entry?

Write a changelog entry if there is a user-visible change. This includes:

* Bug fixes in the framework or in examples: fixing a security hole,
  fixing broken behavior, fixing the build in some configuration or on some
  platform, etc.
* New features in the framework, new examples, or new platform support.
* Changes in existing behavior. These should be rare. Changes in features
  that are documented as experimental may or may not be announced, depending
  on the extent of the change and how widely we expect the feature to be used.

We generally don't include changelog entries for:

* Documentation improvements.
* Performance improvements, unless they are particularly significant.
* Changes to parts of the code base that users don't interact with directly,
  such as test code and test data.

## Changelog entry file format

A changelog entry file must have the extension `*.txt` and must have the
following format:

## {Section}

### {Subsection} (optional)

**Added**
* Additon

**Deprecated**
* Deprecation

**Changed**
* Change

**Fixed**
* Fix

**Removed**
* Removal

Example entry:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

## Wi-Fi
**Fixed**
* Fixed an issue that Wi-Fi stack may crash when receive AMSDU length bigger then 3200

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The permitted changelog entry categories are as follows:
<!-- Keep this synchronized with STANDARD_CATEGORIES in assemble_changelog.py! -->

    Added
    Changed
    Deprecated
    Fixed
    Removed

Use “Changed” for anything that doesn't fit in the other categories.

## How to write a changelog entry

Section entry starts with two hashtags.
Subsection entry (optional) starts with three hashtags.
Each category entry is surrounded with two asterisks.
Each changelog entry is listed under its category, starts with
one asterisk followed by one space. Lines wrap at 79 characters.

Write full English sentences with proper capitalization and punctuation. Use
the present tense. Use the imperative where applicable. For example: “Fix a
bug in esp_function() ….”

Include GitHub issue numbers where relevant. Use the format “#1234” for an
ESP-IDF issue. Add other external references such as CVE numbers where
applicable.

Credit bug reporters where applicable.

**Explain why, not how**. Remember that the audience is the users of the
framework, not its developers. In particular, for a bug fix, explain the
consequences of the bug, not how the bug was fixed. For a new feature, explain
why one might be interested in the feature. For an API change or a deprecation,
explain how to update existing applications.

See [existing entries](../ChangeLog) for examples.

## How `ChangeLog` is updated

Run [`../scripts/assemble_changelog.py`](../scripts/assemble_changelog.py)
from a Git working copy
to move the entries from files in `ChangeLog.d` to the main `ChangeLog` file.