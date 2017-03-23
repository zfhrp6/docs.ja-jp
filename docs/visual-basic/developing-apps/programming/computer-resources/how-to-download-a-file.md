---
title: "How to: Download a File in Visual Basic | Microsoft Docs"
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
  - "downloading Internet resources, files"
  - "downloading files"
  - "remote computers, downloading from"
  - "files, downloading"
  - "files, transferring"
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# How to: Download a File in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> メソッドを使用すると、リモート ファイルをダウンロードして、特定の場所に格納できます。  `ShowUI` パラメーターを `True` に設定した場合、ダウンロードの進行状況を示すダイアログ ボックスが表示され、ユーザーが操作をキャンセルできます。  既定では、同じ名前を持つ既存のファイルは上書きされません。既存のファイルを上書きするには、`overwrite` パラメーターを `True` に設定します。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   ドライブ名が有効でない場合 \(<xref:System.ArgumentException>\)。  
  
-   必要な認証が与えられていない場合 \(<xref:System.UnauthorizedAccessException> または <xref:System.Security.SecurityException>\)。  
  
-   指定した `connectionTimeout` 内にサーバーが応答しない場合 \(<xref:System.TimeoutException>\)。  
  
-   Web サイトが要求を拒否した場合 \(<xref:System.Net.WebException>\)。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  ファイル名からファイルの内容を判断しないでください。  たとえば、Form1.vb というファイルが Visual Basic のソース ファイルではない可能性もあります。  アプリケーションでデータを使用する前に、入力をすべて検証してください。  ファイルの内容が予想どおりでないことがあり、ファイルの内容を読み取るメソッドが失敗する可能性があります。  
  
### ファイルをダウンロードするには  
  
-   `DownloadFile` メソッドを使用してファイルをダウンロードします。その際、対象ファイルの場所を表す文字列または URI、およびファイルを格納する場所を指定します。  この例では、`WineList.txt` ファイルを `http://www.cohowinery.com/downloads` からダウンロードし、`C:\Documents and Settings\All Users\Documents` に保存します。  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### タイムアウト間隔を指定してファイルをダウンロードするには  
  
-   `DownloadFile` メソッドを使用してファイルをダウンロードします。その際、対象ファイルの場所を表す文字列または URI、ファイルを格納する場所、およびミリ秒単位のタイムアウト間隔 \(既定値は 1000\) を指定します。  この例では、タイムアウト間隔に 500 ミリ秒を指定して、`WineList.txt` ファイルを `http://www.cohowinery.com/downloads` からダウンロードし、`C:\Documents and Settings\All Users\Documents` に保存します。  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### ユーザー名とパスワードを指定してファイルをダウンロードするには  
  
-   `DownLoadFile` メソッドを使用してファイルをダウンロードします。その際、対象ファイルの場所を表す文字列または URI、ファイルを格納する場所、ユーザー名、およびパスワードを指定します。  この例では、ユーザー名に `anonymous` を、パスワードに空白を指定して、`WineList.txt` ファイルを `http://www.cohowinery.com/downloads` からダウンロードし、`C:\Documents and Settings\All Users\Documents` に保存します。  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  `DownLoadFile` メソッドで使用される FTP プロトコルは、パスワードを含む情報をプレーンテキストで送信するため、重要な情報の送信には使用しないでください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Devices.Network>   
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>   
 [How to: Upload a File](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)   
 [方法 : ファイル パスを解析する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)