# AnonSharingLib
Anonymous Upload Library for .NET

`Download:`[https://github.com/jackkoolage/AnonSharingLib/releases](https://github.com/jackkoolage/AnonSharingLib/releases)<br>
`Help:`[https://github.com/jackkoolage/AnonSharingLib/wiki](https://github.com/jackkoolage/AnonSharingLib/wiki)<br>
`NuGet:`
[![NuGet](https://img.shields.io/nuget/v/DeQmaTech.AnonSharingLib.svg?style=flat-square&logo=nuget)](https://www.nuget.org/packages/DeQmaTech.AnonSharingLib)<br>


# Features:
* Assemblies for .NET 4.5.2+
* Just one external reference (Newtonsoft.Json)
* Easy to Use & installation using NuGet
* Upload/Download tracking support
* Proxy Support
* Upload/Download cancellation support

# List of functions:
**Image**
* BoringHostUpload
* CasImagesUpload
* CheveretoUpload
* DirectUploadUpload
* FiveCMUpload
* FramaPicUploadLocal
* FramaPicUploadRemote
* FunkyImgUpload
* GameRuUpload
* GeekPicUpload
* GyazoUpload
* IfotkiUpload
* ImageBanUpload
* ImgaaUpload
* ImgBBUpload
* ImggmiRemoteUpload
* ImggmiUpload
* ImgSafeUpload
* ImgurUpload
* JuploadUpload
* NoelShackUpload
* NoelShackUploadRemote
* PasteBoardUpload
* PicABoxUpload
* PicIjoUpload
* PicImageUpload
* PicPlusUpload
* PostImagesUpload
* PostImagesUploadRemote
* PrntScrUpload
* PutreUpload
* ResmimRemoteUpload
* ResmimUpload
* SafeFieryMeUploadLocal
* SafeFieryMeUploadRemote
* SavePhotoUpload
* SavePiceUploadRemote
* SubefotosUpload
* TechPowerUpUpload
* TechPowerUpUploadRemote
* UploadVaaRedUpload
* VGYUpload
* ZupImagesUpload

**File**
* AnonFilesUpload
* AnonymousFilesUpload
* DataFileHostUpload
* EasyUploadUpload
* FileBinUpload
* FileCargoUpload
* FileConvoyUpload
* FileDropperUpload
* FileIOUpload
* FileMailUpload
* FileTeamUpload
* FileTransferUpload
* GoFileIOUpload
* HostrUpload
* OneFichierUpload
* RacatyUpload
* SendFileUpload
* SendItUpload
* SendSpaceUpload
* SolidFilesUpload
* SwissTransferUpload
* TakeAFile
* UploadEEUpload
* UppItUpload
* UptoboxUpload
* WeTransferUpload
* WikiSendUpload
* YourFileLinkUpload
* ZippyShareUpload

**PDF**
* PDFHostUpload
* DocDroidUpload

**Txt**
* HasteBinUpload
* DumpzUpload
* FedoraProjectUpload
* PasteUbuntuUpload
* PasteeeUpload

**Shorten**
* BitLy
* ISGD
* SooGD
* Teknik
* TinyUrl
* TurlCa
* VGD
* Rebrandly
* TinyCC

**Webpage**
* HostHtml5Upload
* SimpleSiloUpload
* FileTownUpload
* HtputUpload
* PushbulletUpload

**Tools**
* FileSharingChecker
* FullPageScreenCapture
* html2pdfrocket_HTML2PDF
* PDFaceUpload_UrlToPDF
* PDFResizerUpload_ImgsToPDF
* PDFShiftUploadLocal_HTML2PDF
* PDFShiftUploadRemote_Url2PDF
* SejdaUpload_ImgsToPDF
* WaybackArchive


# Code simple:
```vb
''set proxy and connection options
Dim con As New AnonSharingLib.ConnectionSettings With {.CloseConnection = True, .TimeOut = TimeSpan.FromMinutes(30), .Proxy = New AnonSharingLib.ProxyConfig With {.SetProxy = True, .ProxyIP = "127.0.0.1", .ProxyPort = 8888, .ProxyUsername = "user", .ProxyPassword = "pass"}}

''set client
Dim CLNT As AnonSharingLib.IClient = New AnonSharingLib.HClient(con)

''image
Dim imgConfig = New AnonSharingLib.ImgClient.ImageUploadConfig
With imgConfig
    .ImgObject = "c:\\photo.jpg"
    .ImgObjectType = AnonSharingLib.ImgClient.ImageSentType.file
    .FileName = "photo.jpg"
    .ReportCls = New Progress(Of AnonSharingLib.ReportStatus)(Sub(ReportClass As AnonSharingLib.ReportStatus) Console.WriteLine(String.Format("{0} - {1}% - {2}", String.Format("{0}/{1}", (ReportClass.BytesTransferred), (ReportClass.TotalBytes)), CInt(ReportClass.ProgressPercentage), ReportClass.TextStatus)))
    .cToken = (New Threading.CancellationTokenSource()).Token
End With

Await CLNT.Img(imgConfig).BoringHostUpload

''file
Dim fileConfig = New AnonSharingLib.FileClient.FileUploadConfig
With fileConfig
    .FileObject = "c:\\temp.zip"
    .FileObjectType = AnonSharingLib.FileClient.FileSentType.file
    .FileName = "temp.zip"
    .ReportCls = New Progress(Of AnonSharingLib.ReportStatus)(Sub(ReportClass As AnonSharingLib.ReportStatus) Console.WriteLine(String.Format("{0} - {1}% - {2}", String.Format("{0}/{1}", (ReportClass.BytesTransferred), (ReportClass.TotalBytes)), CInt(ReportClass.ProgressPercentage), ReportClass.TextStatus)))
    .cToken = (New Threading.CancellationTokenSource()).Token
End With

Await CLNT.File(fileConfig).AnonFilesUpload

''txt
Dim txtConfig = New AnonSharingLib.TxtClient.TextUploadConfig
With txtConfig
    .TextObject = "c:\\class.cs"
    .TextObjectType = AnonSharingLib.TxtClient.TextSentType.file
    .FileName = "class.cs"
    .ReportCls = New Progress(Of AnonSharingLib.ReportStatus)(Sub(ReportClass As AnonSharingLib.ReportStatus) Console.WriteLine(String.Format("{0} - {1}% - {2}", String.Format("{0}/{1}", (ReportClass.BytesTransferred), (ReportClass.TotalBytes)), CInt(ReportClass.ProgressPercentage), ReportClass.TextStatus)))
    .cToken = (New Threading.CancellationTokenSource()).Token
End With

Await CLNT.Txt(txtConfig).DumpzUpload

''Webpage
Dim htmlConfig = New AnonSharingLib.FileClient.FileUploadConfig
With htmlConfig
    .FileObject = "c:\\page.html"
    .FileObjectType = AnonSharingLib.FileClient.FileSentType.file
    .FileName = "page.html"
    .ReportCls = New Progress(Of AnonSharingLib.ReportStatus)(Sub(ReportClass As AnonSharingLib.ReportStatus) Console.WriteLine(String.Format("{0} - {1}% - {2}", String.Format("{0}/{1}", (ReportClass.BytesTransferred), (ReportClass.TotalBytes)), CInt(ReportClass.ProgressPercentage), ReportClass.TextStatus)))
    .cToken = (New Threading.CancellationTokenSource()).Token
End With

Await CLNT.Webpage(htmlConfig).FileTownUpload

''PDF
Dim pdfConfig = New AnonSharingLib.FileClient.FileUploadConfig With { _
    .FileObject = "c:\\book.pdf",
    .FileObjectType = AnonSharingLib.FileClient.FileSentType.file,
    .FileName = "book.pdf",
    .ReportCls = New Progress(Of AnonSharingLib.ReportStatus)(Sub(ReportClass As AnonSharingLib.ReportStatus) Console.WriteLine(String.Format("{0} - {1}% - {2}", String.Format("{0}/{1}", (ReportClass.BytesTransferred), (ReportClass.TotalBytes)), CInt(ReportClass.ProgressPercentage), ReportClass.TextStatus))),
    .cToken = (New Threading.CancellationTokenSource()).Token}

Await CLNT.Pdf(pdfConfig).DocDroidUpload

''Shorten
Await CLNT.Shorten(New Uri("https://www.youtube.com/watch")).BitLy


```

# Tests:
* [Image](https://github.com/jackkoolage/AnonSharingLib/wiki/Image)
* [File](https://github.com/jackkoolage/AnonSharingLib/wiki/FILE)
* [PDF](https://github.com/jackkoolage/AnonSharingLib/wiki/PDF)
* [Txt](https://github.com/jackkoolage/AnonSharingLib/wiki/TXT)
* [Webpage](https://github.com/jackkoolage/AnonSharingLib/wiki/Webpage)
* [Shorten](https://github.com/jackkoolage/AnonSharingLib/wiki/Shorten)


