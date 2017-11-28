---
title: "方法: Visual Basic でファイルをアップロードする"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8a0fab9b812ddff1f56e9fa203bd297fd70bc47d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="9e301-102">方法: Visual Basic でファイルをアップロードする</span><span class="sxs-lookup"><span data-stu-id="9e301-102">How to: Upload a File in Visual Basic</span></span>
<span data-ttu-id="9e301-103"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> メソッドを利用してファイルをアップロードし、離れた場所に格納できます。</span><span class="sxs-lookup"><span data-stu-id="9e301-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="9e301-104">`ShowUI` パラメーターを `True` に設定した場合、アップロードの進行状況を示すダイアログ ボックスが表示され、ユーザーが操作をキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="9e301-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="9e301-105">ファイルをアップロードするには</span><span class="sxs-lookup"><span data-stu-id="9e301-105">To upload a file</span></span>  
  
-   <span data-ttu-id="9e301-106">`UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、およびアップロード先のディレクトリの場所を表す文字列または URI (Uniform Resource Identifier) を指定します。この例では、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="9e301-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_1.vb)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="9e301-107">操作の進行状況を表示しながらファイルをアップロードするには</span><span class="sxs-lookup"><span data-stu-id="9e301-107">To upload a file and show the progress of the operation</span></span>  
  
-   <span data-ttu-id="9e301-108">`UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、およびアップロード先のディレクトリの場所を表す文字列または URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="9e301-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="9e301-109">この例では、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。ユーザー名やパスワードは指定せず、アップロードの進行状況を表示し、タイムアウト間隔は 500 ミリ秒に設定しています。</span><span class="sxs-lookup"><span data-stu-id="9e301-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_2.vb)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="9e301-110">ユーザー名とパスワードを指定してファイルをアップロードするには</span><span class="sxs-lookup"><span data-stu-id="9e301-110">To upload a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="9e301-111">`UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、アップロード先のディレクトリの場所を表す文字列または URI、およびユーザー名とパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e301-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="9e301-112">この例では、ユーザー名に `anonymous` を、パスワードに空白を指定して、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="9e301-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_3.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9e301-113">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="9e301-113">Robust Programming</span></span>  
 <span data-ttu-id="9e301-114">次の条件を満たす場合は、例外がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9e301-114">The following conditions may throw an exception:</span></span>  
  
-   <span data-ttu-id="9e301-115">ローカル ファイル パスが有効ではありません (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="9e301-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="9e301-116">認証に失敗しました (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="9e301-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="9e301-117">接続がタイムアウトしました (<xref:System.TimeoutException>)。</span><span class="sxs-lookup"><span data-stu-id="9e301-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e301-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e301-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>  
 [<span data-ttu-id="9e301-119">方法 : ファイルをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="9e301-119">How to: Download a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)  
 [<span data-ttu-id="9e301-120">方法: ファイル パスを解析する</span><span class="sxs-lookup"><span data-stu-id="9e301-120">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
