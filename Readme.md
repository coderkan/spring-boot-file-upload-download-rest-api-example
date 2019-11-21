## Spring Boot File Upload / Download Rest API Example

This project provides to upload files and preview images. It's simply serving images via url.

You can easily use for your requirements.

* [Rest APIs](#added-rest-apis)
* [Demo](#demo)
* [Usage Of Project](#usage-of-project)

## Added Rest APIs

Added methods and their usage like below;

>Upload single image request.

```bash
curl -X POST -H "Content-Type: multipart/form-data"  -F "file=@sample.jpg" http://localhost:8080/uploadFile  | json_pp
```
>Upload single image resonse.
```json	
{
    "filePreviewUri" : "http://localhost:8080/preview/172303_19112019_QTSKBVDE.jpg",
    "fileName" : "172303_19112019_QTSKBVDE.jpg",
    "size" : 3331132,
    "fileDownloadUri" : "http://localhost:8080/downloadFile/172303_19112019_QTSKBVDE.jpg",
    "fileType" : "image/jpeg"
}
```

>Upload multiple image request.

```bash
curl -X POST -H "Content-Type: multipart/form-data"  -F "files=@sample.jpg" -F "files=@sample.jpg" -F "files=@sample.jpg" http://localhost:8080/uploadMultipleFiles | json_pp
	
```

>Upload multiple image response.

```json
[
    {
        "fileDownloadUri" : "http://localhost:8080/downloadFile/173330_19112019_FGMRZULS.jpg",
        "fileType" : "image/jpeg",
        "fileName" : "173330_19112019_FGMRZULS.jpg",
        "filePreviewUri" : "http://localhost:8080/preview/173330_19112019_FGMRZULS.jpg",
        "size" : 3331132
    },
    {
        "fileType" : "image/jpeg",
        "fileDownloadUri" : "http://localhost:8080/downloadFile/173330_19112019_WFKMAQOK.jpg",
        "fileName" : "173330_19112019_WFKMAQOK.jpg",
        "size" : 3331132,
        "filePreviewUri" : "http://localhost:8080/preview/173330_19112019_WFKMAQOK.jpg"
    },
    {
        "filePreviewUri" : "http://localhost:8080/preview/173331_19112019_SROPPYBA.jpg",
        "size" : 3331132,
        "fileType" : "image/jpeg",
        "fileName" : "173331_19112019_SROPPYBA.jpg",
        "fileDownloadUri" : "http://localhost:8080/downloadFile/173331_19112019_SROPPYBA.jpg"
    }
]
```

> Get all image names in server request.

```bash
curl -X GET http://localhost:8080/listImages | json_pp
```
> Get all image names in server response.
```json
[
    {
        "preview" : "http://localhost:8080/preview/073e8b03-1260-4018-b697-932aa25720c7.PNG",
        "name" : "073e8b03-1260-4018-b697-932aa25720c7.PNG"
    },
    {
        "name" : "084347_20112019_OTQDOMRP.jpg",
        "preview" : "http://localhost:8080/preview/084347_20112019_OTQDOMRP.jpg"
    },
    {
        "name" : "12Factor.PNG",
        "preview" : "http://localhost:8080/preview/12Factor.PNG"
    },
    {
        "name" : "163351_19112019_ARHAWFUL.PNG",
        "preview" : "http://localhost:8080/preview/163351_19112019_ARHAWFUL.PNG"
    },
    {
        "preview" : "http://localhost:8080/preview/163653_19112019_CREMROBE.PNG",
        "name" : "163653_19112019_CREMROBE.PNG"
    }
    ....
]
```
>Get image with name
```bash
	http://localhost:8080/preview/IMAGENAME.PNG|JPG
```
This request is returning an image, if image name is not valid return a default image from resources.


## Demo

![Gif Demo](demo.gif)


## Usage Of Project

**Tutorial**: [Uploading an Downloading files with Spring Boot](https://www.callicoder.com/spring-boot-file-upload-download-rest-api-example/)

## Steps to Setup

**1. Clone the repository** 

```bash
git clone https://github.com/callicoder/spring-boot-file-upload-download-rest-api-example.git
```

**2. Specify the file uploads directory**

Open `src/main/resources/application.properties` file and change the property `file.upload-dir` to the path where you want the uploaded files to be stored.

```
file.upload-dir=/Users/callicoder/uploads
```

**2. Run the app using maven**

```bash
cd spring-boot-file-upload-download-rest-api-example
mvn spring-boot:run
```

That's it! The application can be accessed at `http://localhost:8080`.

You may also package the application in the form of a jar and then run the jar file like so -

```bash
mvn clean package
java -jar target/file-demo-0.0.1-SNAPSHOT.jar
```