Ultimaker Cura Definition Files
===============================

The "cura_defaults" directory contain the "fdmprinter.def.json" and
"fdmextruder.def.json" files from Ultimaker Cura corresponding to the
CuraEngine in use. These files provide reasonable defaults for all settings.
They also define formulas for recomputing linked settings. Symple Slicer will
use these formulas to compute settings that are not given in the Machine or
Print Profiles and when updating linked settings.

Both "fdmprinter.def.json" and "fdmextruder.def.json" should be kept in sync
with upstream Ultimaker Cura and the upstream CuraEngine. This ensures that
the correct settings will be used for the engine. These files should not be
modified to make it easy to replace them whenever the CuraEngine is upgraded.

In the case that a setting is required by CuraEngine but is otherwise missing
from the official Ultimaker Cura definitions files, they may be defined in
"fdmprinter_errata.def.json"

Symple Slicer Machine and Print Profiles
========================================

The profiles in "machine_profile" and "print_profiles" are used to override
defaults provided by the "cura_defaults" files. These files are specific to
Symple Slicer and do not have corresponding files in Ultimaker Cura. These
profiles are meant to be human-readable and follow the [TOML specification].

The printer profiles are used for printer and toolhead parameters; the print
profiles are used for material and quality parameters. No distinction is
made between printer/toolheads or material/quality because such settings are
often highly interrelated.

When writing profiles, the files in "cura_defaults" can serve as a reference
for the names and meanings of the settings that may be overriden.

Dealing Linked Settings and Settings Propagation
================================================ 

If a settings is overridden, the change will propagate to linked settings
according to the formulas in the "cura_defaults" files.

To understand how settings are linked, inspect the "value" and "resolve"
fields in "fdmprinter.def.json" and "fdmextruder.def.json" files for the
settings in question. These formulas specify how and when a setting will
change in response to a change to some other setting or settings.

References:
===========

[TOML specification] https://github.com/toml-lang/toml