---
title: "How to: Write Event Information to a Text File (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "event logs [Visual Studio], writing event information"
  - "text files, writing event information to a text file"
  - "events [Visual Basic], writing event information to a text file"
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Write Event Information to a Text File (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生したイベントに関する情報をログに記録できます。  この例では、`My.Application.Log.WriteEntry` メソッドを使用してトレース情報のログをログ ファイルに記録する方法を示します。  
  
### ファイル ログ リスナーを構成するには  
  
1.  **ソリューション エクスプローラー**で app.config を右クリックし、**\[開く\]** をクリックします。  
  
     または  
  
     app.config ファイルがない場合は、次の操作を行います。  
  
    1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
    2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[アプリケーション構成ファイル\]** をクリックします。  
  
    3.  **\[追加\]** をクリックします。  
  
2.  アプリケーション構成ファイルで `<listeners>` セクションを見つけます。  
  
     \<listeners\> セクションは、最上位の \<configuration\> セクションに入れ子になった \<system.diagnostics\> セクションにさらに入れ子になっている、名前属性が "DefaultSource" の \<source\> セクションにあります。  
  
3.  その `<listeners>` セクションに次の要素を追加します。  
  
    ```  
    <add name="FileLogListener" />  
    ```  
  
4.  最上位の `<configuration>` セクションに入れ子になっている `<system.diagnostics>` セクションで、`<sharedListeners>` セクションを見つけます。  
  
5.  その `<sharedListeners>` セクションに次の要素を追加します。  
  
    ```  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     `customlocation` 属性の値をログ ディレクトリに変更します。  
  
    > [!NOTE]
    >  リスナーのプロパティの値を設定するには、プロパティと同じ名前の属性を使用します。ただし、名前のすべての文字を小文字にします。  たとえば、`location` 属性と `customlocation` 属性は、<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> プロパティと <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> プロパティの値を設定します。  
  
### イベント情報をファイル ログに書き込むには  
  
-   `My.Application.Log.WriteEntry` メソッドまたは `My.Application.Log.WriteException` メソッドを使用して、ファイル ログに情報を書き込みます。  詳細については、「[方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)」および「[How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)」を参照してください。  
  
     アセンブリに対してファイル ログ リスナーを設定すると、そのアセンブリで `My.Application.Log` が書き込んだすべてのメッセージを受け取ります。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)