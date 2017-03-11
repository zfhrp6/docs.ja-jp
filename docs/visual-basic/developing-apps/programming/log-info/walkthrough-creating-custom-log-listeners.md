---
title: "Walkthrough: Creating Custom Log Listeners (Visual Basic) | Microsoft Docs"
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
  - "custom log listeners"
  - "My.Application.Log object, custom log listeners"
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Walkthrough: Creating Custom Log Listeners (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このチュートリアルでは、カスタム ログ リスナーを作成する方法と、`My.Application.Log` オブジェクトの出力を待機するように構成する方法を説明します。  
  
## 作業の開始  
 ログ リスナーは <xref:System.Diagnostics.TraceListener> クラスを継承する必要があります。  
  
#### リスナーを作成するには  
  
-   アプリケーションで、`SimpleListener` という名前のクラスを、<xref:System.Diagnostics.TraceListener> を継承して作成します。  
  
     [!code-vb[VbVbalrMyApplicationLog#16](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/visualbasic/VbVbalrMyApplicationLog/Form1.vb#16)]  
  
     基本クラスのために必要な <xref:System.Diagnostics.TraceListener.Write%2A> メソッドと <xref:System.Diagnostics.TraceListener.WriteLine%2A> メソッドでは、`MsgBox` を呼び出してその入力を表示します。  
  
     <xref:System.Security.Permissions.HostProtectionAttribute> 属性を <xref:System.Diagnostics.TraceListener.Write%2A> メソッドと <xref:System.Diagnostics.TraceListener.WriteLine%2A> メソッドに適用し、基本クラスのメソッドと属性を一致させます。  <xref:System.Security.Permissions.HostProtectionAttribute> 属性により、コードを実行するホストは、そのコードがホスト保護の同期を示していることを確認できます。  
  
    > [!NOTE]
    >  <xref:System.Security.Permissions.HostProtectionAttribute> 属性が有効なのは、共通言語ランタイムをホストし、ホスト保護を実装するアンマネージ アプリケーションにおいてのみです \(SQL Server など\)。  
  
 このログ リスナーを `My.Application.Log` に確実に使用させるためには、ログ リスナーが属するアセンブリに厳密な名前を指定する必要があります。  
  
 次に示すのは、厳密な名前を指定したログ リスナー アセンブリを作成する手順の概要です。  詳細については、「[厳密な名前付きアセンブリの作成と使用](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)」を参照してください。  
  
#### ログ リスナー アセンブリに厳密な名前を指定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **\[署名\]** タブをクリックします。  
  
3.  **\[アセンブリの署名\]** ボックスを選択します。  
  
4.  **\[厳密な名前のキー ファイルを選択してください\]** ボックスの一覧の **\[\<新規作成\>\]** を選択します。  
  
     **\[厳密な名前キーの作成\]** ダイアログ ボックスが表示されます。  
  
5.  **\[キー ファイル\]** ボックスでキー ファイルの名前を指定します。  
  
6.  **\[パスワードの入力\]** ボックスと **\[パスワードの確認\]** ボックスにパスワードを入力します。  
  
7.  **\[OK\]** をクリックします。  
  
8.  アプリケーションをビルドし直します。  
  
## リスナーの追加  
 アセンブリに厳密な名前を付けたので、`My.Application.Log` がログ リスナーを使用するように、リスナーの厳密な名前を確認する必要があります。  
  
 厳密な名前を指定された型の形式は次のとおりです。  
  
 \<型名\>, \<アセンブリ名\>, \<バージョン番号\>, \<カルチャ\>, \<厳密な名前\>  
  
#### リスナーの厳密な名前を確認するには  
  
-   次のコードは、厳密な名前を指定された `SimpleListener` の型名を確認する方法を示しています。  
  
     [!code-vb[VbVbalrMyApplicationLog#17](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/visualbasic/VbVbalrMyApplicationLog/Form1.vb#17)]  
  
     型の厳密な名前はプロジェクトによって異なります。  
  
 厳密な名前を確認できたら、このリスナーを `My.Application.Log` のログ リスナーのコレクションに追加できます。  
  
#### リスナーを My.Application.Log に追加するには  
  
1.  **ソリューション エクスプローラー**で app.config を右クリックし、**\[開く\]** をクリックします。  
  
     または  
  
     app.config ファイルがある場合は、次の操作を行います。  
  
    1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
    2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[アプリケーション構成ファイル\]** をクリックします。  
  
    3.  **\[追加\]** をクリックします。  
  
2.  `<sources>` セクション内にある、`name` 属性が "DefaultSource" の `<source>` セクションで、`<listeners>` セクションを見つけます。  `<sources>` セクションは、最上位の `<configuration>` セクション内の `<system.diagnostics>` セクションにあります。  
  
3.  `<listeners>` セクションに次の要素を追加します。  
  
    ```  
    <add name="SimpleLog" />  
    ```  
  
4.  最上位の `<configuration>` セクション内の `<system.diagnostics>` セクションで、`<sharedListeners>` セクションを見つけます。  
  
5.  その `<sharedListeners>` セクションに次の要素を追加します。  
  
    ```  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     `SimpleLogStrongName` の値をリスナーの厳密な名前に変更します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 [アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)   
 [方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)   
 [チュートリアル : My.Application.Log による情報の書き込み先の変更](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)