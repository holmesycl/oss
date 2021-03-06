# Exception handling {#concept_32083_zh .concept}

If a request error occurs when you use OSS Node.js SDK usage, an exception is thrown.Detailed information about the error is recorded in the log \(oss\_sdk.log by default\).

## ClientError {#section_0uy_nm2_2f4 .section}

ClientErrors indicate exceptions occurred inside the SDK, for example, parameter setting errors and errors occurred when objects are modified in resumable upload or download tasks.

## ServerError {#section_mlz_4n4_qy8 .section}

ServerErrors are the parsing results of the error messages generated by the server and indicate errors occurred on the server. ServerErrors include the following attributes:

-   status: Indicates the HTTP status code of the error request.
-   code: Indicates the OSS error code.
-   message: Indicates the OSS error message.
-   requestId: Indicates the UUID that uniquely identifies the request. Seek help from OSS development engineers by providing this requestId if necessary.

For more information about common error messages in OSS, see [OSS Error Response](../../../../reseller.en-US/Errors and Troubleshooting/OSS error response.md#).

## Debugging {#section_bhh_3yk_lfb .section}

If ClientErrors or ServerErrors occur when you use OSS Node.js SDK, enable debugging by setting the `DEBUG` environment variable as follows:

```language-bash
DEBUG=ali-oss node app.js
			
```

In a browser environment, set the `localStorage.debug` variable in the console to enable debugging:

```language-js
localStorage.debug = 'ali-oss'
			
```

