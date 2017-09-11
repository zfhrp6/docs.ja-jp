---
title: "方法 : Visual Basic でファイルをダウンロードする"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- downloading Internet resources, files
- downloading files
- remote computers, downloading from
- files, downloading
- files, transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8988b922df921c2de3e2c4f6d7a8e98887ba7b0a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="04885-102">方法 : Visual Basic でファイルをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="04885-102">How to: Download a File in Visual Basic</span></span>
<span data-ttu-id="04885-103"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> メソッドを使用すると、リモート ファイルをダウンロードして、指定した場所へ保存できます。</span><span class="sxs-lookup"><span data-stu-id="04885-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="04885-104">`ShowUI` パラメーターを `True` に設定した場合、ダウンロードの進行状況を示すダイアログ ボックスが表示されます。ユーザーは、このダイアログ ボックスで操作をキャンセルすることもできます。</span><span class="sxs-lookup"><span data-stu-id="04885-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="04885-105">既定では、同じ名前を持つ既存のファイルは上書きされません。既存のファイルを上書きするには、`overwrite` パラメーターを `True` に設定します。</span><span class="sxs-lookup"><span data-stu-id="04885-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>  
  
 <span data-ttu-id="04885-106">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="04885-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="04885-107">ドライブ名が有効ではない (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="04885-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="04885-108">必要な認証が付与されていない (<xref:System.UnauthorizedAccessException> または <xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="04885-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="04885-109">指定した `connectionTimeout` 内にサーバーが応答しない (<xref:System.TimeoutException>)。</span><span class="sxs-lookup"><span data-stu-id="04885-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>  
  
-   <span data-ttu-id="04885-110">要求が Web サイトにより拒否された (<xref:System.Net.WebException>)。</span><span class="sxs-lookup"><span data-stu-id="04885-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="04885-111">ファイル名からファイルの内容を判断しないでください。</span><span class="sxs-lookup"><span data-stu-id="04885-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="04885-112">たとえば、Form1.vb というファイルは Visual Basic のソース ファイルではない可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="04885-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="04885-113">アプリケーションでデータを使用する前に、入力をすべて検証してください。</span><span class="sxs-lookup"><span data-stu-id="04885-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="04885-114">ファイルの内容が予想どおりでないことがあり、ファイルの内容を読み取るメソッドが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="04885-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
### <a name="to-download-a-file"></a><span data-ttu-id="04885-115">ファイルをダウンロードするには</span><span class="sxs-lookup"><span data-stu-id="04885-115">To download a file</span></span>  
  
-   <span data-ttu-id="04885-116">`DownloadFile` メソッドを使用してファイルをダウンロードします。その際、ターゲット ファイルの場所を表す文字列または URI と、ファイルを格納する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="04885-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="04885-117">この例では、`WineList.txt` ファイルを `http://www.cohowinery.com/downloads` からダウンロードし、`C:\Documents and Settings\All Users\Documents` に保存します。</span><span class="sxs-lookup"><span data-stu-id="04885-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>  
  
     <span data-ttu-id="04885-118">[!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="04885-118">[!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]</span></span>  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="04885-119">タイムアウト間隔を指定して、ファイルをダウンロードには</span><span class="sxs-lookup"><span data-stu-id="04885-119">To download a file, specifying a time-out interval</span></span>  
  
-   <span data-ttu-id="04885-120">`DownloadFile` メソッドを使用してファイルをダウンロードします。その際、ターゲット ファイルの場所を表す文字列または URI、ファイルを格納する場所、およびタイムアウト間隔 (ミリ秒単位、既定値は 1000) を指定します。</span><span class="sxs-lookup"><span data-stu-id="04885-120">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="04885-121">この例では、タイムアウト間隔に 500 ミリ秒を指定し、`WineList.txt` ファイルを `http://www.cohowinery.com/downloads` からダウンロードして、`C:\Documents and Settings\All Users\Documents` に保存します。</span><span class="sxs-lookup"><span data-stu-id="04885-121">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>  
  
     <span data-ttu-id="04885-122">[!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="04885-122">[!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]</span></span>  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="04885-123">ユーザー名とパスワードを指定して、ファイルをダウンロードするには</span><span class="sxs-lookup"><span data-stu-id="04885-123">To download a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="04885-124">`DownLoadFile` メソッドを使用してファイルをダウンロードします。その際、ターゲット ファイルの場所を表す文字列または URI、ファイルを格納する場所、ユーザー名、およびパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="04885-124">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="04885-125">この例では、ユーザー名に `anonymous` を、パスワードに空白を指定し、`WineList.txt` ファイルを `http://www.cohowinery.com/downloads` からダウンロードして、`C:\Documents and Settings\All Users\Documents` に保存します。</span><span class="sxs-lookup"><span data-stu-id="04885-125">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>  
  
     <span data-ttu-id="04885-126">[!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="04885-126">[!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="04885-127">`DownLoadFile` メソッドで使用される FTP プロトコルは、パスワードを含む情報をプレーンテキストで送信するため、重要な情報の送信には使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="04885-127">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04885-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="04885-128">See Also</span></span>  
 <span data-ttu-id="04885-129"><xref:Microsoft.VisualBasic.Devices.Network></span><span class="sxs-lookup"><span data-stu-id="04885-129"><xref:Microsoft.VisualBasic.Devices.Network></span></span>   
 <span data-ttu-id="04885-130"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A></span><span class="sxs-lookup"><span data-stu-id="04885-130"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A></span></span>   
 <span data-ttu-id="04885-131">[方法: ファイルをアップロードする](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md) </span><span class="sxs-lookup"><span data-stu-id="04885-131">[How to: Upload a File](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md) </span></span>  
 [<span data-ttu-id="04885-132">方法: ファイル パスを解析する</span><span class="sxs-lookup"><span data-stu-id="04885-132">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)

