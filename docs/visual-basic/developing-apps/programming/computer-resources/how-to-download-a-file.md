---
title: "方法: Visual Basic でファイルをダウンロードする | Microsoft Docs"
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
author: stevehoag
ms.author: shoag
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bd37b52d12876dad6ec4b2a1bb34f4987f933c08
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-download-a-file-in-visual-basic"></a>方法 : Visual Basic でファイルをダウンロードする
<xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> メソッドを使用すると、リモート ファイルをダウンロードして、特定の場所に格納できます。 `ShowUI` パラメーターを `True` に設定した場合、ダウンロードの進行状況を示すダイアログ ボックスが表示されます。ユーザーは、このダイアログ ボックスで操作をキャンセルすることもできます。 既定では、同じ名前を持つ既存のファイルは上書きされません。既存のファイルを上書きするには、`overwrite` パラメーターを `True` に設定します。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   ドライブ名が有効でない (<xref:System.ArgumentException>)。  
  
-   必要な認証が与えられていない (<xref:System.UnauthorizedAccessException> または <xref:System.Security.SecurityException>)。  
  
-   指定した `connectionTimeout` 内にサーバーが応答しない (<xref:System.TimeoutException>)。  
  
-   Web サイトが要求を拒否した (<xref:System.Net.WebException>)。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
> [!IMPORTANT]
>  ファイル名からファイルの内容を判断しないでください。 たとえば、Form1.vb というファイルは Visual Basic のソース ファイルではない可能性もあります。 アプリケーションでデータを使用する前に、入力をすべて検証してください。 ファイルの内容が予想どおりでないことがあり、ファイルの内容を読み取るメソッドが失敗する可能性があります。  
  
### <a name="to-download-a-file"></a>ファイルをダウンロードするには  
  
-   `DownloadFile` メソッドを使用してファイルをダウンロードします。その際、ターゲット ファイルの場所を表す文字列または URI と、ファイルを格納する場所を指定します。 この例では、`WineList.txt` ファイルを `http://www.cohowinery.com/downloads` からダウンロードし、`C:\Documents and Settings\All Users\Documents` に保存します。  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a>タイムアウト間隔を指定して、ファイルをダウンロードには  
  
-   `DownloadFile` メソッドを使用してファイルをダウンロードします。その際、ターゲット ファイルの場所を表す文字列または URI、ファイルを格納する場所、およびタイムアウト間隔 (ミリ秒単位、既定値は 1000) を指定します。 この例では、タイムアウト間隔に 500 ミリ秒を指定し、`WineList.txt` ファイルを `http://www.cohowinery.com/downloads` からダウンロードして、`C:\Documents and Settings\All Users\Documents` に保存します。  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>ユーザー名とパスワードを指定して、ファイルをダウンロードするには  
  
-   `DownLoadFile` メソッドを使用してファイルをダウンロードします。その際、ターゲット ファイルの場所を表す文字列または URI、ファイルを格納する場所、ユーザー名、およびパスワードを指定します。 この例では、ユーザー名に `anonymous` を、パスワードに空白を指定し、`WineList.txt` ファイルを `http://www.cohowinery.com/downloads` からダウンロードして、`C:\Documents and Settings\All Users\Documents` に保存します。  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  `DownLoadFile` メソッドで使用される FTP プロトコルは、パスワードを含む情報をプレーンテキストで送信するため、重要な情報の送信には使用しないでください。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Devices.Network>   
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>   
 [方法: ファイルをアップロードする](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)   
 [方法: ファイル パスを解析する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)

