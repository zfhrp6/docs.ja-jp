---
title: "方法: Visual Basic でファイルをアップロードする"
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
- networks, uploading files
- files, uploading
- uploading files
- UploadFile method
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
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
ms.openlocfilehash: 29baf1f420cece6e0b05f9638b30a326178a013d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="96056-102">方法: Visual Basic でファイルをアップロードする</span><span class="sxs-lookup"><span data-stu-id="96056-102">How to: Upload a File in Visual Basic</span></span>
<span data-ttu-id="96056-103"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> メソッドを利用してファイルをアップロードし、離れた場所に格納できます。</span><span class="sxs-lookup"><span data-stu-id="96056-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="96056-104">`ShowUI` パラメーターを `True` に設定した場合、アップロードの進行状況を示すダイアログ ボックスが表示され、ユーザーが操作をキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="96056-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="96056-105">ファイルをアップロードするには</span><span class="sxs-lookup"><span data-stu-id="96056-105">To upload a file</span></span>  
  
-   <span data-ttu-id="96056-106">`UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、およびアップロード先のディレクトリの場所を表す文字列または URI (Uniform Resource Identifier) を指定します。この例では、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="96056-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     <span data-ttu-id="96056-107">[!code-vb[VbResourceTasks#6](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="96056-107">[!code-vb[VbResourceTasks#6](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_1.vb)]</span></span>  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="96056-108">操作の進行状況を表示しながらファイルをアップロードするには</span><span class="sxs-lookup"><span data-stu-id="96056-108">To upload a file and show the progress of the operation</span></span>  
  
-   <span data-ttu-id="96056-109">`UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、およびアップロード先のディレクトリの場所を表す文字列または URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="96056-109">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="96056-110">この例では、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。ユーザー名やパスワードは指定せず、アップロードの進行状況を表示し、タイムアウト間隔は 500 ミリ秒に設定しています。</span><span class="sxs-lookup"><span data-stu-id="96056-110">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     <span data-ttu-id="96056-111">[!code-vb[VbResourceTasks#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="96056-111">[!code-vb[VbResourceTasks#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_2.vb)]</span></span>  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="96056-112">ユーザー名とパスワードを指定してファイルをアップロードするには</span><span class="sxs-lookup"><span data-stu-id="96056-112">To upload a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="96056-113">`UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、アップロード先のディレクトリの場所を表す文字列または URI、およびユーザー名とパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="96056-113">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="96056-114">この例では、ユーザー名に `anonymous` を、パスワードに空白を指定して、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="96056-114">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     <span data-ttu-id="96056-115">[!code-vb[VbResourceTasks#8](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="96056-115">[!code-vb[VbResourceTasks#8](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_3.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="96056-116">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="96056-116">Robust Programming</span></span>  
 <span data-ttu-id="96056-117">次の条件を満たす場合は、例外がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="96056-117">The following conditions may throw an exception:</span></span>  
  
-   <span data-ttu-id="96056-118">ローカル ファイル パスが有効ではありません (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="96056-118">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="96056-119">認証に失敗しました (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="96056-119">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="96056-120">接続がタイムアウトしました (<xref:System.TimeoutException>)。</span><span class="sxs-lookup"><span data-stu-id="96056-120">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96056-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="96056-121">See Also</span></span>  
 <span data-ttu-id="96056-122"><xref:Microsoft.VisualBasic.Devices.Network?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="96056-122"><xref:Microsoft.VisualBasic.Devices.Network?displayProperty=fullName></span></span>   
 <span data-ttu-id="96056-123"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A></span><span class="sxs-lookup"><span data-stu-id="96056-123"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A></span></span>   
 <span data-ttu-id="96056-124">[方法: ファイルをダウンロードする](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md) </span><span class="sxs-lookup"><span data-stu-id="96056-124">[How to: Download a File](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md) </span></span>  
 [<span data-ttu-id="96056-125">方法: ファイル パスを解析する</span><span class="sxs-lookup"><span data-stu-id="96056-125">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)

