### ****** THIS FILE CAN BE DELETED ******

## OpenAPI Specification Naming

The build expects the Open API spec file name to be prefixed with `.openapi.yml`

## OpenAPI Specification VERSION

The version in the Open API spec file should be set to `0.0.0`.

The actual version will be driven by the GitHub version and applied during the build. See [OPENAPI-SPEC-VERSIONING](../../../../docs/OPENAPI-SPEC-VERSIONING.md) for more details.

## Schemas

So that the generated Java classes have proper names the schema files should live under the directory `./schema` and the file name should be the same as the expected class name
