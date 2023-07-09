# pandas_errors_analytics
This is dummy repo with error analytics for https://github.com/pandas-dev/pandas/pull/54046 

I ran the following command in both Gitpod and docker after building pandas in both environments (in the cloud and locally):
`pytest pandas/tests/io/test_sql.py pandas/tests/io/parser/test_network.py pandas/tests/io/test_fsspec.py pandas/tests/io/test_parquet.py pandas/tests/io/test_s3.py pandas/tests/io/excel/test_readers.py pandas/tests/io/excel/test_style.py pandas/tests/io/json/test_compression.py pandas/tests/io/json/test_pandas.py pandas/tests/io/xml/test_to_xml.py > myoutput.log`

Using diffchecker in VSCode showed that they have exactly the same errors, which means that either there is an issue with the version pinning of the some of the dependencies in the [requirements file](https://raw.githubusercontent.com/pandas-dev/pandas/main/requirements-dev.txt) downloaded in the docker file; or a lack of access to endpoints required for testing. [This is expected behavior](https://pandas.pydata.org/docs/dev/development/contributing_codebase.html#contributing-running-tests):

<img width="720" alt="Screen Shot 2023-07-08 at 8 40 58 PM" src="https://github.com/theuerc/pandas_errors_analytics/assets/60138157/98eb37fc-2390-44c8-a391-174aac10bc22">


<img width="1385" alt="Screen Shot 2023-07-08 at 8 34 30 PM" src="https://github.com/theuerc/pandas_errors_analytics/assets/60138157/03ee2258-45d3-4d6d-a149-f828107d0ff5">

- `docker_full_test_results.log` is the full output of the command above for the docker build run locally on my computer
- `docker_summary_test_results` is just the summary test info for the output
- `gitpod_full_test_results.log` and `gitpod_summary_test_results.log` are the same for the Gitpod build
- `myoutput.log` is the full `pytest pandas` output in the Gitpod environment. I don't have the equivalent for the docker build because my computer cannot run it.
