# IMG implementation modes

You can use object URLs, API operations, or SDKs to process images in OSS. This topic describes how to use these three methods to process images.

## Add parameters to an object URL

You can add Image Processing \(IMG\) parameters or image styles to the end of the image URL:

-   Use IMG parameters

    Format: `https://bucketname.endpoint/objectname?x-oss-process=image/action,parame_value`

    -   https://bucketname.endpoint/objectname : the URL that is used to access the object. For more information about how to obtain the URL of an object, see [How do I obtain the URL of an uploaded object?](/intl.en-US/Developer Guide/Objects/FAQ/How do I obtain the URL of an uploaded object?.md).
    -   x-oss-process=image/: the fixed parameter, which indicates that the image object is processed by using IMG parameters.
    -   action, Param \_value: the action, parameter, and value of an IMG method. These parameters are used to determine an IMG method. Separate multiple operations with forward slashes \(/\). OSS processes images in the order of IMG parameters. For example, `image/resize,w_200/rotate,90` indicates that OSS resizes the image to a width of 200 pixels, and rotates the image 90°. For more information about the parameters supported by IMG, see [Parameters](/intl.en-US/Developer Guide/Data Processing/Image Processing/Overview.md).
    Example: [http://image-demo.oss-cn-hangzhou.aliyuncs.com/example.jpg?x-oss-process=image/resize,w\_300/quality,q\_90](http://image-demo.oss-cn-hangzhou.aliyuncs.com/example.jpg?x-oss-process=image/resize,w_300,h_300/quality,q_90/watermark,image_cGFuZGEucG5n,t_90,g_se,x_10,y_10)

-   Use style parameters

    Format: `https://bucketname.endpoint/objectname?x-oss-process=style/stylename`

    -   https://bucketname.endpoint/objectname : the URL of the object.
    -   x-oss-process=style/: the fixed parameter, which indicates whether to use image style parameters to process image objects.
    -   stylename: the name of the style that you set in the OSS console. For more information, see [Create a style](/intl.en-US/Developer Guide/Data Processing/Image Processing/Image style.md).
    Example: [http://image-demo.oss-cn-hangzhou.aliyuncs.com/example.jpg?x-oss-process=style/panda\_style](http://image-demo.oss-cn-hangzhou.aliyuncs.com/example.jpg?x-oss-process=style/panda_style)

    If you set a custom delimiter, you can use it to replace `? x-oss-process=style /` to further simplify the URL for IMG. For example, if you set the delimiter to an exclamation point \(!\), the image URL is `<https://bucketname.endpoint/objectname! stylename`. For more information about how to configure custom delimiters, see the "Configure source image protection" section in [Source image protection](/intl.en-US/Developer Guide/Data Processing/Image Processing/Source image protection.md).


The preceding description applies only to objects that allow anonymous access. If your object does not allow anonymous access, you must add IMG to the signature. For more information, see the following topics:

-   [Java SDK](/intl.en-US/SDK Reference/Java/Image processing.md)
-   [Python SDK](/intl.en-US/SDK Reference/Python/Image processing.md)
-   [PHP SDK](/intl.en-US/SDK Reference/PHP/Image processing.md)
-   [Go SDK](/intl.en-US/SDK Reference/Go/Image processing.md)
-   [C SDK](/intl.en-US/SDK Reference/C/Image processing.md)
-   [C++ SDK](/intl.en-US/SDK Reference/C++/IMG.md)
-   [.NET SDK](/intl.en-US/SDK Reference/. NET/Image processing.md)
-   [Android SDK](/intl.en-US/SDK Reference/Android/Image processing.md)
-   [iOS SDK](/intl.en-US/SDK Reference/iOS/IMG.md)
-   [Node.js SDK](/intl.en-US/SDK Reference/Node. js/IMG.md)
-   [browser.js SDK](/intl.en-US/SDK Reference/Browser.js/Image processing.md)

## Use SDKs to process images

You can use IMG or style parameters in SDKs to process images. The following code provides an example on how to use OSS SDK for Java to process images:

-   Use IMG parameters

    When you use IMG parameters to process images, separate multiple operations with forward slashes \(/\).

    ```
    // The endpoint of the China (Hangzhou) region is used in this example. Specify the actual endpoint.
    String endpoint = "http://oss-cn-hangzhou.aliyuncs.com";
    // Security risks may arise if you use the AccessKey pair of an Alibaba Cloud account to log on to OSS because the account has permissions on all API operations. We recommend that you use your RAM user's credentials to call API operations or perform routine operations and maintenance. To create a RAM user, log on to the RAM console.
    String accessKeyId = "<yourAccessKeyId>";
    String accessKeySecret = "<yourAccessKeySecret>";
    String bucketName = "<yourBucketName>";
    String objectName = "<yourObjectName>";
    // Create an OSSClient instance.
    OSS ossClient = new OSSClientBuilder().build(endpoint, accessKeyId, accessKeySecret);
    // Resize the image to a height and width of 100 pixels, and add text watermarks. The content of the watermark is: Hello image service.
    String style = "image/resize,m_fixed,w_100,h_100/watermark,text_SGVsbG8g5Zu-54mH5pyN5YqhIQ";
    GetObjectRequest request = new GetObjectRequest(bucketName, objectName);
    request.setProcess(style);
    ossClient.getObject(request, new File("<example.jpg>"));
    // Shut down the OSSClient instance.
    ossClient.shutdown();
                            
    ```

-   Use style parameters

    ```
    // The endpoint of the China (Hangzhou) region is used in this example. Specify the actual endpoint.
    String endpoint = "http://oss-cn-hangzhou.aliyuncs.com";
    // Security risks may arise if you use the AccessKey pair of an Alibaba Cloud account to log on to OSS because the account has permissions on all API operations. We recommend that you use your RAM user's credentials to call API operations or perform routine operations and maintenance. To create a RAM user, log on to the RAM console.
    String accessKeyId = "<yourAccessKeyId>";
    String accessKeySecret = "<yourAccessKeySecret>";
    String bucketName = "<yourBucketName>";
    String objectName = "<yourObjectName>";
    
    // Create an OSSClient instance.
    OSS ossClient = new OSSClientBuilder().build(endpoint, accessKeyId, accessKeySecret);
    
    // Customize the image style.
    String style = "style/<yourCustomStyleName>";
    GetObjectRequest request = new GetObjectRequest(bucketName, objectName);
    request.setProcess(style);
    
    ossClient.getObject(request, new File("<example.jpg>"));
    
    // Shut down the OSSClient instance.
    ossClient.shutdown();
    ```


For more information about SDK demos for other programming languages, see the following topics:

-   [Java SDK](/intl.en-US/SDK Reference/Java/Image processing.md)
-   [Python SDK](/intl.en-US/SDK Reference/Python/Image processing.md)
-   [PHP SDK](/intl.en-US/SDK Reference/PHP/Image processing.md)
-   [Go SDK](/intl.en-US/SDK Reference/Go/Image processing.md)
-   [C SDK](/intl.en-US/SDK Reference/C/Image processing.md)
-   [C++ SDK](/intl.en-US/SDK Reference/C++/IMG.md)
-   [.NET SDK](/intl.en-US/SDK Reference/. NET/Image processing.md)
-   [Android SDK](/intl.en-US/SDK Reference/Android/Image processing.md)
-   [iOS SDK](/intl.en-US/SDK Reference/iOS/IMG.md)
-   [Node.js SDK](/intl.en-US/SDK Reference/Node. js/IMG.md)
-   [browser.js SDK](/intl.en-US/SDK Reference/Browser.js/Image processing.md)

## Call API operations to process images

You can add IMG or style parameters to the GetObject operation to process images.

-   Use IMG parameters

    Sample requests

    ```
    GET /oss.jpg? x-oss-process=image/resize,w_100 HTTP/1.1
    Host: oss-example.oss-cn-hangzhou.aliyuncs.com
    Date: Fri, 24 Feb 2012 06:38:30 GMT
    Authorization: OSS qn6qrrqxo2oawuk53otfjbyc:UNQDb7GapEgJkcde6OhZ9J*****
    ```

-   Use style parameters

    Sample requests

    ```
    GET /oss.jpg? x-oss-process=style/styleexample HTTP/1.1
    Host: oss-example.oss-cn-hangzhou.aliyuncs.com
    Date: Fri, 24 Feb 2012 06:40:10 GMT
    Authorization: OSS qn6qrrawuk53oqxo2otfjbyc:UNapEgQDb7GJkcde6OhZ9J*****
    ```


## Save processed images

By default, IMG does not save processed images. However, OSS allows you to add the saveas parameter to an IMG request. You can save the processed image as an object to a specified bucket. For more information, see [IMG persistence](/intl.en-US/Developer Guide/Data Processing/Image Processing/Save processed images.md).

