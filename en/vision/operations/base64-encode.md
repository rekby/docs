# Encode a file to Base64

To pass an image file to the Vision API, convert the file content into text in the Base64 format:

{% include [base64-encode-command](../../_includes/vision/base64-encode-command.md) %}

Pass the content of the resulting `output.txt` file in the request body's `content` property:

```json
{
    "folderId": "ajk55f3mblj12eghq2oe",
    "analyze_specs": [{
        "content": "iVBORw0KGgo...",
        ...
    }]
}
```

