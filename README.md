## Purpose

This repo provides XULE support for ferc validation rulesets.

The repo contains ferc form ruleset files that support validation with the latest version of XULE.

## Versions
There are different versions of the rulesets that accompany each taxonomy version.  The repo has seperate branches for each taxonomy version.  The main branch reflects the validation rules for the latest taxonomy release.

## Validating a Filing
FERC forms are validated during the submission process with a series of checks.  These validations can also be downloaded from the root of this repository and invoked as .zip files using Arelle *version 2.36.4* or later and the XULE processor *version 3.0.30044* or later. 

The command to validate a filing is as follows (update the _{location}_ text for the corresponding ruleset to use and instance to check):

`arellecmdline --plugins xule --xule-rule-set {location of form ruleset}/Form1.zip -f {location of instance}/sampleF1.xbrl -v --logFile {location of output}/log.xml`

The validation ruleset.zip files can be invoked from this repository by using the `/raw/` attribute in the URL. The following example will check a sample posted to the FERC Xendr templates repository:

`.\arellecmdline.exe --plugins xule --xule-rule-set https://github.com/xbrlus/ferc-validation-rulesets/raw/2024-04-01/ValidationRuleset_Form2.zip -f https://raw.githubusercontent.com/xbrlus/ferc-xendr-rulesets/2024-04-01/Form2/sampleInstances/Sample_Form_2.xbrl -v --logFile log.xml`

Parameters used by XULE in the above Arelle command are as follows:
--plugins: This argument references the XULE plugin called by Arelle.  This is included as part of the Arelle distribution.
--xule-rule-set: This argument references the location of the ruleset zip file provided by FERC.
-f: This argument is used to define the location of the instance file.
-v: This argument is required to indicate that the Arelle processor should perform a validation.
--logFile: This argument is used to define the output file where the results of the rules is written to.

Check it out with [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/xbrlus/xule/jupyter?filepath=sample.ipynb) or [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/xbrlus/xule/blob/jupyter/sample-colab.ipynb): after running the first cell to create a Python environment with Arelle and XULE, paste the command below into the "2. Run XULE against an XBRL report" step (replacing what's in the cell), then run the cell. This will take about 75 seconds to load the taxonomy, process the filing and run FERC validations:

`!arelleCmdLine --plugins xule --xule-rule-set https://github.com/xbrlus/ferc-validation-rulesets/raw/2024-04-01/ValidationRuleset_Form2.zip -f https://raw.githubusercontent.com/xbrlus/ferc-xendr-rulesets/2024-04-01/Form2/sampleInstances/Sample_Form_2.xbrl -v --logFormat="[%(messageCode)s] %(message)s"`
