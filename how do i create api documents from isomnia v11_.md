# how do i create api documents from insomnia v11?

In Insomnia v11, there are several methods to create API documentation from your collections. Here are the main approaches:[^1]

## Method 1: Using Insomnia-Documenter CLI Tool

The most popular method is using the `insomnia-documenter` command-line tool, which generates beautiful static HTML documentation.

### Steps:

1. **Add descriptions to your requests** in Insomnia by clicking the arrow on the right side of each request tab to include detailed information that will appear in the documentation[^1]
2. **Export your collection** by going to **File > Export Data > Insomnia v4 (JSON)**[^2][^1]
3. **Generate documentation** using the CLI tool:

```bash
npx insomnia-documenter --config filename.json --output documentation-folder
```

4. **View locally** by serving the generated files:

```bash
cd documentation-folder
npx serve
```

This creates a local server at `http://localhost:5000` where you can view your documentation[^1]

## Method 2: Using Insomnia Plugin

There's also an `insomnia-plugin-documenter` that provides a workspace action labeled "Export HTML Documentation" directly from within Insomnia.[^3]

## Method 3: Design Documents for OpenAPI

For newer versions, Insomnia supports creating **Design Documents** that work with OpenAPI specifications. You can:[^4]

1. Create a new **Design Document** from the dashboard
2. Write your API specification in OpenAPI/YAML format
3. Use the built-in preview pane to see real-time documentation
4. Export the specification for use with other documentation tools

## Method 4: Using Inso CLI

Insomnia also provides the `inso` CLI tool for exporting API specifications :[^5]

```bash
inso export spec [identifier] -o output-file
```


## Method 5: Converting to Swagger/OpenAPI

You can convert Insomnia collections to Swagger documentation using tools like **Swaggymnia**  or VS Code extensions that convert Insomnia JSON to Swagger YAML.[^6][^7]

## Best Practices

- **Add comprehensive descriptions** to all requests, folders, and parameters before exporting[^1]
- **Organize requests into logical folders** (like Auth, Users, etc.) to improve documentation structure[^1]
- **Include example request/response bodies** to make the documentation more helpful[^1]
- **Use environment variables** appropriately, though they may not always translate perfectly to static documentation[^1]

The `insomnia-documenter` approach is the most widely used and generates professional-looking documentation that can be easily deployed to any web server or hosting platform like Netlify.[^2]
<span style="display:none">[^10][^11][^12][^13][^14][^15][^16][^17][^18][^19][^20][^21][^22][^23][^24][^25][^26][^27][^28][^29][^8][^9]</span>

<div align="center">⁂</div>

[^1]: https://lightrains.com/blogs/create-api-documentation-insomnia-documenter/

[^2]: https://dev.to/joselatines/how-to-generate-api-documentation-with-insomnia-18fg

[^3]: https://insomnia.rest/plugins/insomnia-plugin-documenter

[^4]: https://www.digitalocean.com/community/tutorials/how-to-create-documentation-for-your-rest-api-with-insomnia

[^5]: https://developer.konghq.com/inso-cli/reference/export_spec/

[^6]: https://www.blog.labouardy.com/generate-swagger-documentation-from-insomnia-rest-client/

[^7]: https://marketplace.visualstudio.com/items?itemName=rslgp.insomnia-to-swagger

[^8]: https://www.youtube.com/watch?v=1zvkn1_UJ7E

[^9]: https://apidog.com/blog/insomnia-api-documentation/

[^10]: https://developer.konghq.com/insomnia/

[^11]: https://apidog.com/articles/how-to-export-insomnia-collection/

[^12]: https://developer.konghq.com/insomnia/import-export/

[^13]: https://github.com/insodoc/insomnia-documenter

[^14]: https://developer.konghq.com/insomnia/documents/

[^15]: https://connect.cloudblue.com/community/developers/api/rest-clients/insomnia-rest-client/

[^16]: https://docs.proabono.com/documentation/api-overview/what-is-insomnia-the-api-rest-client/

[^17]: https://github.com/Kong/insomnia/issues/8505

[^18]: https://labouardy.com/generate-swagger-documentation-from-insomnia-rest-client/

[^19]: https://insomnia.rest

[^20]: https://insomnia.rest/download

[^21]: https://insomnia.rest/plugins

[^22]: https://www.youtube.com/watch?v=P8N8DwMITqQ

[^23]: https://www.echoapi.com/blog/insomnia-vs-postman-showdown-discover-the-ultimate-tool-for-your-project/

[^24]: https://pesto.tech/resources/top-12-tools-for-api-documentation-in-2024

[^25]: https://www.echoapi.com/blog/getting-started-with-insomnia-how-to-export-and-publish-collections/

[^26]: https://github.com/Kong/insomnia/discussions/3737

[^27]: https://www.reddit.com/r/node/comments/nhwmrx/how_do_you_write_your_api_documentation_any/

[^28]: https://firecamp.io/blog/5-opensource-insomnia-alternatives

[^29]: https://github.com/dwyl/learn-insomnia

