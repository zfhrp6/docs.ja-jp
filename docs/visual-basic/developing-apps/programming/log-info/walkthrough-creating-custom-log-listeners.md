---
title: "カスタム ログ リスナーの作成 (Visual Basic) | Microsoft Docs"
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
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
caps.latest.revision: 19
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
ms.openlocfilehash: 98cec8d5077e777f18c18ad1af0040b3359151f7
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>チュートリアル: カスタム ログ リスナーの作成 (Visual Basic)
このチュートリアルでは、カスタム ログ リスナーを作成する方法と、`My.Application.Log` オブジェクトの出力を待機するように構成する方法について説明します。  
  
## <a name="getting-started"></a>作業の開始  
 ログ リスナーは、<xref:System.Diagnostics.TraceListener> クラスから継承する必要があります。  
  
#### <a name="to-create-the-listener"></a>リスナーを作成するには  
  
-   アプリケーションで、 <xref:System.Diagnostics.TraceListener> を継承する `SimpleListener` という名前のクラスを作成します。  
  
     [!code-vb[VbVbalrMyApplicationLog#16](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_1.vb)]  
  
     <xref:System.Diagnostics.TraceListener.Write%2A> および <xref:System.Diagnostics.TraceListener.WriteLine%2A> メソッド (基底クラスに必須 ) は、`MsgBox` を呼び出して入力を表示します。  
  
     <xref:System.Security.Permissions.HostProtectionAttribute> 属性は、 <xref:System.Diagnostics.TraceListener.Write%2A> および <xref:System.Diagnostics.TraceListener.WriteLine%2A> メソッドに適用されます。これは、各メソッドの属性を基底クラスのメソッドに一致させるためです。 <xref:System.Security.Permissions.HostProtectionAttribute> 属性を使用すると、コードを実行するホストは、コードがホスト保護の同期を公開していることを確認できます。  
  
    > [!NOTE]
    >  <xref:System.Security.Permissions.HostProtectionAttribute> 属性は、共通言語ランタイムをホストし、SQL Server などのホスト保護を実装しているアンマネージ アプリケーションでのみ有効になります。  
  
 `My.Application.Log` でログ リスナーが使用されるようにするには、ログ リスナーを含むアセンブリに厳密な名前を付ける必要があります。  
  
 次の手順では、厳密な名前付きのログ リスナー アセンブリを作成するための簡単な手順を示します。 詳しくは、「[厳密な名前付きアセンブリの作成と使用](https://msdn.microsoft.com/library/xwb8f617)」をご覧ください。  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a>ログ リスナー アセンブリに厳密な名前を付けるには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **[署名]** タブをクリックします。  
  
3.  **[アセンブリの署名]** ボックスを選択します。  
  
4.  **[厳密な名前のキー ファイルを選択してください]** ドロップダウン リストから **[\<新規作成>]** を選択します。  
  
     **[厳密な名前キーの作成]** ダイアログ ボックスが開きます。  
  
5.  **[キー ファイル名]** ボックスで、キー ファイルの名前を指定します。  
  
6.  **[パスワードの入力]** および **[パスワードの確認入力]** ボックスにパスワードを入力します。  
  
7.  **[OK]** をクリックします。  
  
8.  アプリケーションをリビルドします。  
  
## <a name="adding-the-listener"></a>リスナーの追加  
 アセンブリに厳密な名前を付けたら、次はリスナーの厳密な名前を確認して、`My.Application.Log` でログ リスナーが使用されるようにする必要があります。  
  
 厳密な名前を持つ型の書式は次のとおりです。  
  
 \<型名>, \<アセンブリ名>, \<バージョン番号>, \<カルチャ>, \<厳密な名前>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a>リスナーの厳密な名前を確認するには  
  
-   次のコードは、厳密に名前指定された `SimpleListener` の型名を確認する方法を示しています。  
  
     [!code-vb[VbVbalrMyApplicationLog#17](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_2.vb)]  
  
     型の厳密な名前は、プロジェクトによって変わります。  
  
 厳密な名前を使用すると、リスナーを `My.Application.Log` のログ リスナー コレクションに追加できます。  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a>My.Application.Log にリスナーを追加するには  
  
1.  **ソリューション エクスプローラー** で app.config を右クリックし、 **[開く]**を選択します。  
  
     または  
  
     app.config ファイルがある場合は、次の操作を行います。  
  
    1.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
    2.  **[新しい項目の追加]** ダイアログ ボックスで、 **[アプリケーション構成ファイル]**を選択します。  
  
    3.  **[追加]**をクリックします。  
  
2.  `<listeners>` セクション内にある、 `<source>` 属性が "DefaultSource" の `name` セクションで、 `<sources>` セクションを見つけます。 `<sources>` セクションは、最上位の `<system.diagnostics>` セクション内の `<configuration>` セクションにあります。  
  
3.  `<listeners>` セクションに次の要素を追加します。  
  
    ```  
    <add name="SimpleLog" />  
    ```  
  
4.  最上位の `<sharedListeners>` セクション内の `<system.diagnostics>` セクションで、 `<configuration>` セクションを見つけます。  
  
5.  その `<sharedListeners>` セクションに次の要素を追加します。  
  
    ```  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     `SimpleLogStrongName` の値はリスナーの厳密な名前に置き換えてください。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 [アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [方法 : 例外をログに記録する](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)   
 [方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)   
 [チュートリアル : My.Application.Log による情報の書き込み先の変更](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
