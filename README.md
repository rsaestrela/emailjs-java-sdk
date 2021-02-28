![build-status](https://github.com/rsaestrela/emailjs-java-sdk/workflows/build/badge.svg)

# EmailJS Java SDK

Non-official EmailJS Java SDK to interact with [EMailJS.com](https://www.emailjs.com/) REST API. 
All the sources are dynamically generated using [openapi-generator](https://github.com/OpenAPITools/openapi-generator/tree/master/modules/openapi-generator-maven-plugin).
Only the `send` operation necessary to send e-mails is implemented. 

Feel free to reuse the [OAS created for this purpose](https://raw.githubusercontent.com/rsaestrela/emailjs-java-sdk/main/emailjs-rest-api.yml).

### How to use the SDK

Add the dependency to your project:

```
<dependency>
  <groupId>me.estrela</groupId>
  <artifactId>emailjs-java-sdk</artifactId>
  <version>1.0.24</version>
</dependency>
```

The library is only published in GitHub, so you may need to add the repository configuration:

```
<repositories>
  <repository>
    <id>github</id>
    <url>https://maven.pkg.github.com/rsaestrela/emailjs-java-sdk</url>
  </repository>
</repositories>
```

Ready to send e-mails!

``` java
var api = new DefaultApi(Configuration.getDefaultApiClient());
var body = new SendRequest();
body.setTemplateId("your_template_id");
body.serviceId("your_service_id");
body.setAccessToken("your_access_token");
body.setUserId("your_user_id");
// Jackson, GSON or any other can be used to create a JSON object
var params = new ObjectMapper().createObjectNode(); 
params.put("to", "mail@to.com");
body.setTemplateParams(params);
try {
    api.send(body);
    // or api.sendAsync();
} catch (ApiException e) {
    System.err.println("Status code: " + e.getCode());
    System.err.println("Reason: " + e.getResponseBody());
    System.err.println("Response headers: " + e.getResponseHeaders());
    e.printStackTrace();
}
```

For more information about EMailJS API please consult the [official docs](https://www.emailjs.com/docs/).

### Contribute

If something doesn't look right, feel free to open an issue or submit a PR.

### License

This library comes without any warranty - just take it or leave it. Also, the author is not connected to EmailJS.

[MIT](/LICENSE) &copy; 2021

