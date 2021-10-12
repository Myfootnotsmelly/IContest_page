# gitbook-plugin-extra-html
This is a plugin of gitbook to add some html to render result

```json
{
    "plugins": [
        "extra-html"
    ],
    "pluginsConfig": {
        "extra-html": {
            "footer": {
                "files": [
                    "_footer.html"
                ],
                "modules": {
                    "divider": true,
                    "donate": {
                        "qrCodes": [
                            {
                                "image": "图片地址",
                                "label": "微信"
                            },
                            {
                                "image": "图片地址",
                                "label": "支付宝"
                            }
                        ]
                    }
                }
            },
            "header": {}
        }
    }
}
```