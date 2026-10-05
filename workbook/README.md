# Portfolio Workbook

The Excel workbook in this directory contains the analytical model supporting
the Charlotte–Mecklenburg Population Health Intelligence project.

The workbook demonstrates:

- Power Query ETL
- Multi-year mortality data integration
- Population-data transformation
- Age-group mapping
- Crude and age-specific mortality-rate calculations
- Cause-specific analysis
- Data-quality validation
- Executive dashboard development

## Refreshing the Data

The Power Query model uses the `ProjectDataPath` parameter to control source
file locations.

The public portfolio version contains a placeholder source path to protect
local system information.

To refresh the queries, download the corresponding source files, update
`ProjectDataPath` to the local source directory, and confirm that the source
filenames match those referenced by the queries.

The workbook can be reviewed without refreshing the source queries.
