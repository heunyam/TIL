# HTTP Content-Disposition

멘토링 깜짝 미션으로 HTTP Content-Disposition에 대해 알아보게 되었다



## Content-Disposition 란?

HTTP Response Header에 들어간다

1. `Content-Dispostion: inline`

   default 값이며 주로 웹상에서 표시하는 데이터라고 생각하면 된다.

2. `Content-Dispostion: attachment, filename="index.jpg"`

   다운로드 되는 파일은 attachment로 값을 설정한다.

   filename 옵션으로 파일명까지 지정해 줄 수 있다. 



## multipart

Body에 담길 데이터가 엄청 커서 response가 여러 번 가야 할 때, 아래와 같은 형식으로 나간다.

```
# 1
Content-type: multipart/form-data; boundary="boundary"

# 2
Content-Disposition: form-data; name="field1"

# 3
Content-Disposition: form-data; name="field2"; filename="example.file"
```



## 실제로 해보기

```
    if as_attachment:
        if attachment_filename is None:
            raise TypeError("filename unavailable, required for sending as attachment")

        if not isinstance(attachment_filename, text_type):
            attachment_filename = attachment_filename.decode("utf-8")

        try:
            attachment_filename = attachment_filename.encode("ascii")
        except UnicodeEncodeError:
            filenames = {
                "filename": unicodedata.normalize("NFKD", attachment_filename).encode(
                    "ascii", "ignore"
                ),
                "filename*": "UTF-8''%s" % url_quote(attachment_filename, safe=b""),
            }
        else:
            filenames = {"filename": attachment_filename}

        headers.add("Content-Disposition", "attachment", **filenames)
```

