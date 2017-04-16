---
title: "方法 : Windows アプリケーションにヘルプを提供する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "フォーム, 提供 (ヘルプを)"
  - "ヘルプ, Windows アプリケーション"
  - "HelpProvider コンポーネント [Windows フォーム]"
  - "HTML ヘルプ, Windows フォーム"
  - "Windows アプリケーション, 提供 (ヘルプを)"
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : Windows アプリケーションにヘルプを提供する
<xref:System.Windows.Forms.HelpProvider> コンポーネントを使用すると、ヘルプ ファイル内のヘルプ トピックを Windows フォームの特定のコントロールに追加できます。  ヘルプ ファイルの形式には、HTML または HTMLHelp 1.x 以上を指定できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### ヘルプを提供するには  
  
1.  **ツールボックス**から、フォームに <xref:System.Windows.Forms.HelpProvider> コンポーネントをドラッグします。  
  
     コンポーネントは、Windows フォーム デザイナーの下部にあるトレイに配置されます。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> プロパティを .chm、.col、または .htm ヘルプ ファイルに設定します。  
  
3.  フォーム上の他のコントロールを選択し、**\[プロパティ\]** ウィンドウで [HelpKeyword](frlrfSystemWindowsFormsHelpProviderClassSetHelpKeywordTopic) プロパティを設定します。  
  
     これは、適切なヘルプ トピックを呼び出すために <xref:System.Windows.Forms.HelpProvider> コンポーネントによってヘルプ ファイルに渡される文字列です。  
  
4.  **\[プロパティ\]** ウィンドウで、[HelpNavigator](frlrfSystemWindowsFormsHelpProviderClassSetHelpNavigatorTopic) プロパティを <xref:System.Windows.Forms.HelpNavigator> 列挙定数の値に設定します。  
  
     これにより、**HelpKeyword** プロパティがヘルプ システムに渡される方法が決まります。  設定できるオプションとその説明を次の表に示します。  
  
    |メンバー名|Description|  
    |-----------|-----------------|  
    |AssociateIndex|指定したトピックのインデックスを指定した URL で実行するように指定します。|  
    |\[検索\]|指定した URL の検索ページを表示するように指定します。|  
    |Index|指定した URL のインデックスを表示するように指定します。|  
    |KeywordIndex|検索するキーワードと、指定した URL で実行するアクションを指定します。|  
    |TableOfContents|HTML 1.0 ヘルプ ファイルの目次を表示するように指定します。|  
    |トピック|指定した URL によって参照されるトピックを表示するように指定します。|  
  
 実行時に、**HelpKeyword** プロパティおよび **HelpNavigator** プロパティを設定したコントロールにフォーカスがある状態で F1 キーを押すと、<xref:System.Windows.Forms.HelpProvider> コンポーネントに関連付けられたヘルプ ファイルが開きます。  
  
 現在、**HelpNamespace** プロパティは HTMLHelp 1.x、HTMLHelp 2.0、および HTML の 3 つの形式のヘルプ ファイルをサポートしています。  したがって、**HelpNamespace** プロパティには http:\/\/ アドレス \(Web ページなど\) を設定できます。  プロパティに http:\/\/ アドレスを設定すると、既定のブラウザーが開き、**HelpKeyword** プロパティに指定した文字列をアンカーとして使用して Web ページが表示されます。  アンカーは HTML ページの特定の部分にジャンプするために使用されます。  
  
> [!IMPORTANT]
>  クライアントから送信された情報は、アプリケーションで使用する前に必ずチェックしてください。  悪意のあるユーザーが、実行可能スクリプトや SQL ステートメントなどのコードの送信 \(挿入\) を試みる場合があります。  ユーザーからの入力を表示したり、データベースに格納したり、操作したりする前に、安全でない可能性のある情報が含まれていないかどうかを確認してください。  一般的な確認方法としては、ユーザーから入力を受け取ったときに、正規表現を使用して、"SCRIPT" などのキーワードを検索します。  
  
 Windows フォーム上のコントロールに対してヘルプ ファイルを表示するように <xref:System.Windows.Forms.HelpProvider> コンポーネントを設定した場合でも、このコンポーネントを使用してポップアップ ヘルプを表示できます。  詳細については、「[方法 : ポップアップ ヘルプを表示する](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)」を参照してください。  
  
## 参照  
 [方法 : ポップアップ ヘルプを表示する](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)   
 [ツールヒントを使用したコントロールのヘルプ](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)   
 [Windows フォームでのヘルプの統合](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)   
 [Windows フォーム](../../../../docs/framework/winforms/index.md)