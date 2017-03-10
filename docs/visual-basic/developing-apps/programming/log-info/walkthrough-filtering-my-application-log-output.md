---
title: "チュートリアル: My.Application.Log の出力のフィルター処理 (Visual Basic) | Microsoft Docs"
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
  - "My.Log オブジェクト、出力をフィルター処理"
  - "My.Application.Log オブジェクト、出力をフィルター処理"
  - "アプリケーション イベント ログの出力フィルター"
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# チュートリアル: My.Application.Log の出力のフィルター処理 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

既定のログのフィルター選択を変更する方法についても説明、 `My.Application.Log` からどのような情報が渡されたを制御するため、オブジェクト、 `Log` リスナーおよびリスナーによってどのような情報を記述するオブジェクト。 構成情報は、アプリケーションの構成ファイルに保存されるため、アプリケーションをビルドした後でも、ログ記録の動作を変更します。  
  
## <a name="getting-started"></a>作業の開始  
 各メッセージが `My.Application.Log` 書き込みがログ出力を制御するフィルター機能を使用して、関連付けられている重要度レベル。 このサンプル アプリケーションを使用して `My.Application.Log` いくつかを記述する方法は、さまざまな重大度レベルのメッセージを記録します。  
  
#### <a name="to-build-the-sample-application"></a>サンプル アプリケーションをビルドするには  
  
1.  新しい [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] Windows アプリケーション プロジェクト。  
  
2.  Form1 に Button1 という名前のボタンを追加します。  
  
3.   <xref:System.Windows.Forms.Control.Click> 、Button1 のイベント ハンドラーは、次のコードを追加します。  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/visualbasic/VbVbcnMyApplicationLogFiltering/Form1.vb#1)]  
  
4.  デバッガーでアプリケーションを実行します。  
  
5.  キーを押して **Button1**します。  
  
     アプリケーションは、次の情報をアプリケーションのデバッグ出力およびログ ファイルに書き込みます。  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  アプリケーションを終了します。  
  
     アプリケーションのデバッグ出力ウィンドウを表示する方法の詳細については、次を参照してください。 [出力ウィンドウ](/visual-studio/ide/reference/output-window)です。 アプリケーションのログ ファイルの場所については、次を参照してください。 [チュートリアル: を決定する、My.Application.Log 書き込みます情報](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)します。  
  
    > [!NOTE]
    >  既定では、アプリケーションは、アプリケーションの終了時にログ ファイルの出力をフラッシュします。  
  
     2 番目の呼び出し前の例で、 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> メソッドを呼び出すまで、 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> メソッドには、最初と最後の呼び出し中に、ログ出力が生成されます。、 `WriteEntry` メソッドがないです。 これは、ための重大度レベル `WriteEntry` と `WriteException` は「情報」および「エラー」でどちらも許可されて、 `My.Application.Log` オブジェクトの既定のログのフィルター処理します。 ただし、"Start"、"Stop"の重大度レベルのイベントはログの出力を生成できません。  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a>My.Application.Log のすべてのリスナーのフィルター処理  
  `My.Application.Log` オブジェクトが使用、 <xref:System.Diagnostics.SourceSwitch> という名前 `DefaultSwitch` からパスをメッセージの種類を制御する、 `WriteEntry` と `WriteException` ログ リスナーのメソッドです。 構成する `DefaultSwitch` のいずれかにその値を設定して、アプリケーションの構成ファイルで、 <xref:System.Diagnostics.SourceLevels> 列挙値。 既定では、その値は、「情報」です。  
  
 次の表は、特定の指定、リスナーにメッセージを書き込むログに必要な重要度レベル `DefaultSwitch` 設定します。  
  
|||  
|-|-|  
|DefaultSwitch 値|出力に必要なメッセージの重要度|  
|`Critical`|`Critical`|  
|`Error`|`Critical` または `Error`|  
|`Warning`|`Critical`、`Error`、または `Warning`|  
|`Information`|`Critical`、`Error`、`Warning`、または `Information`|  
|`Verbose`|`Critical`、`Error`、`Warning`、`Information`、または `Verbose`|  
|`ActivityTracing`|`Start`、`Stop`、`Suspend`、`Resume`、または `Transfer`|  
|`All`|すべてのメッセージが許可されます。|  
|`Off`|すべてのメッセージがブロックされます。|  
  
> [!NOTE]
>   `WriteEntry` と `WriteException` の各メソッドは、重大度レベルが指定されていないオーバー ロードがあります。 暗黙的な重大度レベル、 `WriteEntry` オーバー ロードは、「情報」との暗黙の重大度レベル、 `WriteException` オーバー ロードは、「エラー」です。  
  
 この表に、前の例に示すようにログ出力: 既定の `DefaultSwitch` 「情報」の設定を 2 番目の呼び出し、 `WriteEntry` メソッドを呼び出すまで、 `WriteException` メソッドの生成ログ出力します。  
  
#### <a name="to-log-only-activity-tracing-events"></a>唯一のアクティビティ トレース イベントを記録するには  
  
1.  App.config 内を右クリックし、 **ソリューション エクスプ ローラー** 選択 **開いている**します。  
  
     -または-  
  
     app.config ファイルがない場合は、次の操作を行います。  
  
    1.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
    2.  **[新しい項目の追加]** ダイアログ ボックスで、 **[アプリケーション構成ファイル]**を選択します。  
  
    3.  **[追加]**をクリックします。  
  
