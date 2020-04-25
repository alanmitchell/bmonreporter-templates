# bmonreporter-templates

This repository holds Jupyter Notebook templates and configuration information that is
used by the [bmonreporter](https://github.com/alanmitchell/bmonreporter) application.
The Jupyter Notebooks are found in the 'templates' directory and the 
[`config.yaml` configuration file](https://github.com/alanmitchell/bmonreporter-templates/blob/master/config.yaml)
that controls which BMON servers that are processed, the AWS S3 bucket where the final reports
are placed, and the format of the reports is found in the root of this repository.

This repository serves as an example for creating other repositories holding Jupyter report
templates.  The requirements for a similar repo are:

* a `config.yaml` file in the root of the repo.
* a `templates` directory, and within that directory a `building` and an `organization`
  subdirectory, each holding Jupyter Notebooks that produce the reports.  The notebooks have
  no naming requirements.

A reasonable approach is to fork this repo and then modify the configuration file and Jupyter notebooks
to suit your needs.  New notebooks can be added and unneeded notebooks can be deleted as required.

## Notes about creating Jupyter Notebook Templates

* After refining and testing a Notebook, using the "Cell, All Output, Clear" menu option will remove all graphs
  and output from the Notebook, substantially reducing it's size.  Be sure to save the Notebook after
  executing the command.
* If you want a report template to only be applied to certain buildings or organizations, you
  can do a test on the `building_id` or `org_id` in the cell following the Parameter cell.  Raise
  an error if you do not want to proceed further with report creation.  For example, the code below
  ensures that the report will only be applied to buildings 23 and 44:

```python
if building_id not in (23, 44):
    raise RuntimeError('Not Applicable')
```
