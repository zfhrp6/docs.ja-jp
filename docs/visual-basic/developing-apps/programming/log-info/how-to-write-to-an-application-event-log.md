---
title: "方法: アプリケーション イベント ログに書き込む (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Computer.EventLog 要素"
  - "WriteEntry メソッド"
  - "My.Computer.EventLog 要素"
  - "イベント ログ, 書き込み先"
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法: アプリケーション イベント ログに書き込む (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生したイベントに関する情報を書き込めます。 この例では、`My.Application.Log` がアプリケーション イベント ログにトレース情報を書き込むようにイベント ログ リスナーを構成する方法を示します。  
  
 セキュリティ ログに書き込むことはできません。 システム ログに書き込むためには、LocalSystem または Administrator アカウントのメンバーであることが必要です。  
  
 イベント ログを参照するには、**サーバー エクスプローラー**または **Windows イベント ビューアー**を使用できます。 詳細については、「[.NET Framework の ETW イベント](../Topic/ETW%20Events%20in%20the%20.NET%20Framework.md)」を参照してください。  
  
> [!NOTE]
>  Windows 95、Windows 98、および Windows ME \(Millennium Edition\) では、イベント ログはサポートされていません。  
  
### イベント ログ リスナーを追加および構成するには  
  
1.  **ソリューション エクスプローラー**で app.config を右クリックし、**\[開く\]** を選択します。  
  
     または  
  
     app.config ファイルがない場合は、次の操作を行います。  
  
    1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
    2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[アプリケーション構成ファイル\]** を選択します。  
  
    3.  **\[追加\]** をクリックします。  
  
2.  アプリケーション構成ファイルで `<listeners>` セクションを見つけます。  
  
     `<listeners>` セクションは、最上位の `<configuration>` セクションに入れ子になった `<system.diagnostics>` セクションにさらに入れ子になっている、名前属性が "DefaultSource" の `<source>` セクションにあります。  
  
3.  その `<listeners>` セクションに次の要素を追加します。  
  
    ```  
    <add name="EventLog"/>  
    ```  
  
4.  最上位の `<configuration>` セクション内の `<system.diagnostics>` セクションで、`<sharedListeners>` セクションを見つけます。  
  
5.  その `<sharedListeners>` セクションに次の要素を追加します。  
  
    ```  
    <add name="EventLog"  
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="APPLICATION_NAME"/>  
    ```  
  
     `APPLICATION_NAME` をアプリケーションの名前に置き換えます。  
  
    > [!NOTE]
    >  通常、アプリケーションがイベント ログに書き込むのはエラーのみです。 ログ出力のフィルター処理の詳細については、「[Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)」を参照してください。  
  
### イベント情報をイベント ログに書き込むには  
  
-   `My.Application.Log.WriteEntry` メソッドまたは `My.Application.Log.WriteException` メソッドを使用して、イベント ログに情報を書き込みます。 詳細については、次のトピックを参照してください。[方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) および[How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     アセンブリに対してイベント ログ リスナーを設定すると、そのアセンブリで `My.Applcation.Log` が書き込んだすべてのメッセージを受け取ります。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)   
 [チュートリアル : My.Application.Log による情報の書き込み先の確認](../Topic/Walkthrough:%20Determining%20Where%20My.Application.Log%20Writes%20Information%20\(Visual%20Basic\).md)