2.  検索、 `<switches>` セクションでは、 `<system.diagnostics>` ] セクションで、最上位レベルにある `<configuration>` セクションです。  
  
3.  追加する要素を見つけます `DefaultSwitch` スイッチのコレクションにします。 この要素にように表示する必要があります。  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  値を変更、 `value` 属性を"ActivityTracing"にします。  
  
5.  app.config ファイルの内容は次の XML のようになります。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="ActivityTracing" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
6.  デバッガーでアプリケーションを実行します。  
  
7.  キーを押して **Button1**します。  
  
     アプリケーションでは、次の情報をアプリケーションのデバッグ出力およびログ ファイルに書き込みます。  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  アプリケーションを終了します。  
  
9. 値を変更、 `value` 属性「情報」をバックアップします。  
  
    > [!NOTE]
    >   `DefaultSwitch` スイッチは、設定の制御のみ `My.Application.Log`します。 変更されませんが、どのように [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=fullName> と <xref:System.Diagnostics.Debug?displayProperty=fullName> クラスの動作です。  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a>個人 My.Application.Log のリスナーに対してフィルター処理  
 前の例は、すべてのフィルター選択を変更する方法を示しています。 `My.Application.Log` 出力します。 この例では、それぞれ個別にログ リスナーをフィルター処理する方法を示します。 既定では、アプリケーションは、アプリケーションのデバッグ出力およびログ ファイルへの書き込みの 2 つのリスナーを持ちます。  
  
 構成ファイルは、それぞれ 1 つのスイッチに似ていますが、フィルターを許可することでログ リスナーの動作を制御 `My.Application.Log`します。 ログ リスナーによってログの両方のメッセージの重大度レベルが許可された場合にのみ、メッセージの出力は `DefaultSwitch` とログ リスナーのフィルター処理します。  
  
 この例のフィルタ リング、新しいデバッグ リスナーを構成しに追加する方法、 `Log` オブジェクトです。 既定のデバッグ リスナーを削除するか、 `Log` オブジェクトのため、新しいデバッグ リスナーからデバッグ メッセージを受け取ることは明らかです。  
  
#### <a name="to-log-only-activity-tracing-events"></a>アクティビティ トレース イベントのみを記録するには  
  
1.  App.config 内を右クリックし、 **ソリューション エクスプ ローラー** 選択 **開いている**します。  
  
     または  
  
     app.config ファイルがない場合は、次の操作を行います。  
  
    1.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
    2.  **[新しい項目の追加]** ダイアログ ボックスで、 **[アプリケーション構成ファイル]**を選択します。  
  
    3.  **[追加]**をクリックします。  
  
2.  App.config 内を右クリックして **ソリューション エクスプ ローラー**します。 選択 **開く**します。  
  
3.  検索、 `<listeners>` セクションで、 `<source>` のセクション、 `name` 属性の「ここをクリック」、下にある、 `<sources>` セクションです。  `<sources>` セクションは中、 `<system.diagnostics>` ] セクションの最上位レベル [ `<configuration>` セクションです。  
  
4.  この要素を追加、 `<listeners>` セクション。  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5.  最上位の `<sharedListeners>` セクション内の `<system.diagnostics>` セクションで、 `<configuration>` セクションを見つけます。  
  
6.  その `<sharedListeners>` セクションに次の要素を追加します。  
  
    ```xml  
    <add name="NewDefault"   
         type="System.Diagnostics.DefaultTraceListener,   
               System, Version=2.0.0.0, Culture=neutral,   
               PublicKeyToken=b77a5c561934e089,   
               processorArchitecture=MSIL">  
        <filter type="System.Diagnostics.EventTypeFilter"   
                initializeData="Error" />  
    </add>  
    ```  
  
      <xref:System.Diagnostics.EventTypeFilter> フィルターでは、 <xref:System.Diagnostics.SourceLevels> 列挙の値としてその `initializeData` 属性です。  
  
7.  app.config ファイルの内容は次の XML のようになります。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
              <!-- Remove the default debug listener. -->  
              <remove name="Default"/>  
              <!-- Add a filterable debug listener. -->  
              <add name="NewDefault"/>  
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
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
          <add name="NewDefault"   
               type="System.Diagnostics.DefaultTraceListener,   
                     System, Version=2.0.0.0, Culture=neutral,   
                     PublicKeyToken=b77a5c561934e089,   
                     processorArchitecture=MSIL">  
            <filter type="System.Diagnostics.EventTypeFilter"   
                    initializeData="Error" />  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
8.  デバッガーでアプリケーションを実行します。  
  
9. キーを押して **Button1**します。  
  
     アプリケーションでは、次の情報をアプリケーションのログ ファイルに書き込みます。  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     アプリケーションより制限の厳しいフィルター処理のため、少ない情報をアプリケーションのデバッグ出力に書き込みます。  
  
     `Default Error   2   Error`  
  
10. アプリケーションを終了します。  
  
 配置後にログの設定を変更する方法の詳細については、次を参照してください。 [アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)します。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: My.Application.Log による情報の書き込み先の確認](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)   
 [チュートリアル: My.Application.Log による情報の書き込み先の変更](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)   
 [チュートリアル: カスタム ログ リスナーの作成](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)   
 [方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)   
 [トレース スイッチ](../Topic/Trace%20Switches.md)   
 [アプリケーションからのログ情報](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)