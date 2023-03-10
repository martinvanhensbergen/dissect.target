The purpose of the docs directory
=================================

This *docs* directory is intended to aid `developers` in the process of writing and validating API documentation for this repository. If you are not developing documentation, you should visit https://docs.dissect.tools for all current documentation.

If you do inted to work on this API documentation, this directory provides functionality to assist you in reviewing your changes in documentation before submitting them. 

You can do the following:
1. Build an HTML version of the documentation to help you manually inspect the documentation for any render issues
2. Automatically check if URLs to external websites are not broken.

The sections below show how this works.

Preparing your environment
--------------------------

The API documentation is built using [Sphinx](https://www.sphinx-doc.org/en/master/) and familiarity with this tooling is assumed.

To prepare your environment, create a new virtual environment (if necessary) and install the dependencies:

```bash
pip install -r requirements.txt
```

Build and show a preview of the documentation
---------------------------------------------

Documentation is created from the *docstrings* in the Python code. Before committing your changes, it is good to review how the rendered HTML will look.

Assuming you have set up your environment as above, you can create an HTML version of the API documentation by invoking the following command:

```bash
make html
```

This will create a `build` directory with all the generated documentation. Apart from the styling, this will show you the result of your documentation as it will appear on https://docs.dissect.tools if your changes are accepted.

**Note**: It is not unusual that warnings and errors appear; you can safely ignore them as long as the building of the documentation does not fail in its entirety.

After the build process has finished, you can view the documentation in, for example Firefox:

```bash
firefox build/html/index.html
```

If you experience build issues, you can clean up your environment using:

```bash
make clean
```


Checking external URLs
----------------------

If you include external website links in your API documentation, it is good to validate if these links are still valid before commiting your changes.

Assuming you have set up your environment as above, you can check for broken links by invoking the following command:

```bash
make linkcheck
```

You will see the results of the checks in your terminal, but they can also be found in the file `build/linkcheck/output.txt`.

### Processing the output of linkcheck

Each URL that is checked will result in a line containing the  file and linenumber containing the URL, the result of the check (see below) and the actual URL that was checked.

Use the following table to process the output:
| Result Code      | Meaning | Resolve    |
|------------------|---------|------------|
| ok      | The URL resolves without issues  | No change required |
| redirect | The URL resolves, but is redirected in the process | No change required |
| broken | The URL doesn't appear to be working | Determine the cause of failure: check in the HTML if the URL is rendered properly. Does the website block the check but does the URL function when using a browser? In the latter case, the link can be kept, otherwise consider removing the link.
| *other* | An unforeseen error occured | Manually check if the link is still valid; remove the link if necessary. |

Important guidelines
--------------------

? Misschien link naar iets in Core?

sources
blok
link formatting






