---
title: "チュートリアル: My.Application.Log による情報の書き込み先の変更 (Visual Basic) | Microsoft Docs"
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
  - "My.Application.Log オブジェクト, チュートリアル"
  - "イベント ログ, 出力場所の変更"
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# チュートリアル: My.Application.Log による情報の書き込み先の変更 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生したイベントに関する情報をログに記録できます。 このチュートリアルでは、既定の設定をオーバーライドして、`Log` オブジェクトによる書き込み先を他のログ リスナーに変更する方法を示します。  
  
## 必須コンポーネント  
 `Log` オブジェクトは、複数のログ リスナーに情報を書き込むことができます。 ログ リスナーの構成を変更する前に、現在の構成を確認する必要があります。 詳細については、「[チュートリアル : My.Application.Log による情報の書き込み先の確認](../Topic/Walkthrough:%20Determining%20Where%20My.Application.Log%20Writes%20Information%20\(Visual%20Basic\).md)」を参照してください。  
  
 必要に応じて、「[How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)」および「[方法 : アプリケーション イベント ログに書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)」も参照してください。  
  
### リスナーを追加するには  
  
1.  **ソリューション エクスプローラー**で app.config を右クリックし、**\[開く\]** を選択します。  
  
     または  
  
     app.config ファイルがない場合は、次の操作を行います。  
  
    1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
    2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[アプリケーション構成ファイル\]** をクリックします。  
  
    3.  **\[追加\]** をクリックします。  
  
2.  `<sources>` セクション内にある、`name` 属性が "DefaultSource" の `<source>` セクションで、`<listeners>` セクションを見つけます。`<sources>` セクションは、最上位の `<configuration>` セクション内の `<system.diagnostics>` セクションにあります。  
  
3.  その `<listeners>` セクションに次の要素を追加します。  
  
    ```  
    <!-- Uncomment to connect the application file log. -->  
    <!-- <add name="FileLog" /> -->  
    <!-- Uncomment to connect the event log. -->  
    <!-- <add name="EventLog" /> -->  
    <!-- Uncomment to connect the event log. -->  
    <!-- <add name="Delimited" /> -->  
    <!-- Uncomment to connect the XML log. -->  
    <!-- <add name="XmlWriter" /> -->  
    <!-- Uncomment to connect the console log. -->  
    <!-- <add name="Console" /> -->  
    ```  
  
4.  `Log` のメッセージを受け取らせるログ リスナーをコメントから外します。  
  
5.  最上位の `<configuration>` セクション内の `<system.diagnostics>` セクションで、`<sharedListeners>` セクションを見つけます。  
  
6.  その `<sharedListeners>` セクションに次の要素を追加します。  
  
    ```  
    <add name="FileLog"  
         type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
               Microsoft.VisualBasic, Version=8.0.0.0,   
               Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
         initializeData="FileLogWriter" />  
    <add name="EventLog"  
         type="System.Diagnostics.EventLogTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="sample application"/>  
    <add name="Delimited"   
         type="System.Diagnostics.DelimitedListTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="c:\temp\sampleDelimitedFile.txt"  
         traceOutputOptions="DateTime" />  
    <add name="XmlWriter"  
         type="System.Diagnostics.XmlWriterTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="c:\temp\sampleLogFile.xml" />  
    <add name="Console"  
         type="System.Diagnostics.ConsoleTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="true" />  
    ```  
  
7.  app.config ファイルの内容は次の XML のようになります。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
              <!-- Uncomment to connect the application file log. -->  
              <!-- <add name="FileLog" /> -->  
              <!-- Uncomment to connect the event log. -->  
              <!-- <add name="EventLog" /> -->  
              <!-- Uncomment to connect the event log. -->  
              <!-- <add name="Delimited" /> -->  
              <!-- Uncomment to connect the XML log. -->  
              <!-- <add name="XmlWriter" /> -->  
              <!-- Uncomment to connect the console log. -->  
              <!-- <add name="Console" /> -->  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="Information" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
               initializeData="FileLogWriter" />  
          <add name="EventLog"  
               type="System.Diagnostics.EventLogTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="sample application"/>  
          <add name="Delimited"   
               type="System.Diagnostics.DelimitedListTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="c:\temp\sampleDelimitedFile.txt"  
               traceOutputOptions="DateTime" />  
          <add name="XmlWriter"  
               type="System.Diagnostics.XmlWriterTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="c:\temp\sampleLogFile.xml" />  
          <add name="Console"  
               type="System.Diagnostics.ConsoleTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="true" />  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
### リスナーを再構成するには  
  
1.  `<sharedListeners>` セクションで、リスナーの `<add>` 要素を見つけます。  
  
2.  `type` 属性はリスナーの型の名前を表します。 この型は <xref:System.Diagnostics.TraceListener> クラスを継承する必要があります。 正しい型が確実に使用されるよう、型名には厳密な名前を使用します。 詳細については、後述の「厳密な名前を指定された型を参照するには」を参照してください。  
  
     使用できる型のいくつかを以下に示します。  
  
    -   <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=fullName> リスナー。ファイル ログに書き込みます。  
  
    -   <xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName> リスナー。`initializeData` パラメーターで指定された、コンピューターのイベント ログに情報を書き込みます。  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=fullName> リスナーおよび <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=fullName> リスナー。`initializeData` パラメーターで指定されたファイルに書き込みます。  
  
    -   <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=fullName> リスナー。コマンド ライン コンソールに書き込みます。  
  
     他の型のログ リスナーが情報を書き込む先については、その型のドキュメントを参照してください。  
  
3.  アプリケーションは、ログ リスナー オブジェクトを作成するときに、コンストラクターのパラメーターとして `initializeData` 属性を渡します。`initializeData` 属性の意味はトレース リスナーによって異なります。  
  
4.  ログ リスナーの作成後にアプリケーションはリスナーのプロパティを設定します。 これらのプロパティは、`<add>` 要素の他の属性で定義されています。 特定のリスナーのプロパティの詳細については、そのリスナーの型のドキュメントを参照してください。  
  
### 厳密な名前を指定された型を参照するには  
  
1.  ログ リスナーとして正しい型を確実に使用するために、完全修飾型名と厳密な名前のアセンブリ名を使用する必要があります。 厳密な名前を指定された型の構文は次のとおりです。  
  
     \<*型名*\>, \<*アセンブリ名*\>, \<*バージョン番号*\>, \<*カルチャ*\>, \<*厳密な名前*\>  
  
2.  次のコード例は、完全修飾された型の厳密な名前を確認する方法を示します。この例では "System.Diagnostics.FileLogTraceListener" です。  
  
     [!code-vb[VbVbalrMyApplicationLog#15](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-changing-where-my-application-log-writes-information_1.vb)]  
  
     次に示すのが出力です。これを使用して、前述の「リスナーを追加するには」の手順で示した方法で、厳密な名前を指定された型を一意に参照できます。  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## 参照  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:System.Diagnostics.TraceListener>   
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=fullName>   
 <xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName>   
 [How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)   
 [方法 : アプリケーション イベント ログに書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)