---
title: "How to: Upload a File in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "networks, uploading files"
  - "files, uploading"
  - "uploading files"
  - "UploadFile method"
  - "My.Computer.Network.UploadFile method"
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# How to: Upload a File in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> メソッドを使用すると、ファイルをアップロードして、リモートの場所に格納できます。  `ShowUI` パラメーターを `True` に設定した場合、アップロードの進行状況を示すダイアログ ボックスが表示され、ユーザーが操作をキャンセルできます。  
  
### ファイルをアップロードするには  
  
-   `UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、およびアップロード先のディレクトリの場所を表す文字列または URI \(Uniform Resource Identifier\) を指定します。この例では、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。  
  
     [!code-vb[VbResourceTasks#6](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/how-to-upload-a-file_1.vb)]  
  
### 操作の進行状況を表示しながらファイルをアップロードするには  
  
-   `UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、およびアップロード先のディレクトリの場所を表す文字列または URI を指定します。  この例では、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。ユーザー名やパスワードは指定せず、進行状況を表示し、アップロードのタイムアウト間隔は 500 ミリ秒に設定しています。  
  
     [!code-vb[VbResourceTasks#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/how-to-upload-a-file_2.vb)]  
  
### ユーザー名とパスワードを指定してファイルをアップロードするには  
  
-   `UploadFile` メソッドを使用してファイルをアップロードします。その際、対象ファイルの場所、アップロード先のディレクトリの場所を表す文字列または URI、およびユーザー名とパスワードを指定します。  この例では、ユーザー名に `anonymous` を、パスワードに空白を指定して、`Order.txt` ファイルを `http://www.cohowinery.com/uploads.aspx` にアップロードします。  
  
     [!code-vb[VbResourceTasks#8](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/how-to-upload-a-file_3.vb)]  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外がスローされる可能性があります。  
  
-   ローカル ファイルのパスが無効な場合 \(<xref:System.ArgumentException>\)。  
  
-   認証が失敗した場合 \(<xref:System.Security.SecurityException>\)。  
  
-   接続がタイムアウトした場合 \(<xref:System.TimeoutException>\)。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>   
 [How to: Download a File](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)   
 [方法 : ファイル パスを解析する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)