---
title: "方法 : Windows アプリケーションにヘルプを提供する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0f407f1c17c67ec99f4499b89c49932a4ba6d32c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-provide-help-in-a-windows-application"></a>方法 : Windows アプリケーションにヘルプを提供する
使用することができます、 <xref:System.Windows.Forms.HelpProvider> Windows フォームでの特定のコントロールにヘルプ ファイル内でヘルプ トピックをアタッチするコンポーネントです。 ヘルプ ファイルの形式には、HTML または HTMLHelp 1.x 以上を指定できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-provide-help"></a>ヘルプを提供するには  
  
1.  **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.HelpProvider>コンポーネントをフォームにします。  
  
     コンポーネントは、Windows フォーム デザイナーの下部にあるトレイに配置されます。  
  
2.  **プロパティ**ウィンドウで、設定、 <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> .chm、.col、または .htm のヘルプ ファイルへのプロパティです。  
  
3.  フォーム上にあるし、別のコントロールを選択して、**プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>プロパティです。  
  
     これは、を介して渡された文字列、<xref:System.Windows.Forms.HelpProvider>コンポーネント、ヘルプ ファイルに適切なヘルプ トピックをします。  
  
4.  **プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A>プロパティの値を<xref:System.Windows.Forms.HelpNavigator>列挙します。  
  
     これにより、**HelpKeyword** プロパティがヘルプ システムに渡される方法が決まります。 設定できるオプションとその説明を次の表に示します。  
  
    |メンバー名|説明|  
    |-----------------|-----------------|  
    |AssociateIndex|指定したトピックのインデックスを指定した URL で実行するように指定します。|  
    |[検索]|指定した URL の検索ページを表示するように指定します。|  
    |インデックス|指定した URL のインデックスを表示するように指定します。|  
    |KeywordIndex|検索するキーワードと、指定した URL で実行するアクションを指定します。|  
    |TableOfContents|HTML 1.0 ヘルプ ファイルの目次を表示するように指定します。|  
    |トピック|指定した URL によって参照されるトピックを表示するように指定します。|  
  
 F1 キーを押して、実行時にときにコントロール — 設定したため、 **HelpKeyword**と**HelpNavigator**プロパティ — がフォーカスに関連付けられているヘルプ ファイルを開きます<xref:System.Windows.Forms.HelpProvider>コンポーネントです。  
  
 現在、**HelpNamespace** プロパティは HTMLHelp 1.x、HTMLHelp 2.0、および HTML の 3 つの形式のヘルプ ファイルをサポートしています。 したがって、**HelpNamespace** プロパティには http:// アドレス (Web ページなど) を設定できます。 プロパティに http:// アドレスを設定すると、既定のブラウザーが開き、**HelpKeyword** プロパティに指定した文字列をアンカーとして使用して Web ページが表示されます。 アンカーは HTML ページの特定の部分にジャンプするために使用されます。  
  
> [!IMPORTANT]
>  クライアントから送信された情報は、アプリケーションで使用する前に必ずチェックしてください。 悪意のあるユーザーが、実行可能スクリプトや SQL ステートメントなどのコードの送信 (挿入) を試みる場合があります。 ユーザーからの入力を表示したり、データベースに格納したり、操作したりする前に、安全でない可能性のある情報が含まれていないかどうかを確認してください。 一般的な確認方法としては、ユーザーから入力を受け取ったときに、正規表現を使用して、"SCRIPT" などのキーワードを検索します。  
  
 使用することも、 <xref:System.Windows.Forms.HelpProvider> Windows フォーム上のコントロールのヘルプ ファイルを表示するよう構成されている場合でも、ポップアップのヘルプを表示するコンポーネントです。 詳細については、「[方法: ポップアップ ヘルプを表示する](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [方法: ポップアップ ヘルプを表示する](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 [ツールヒントを使用したコントロールのヘルプ](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [Windows フォームでのヘルプの統合](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [Windows フォーム](../../../../docs/framework/winforms/index.md)
