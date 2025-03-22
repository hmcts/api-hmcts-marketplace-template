# api-cp-template

Naming conventions will follow the pattern of generic to specific. For example, an API schema definition would be in the format of:

```
api-cp-[case-type]-{product-domain}-{name-of-entity}
```
The optional _case-type_ parameter could be:

* civil 
* crime 
* family 
* tribunal

HMCTS manages all Civil, Criminal, Family (separate from civil), and Tribunal cases.


## GitHub Action OpenAPI Validator

The `validate` action uses the OpenAPI Schema provided via the environment variable `OAPI_SCHEMA_URL` or defaults to `https://raw.githubusercontent.com/OAI/OpenAPI-Specification/refs/tags/3.1.1/schemas/v3.0/schema.yaml`

### Run validation locally

It is assumed that python is installed on your machine.

Install the required dependencies by running the following command:
```bash
  pip install -r .github/scripts/requirements.txt
```

Run the following command to validate the OpenAPI specification:
```bash
python ./.github/scripts/validate_openapi.py ./openapi
```
or to test the validation script run:
```bash
python ./.github/scripts/validate_openapi.py ./.github/examples
```
