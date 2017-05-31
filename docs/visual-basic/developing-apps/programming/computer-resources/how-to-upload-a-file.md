---
title: "方法: Visual Basic でファイルをアップロードする | Microsoft Docs"
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1663cc6ad0a6e5f2a940c050c75d403cffd1f53f
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-upload-a-file-in-visual-basic"></a>方法: Visual Basic でファイルをアップロードする
<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> メソッドを使用すると、ファイルをアップロードして、リモートの場所に格納できます。 `ShowUI` パラメーターを `True` に設定した場合、ダウンロードの進行状況を示すダイアログ ボックスが表示され、ユーザーが操作をキャンセルできます。  
  
### <a name="to-upload-a-file"></a>ファイルをアップロードするには  
  
-   `UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、およびアップロード先のディレクトリの場所を表す文字列または URI (Uniform Resource Identifier) を指定します。この例では、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。  
  
     [!code-vb[VbResourceTasks#6](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_1.vb)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>操作の進行状況を表示しながらファイルをアップロードするには  
  
-   `UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、およびアップロード先のディレクトリの場所を表す文字列または URI を指定します。 この例では、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。ユーザー名やパスワードは指定せず、アップロードの進行状況を表示し、タイムアウト間隔は 500 ミリ秒に設定しています。  
  
     [!code-vb[VbResourceTasks#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_2.vb)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>ユーザー名とパスワードを指定してファイルをアップロードするには  
  
-   `UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、アップロード先のディレクトリの場所を表す文字列または URI、およびユーザー名とパスワードを指定します。 この例では、ユーザー名に `anonymous` を、パスワードに空白を指定して、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。  
  
     [!code-vb[VbResourceTasks#8](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_3.vb)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外がスローされる可能性があります。  
  
-   ローカル ファイルのパスが無効な場合 (<xref:System.ArgumentException>)。  
  
-   認証が失敗した場合 (<xref:System.Security.SecurityException>)。  
  
-   接続がタイムアウトした場合 (<xref:System.TimeoutException>)。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>   
 [方法: ファイルをダウンロードする](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)   
 [方法: ファイル パスを解析する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
