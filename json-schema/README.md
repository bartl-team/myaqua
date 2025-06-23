## JSON Schema

```bash
# Fetch the original schema
curl -O https://raw.githubusercontent.com/aquaproj/aqua/main/json-schema/registry.json

# Allow additional properties like "x-"
jq 'walk(
  if type == "object" and .type == "object" and has("additionalProperties")
  then .additionalProperties = true
  else .
  end
)' registry.json > relaxed-registry.json
```
