---
layout: "post"
---
I've been learning a lot how to handle files with PHP and furthermore AWS s3. The general flow is to upload the file from the client's browser to a temporary location on the server, process and check the file to add name, check size, filetype, etc. Then upload it to AWS s3. 
```
 if(isset($_FILES['image'])){ #Set the files attributes before uploading
      $errors= array();
      $file_name = $_FILES['image']['name'];
      $file_size = $_FILES['image']['size'];
      $file_tmp = $_FILES['image']['tmp_name'];
...
      move_uploaded_file($file_tmp,"TEMP_DIR/".$file_name); #Upload the file to a temp directory for further processing
```

The next step is to upload the file from the server instance in to AWS s3 bucket. There are several ways to accomplish this, using text strings, images, or files.
```
$result = $client->putObject(array(
    'Bucket'     => $bucket,
    'Key'        => '$userName/data_from_file.txt', #IMPORTANT uploads a file to a specific user's directory inside a bucket. 
    'SourceFile' => $pathToFile,
    'Metadata'   => array(
        'date' => '$currentDate',
        'username' => '$userName'
    )
));
```

There are some problems which may arise at this stage. I need to watch out for file names and sanitize them properly. File names such as "../file.txt" or "$someUser/file.txt" may cause problems in the upload scripts. I will most likely need to disallow usage of symbols in the file names. Next time I will talk about getting objects from AWS s3 to list them for viewing and downloading. 
