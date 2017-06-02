---
title: "方法 : マネージ HTML DOM (Document Object Model) にアクセスする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "HTML DOM にアクセスします。"
  - "マネージ HTML DOM にアクセスします。"
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : マネージ HTML DOM (Document Object Model) にアクセスする
マネージ HTML ドキュメント オブジェクト モデル (DOM) には、次の&2; 種類のアプリケーションからアクセスできます。  
  
-   マネージ ホストされている Windows フォーム アプリケーション (.exe) <xref:System.Windows.Forms.WebBrowser>コントロールです。 これら&2; つのテクノロジが相互に補完、 <xref:System.Windows.Forms.WebBrowser>コントロール、ユーザーと、ドキュメントの論理構造を表す HTML DOM にページを表示します。  
  
-   Windows フォーム<xref:System.Windows.Forms.UserControl> Internet Explorer 内でホストされています。 先のページを表す HTML DOM にアクセスすることができます、 <xref:System.Windows.Forms.UserControl>がドキュメントの構造を変更したり、さまざまな操作の間でのモーダル ダイアログ ボックスを開いたりするためにホストされています。  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a>Windows フォーム アプリケーションから DOM にアクセスするには  
  
1.  ホスト、 <xref:System.Windows.Forms.WebBrowser> 、Windows フォーム アプリケーション内で制御し、監視、 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted>イベントです。 コントロールをホストしていると、イベントの監視の詳細については、「[イベント](../../../../docs/standard/events/index.md)です。  
  
2.  取得、 <xref:System.Windows.Forms.HtmlDocument> 、現在のページにアクセスして、<xref:System.Windows.Forms.WebBrowser.Document%2A>のプロパティ、 <xref:System.Windows.Forms.WebBrowser>コントロールです。  
  
<!-- TODO: review snippet reference  [!CODE [AccessHTMLDOMApp#1](AccessHTMLDOMApp#1)]  -->  
  
### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a>Internet Explorer でホストされた UserControl から DOM にアクセスするには  
  
1.  独自のカスタム派生クラスを作成、 <xref:System.Windows.Forms.UserControl>クラスです。 詳細については、次を参照してください。[方法: 複合コントロールの作成](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)します。  
  
2.  Load イベント ハンドラー内の次のコードを配置、 <xref:System.Windows.Forms.UserControl>:  
  
 [!code-csharp[AccessHTMLDOMControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
  
1.  を通じて DOM を使用する場合、 <xref:System.Windows.Forms.WebBrowser>コントロールが常にまで待っていると、 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted>にアクセスする前に発生するイベント、<xref:System.Windows.Forms.WebBrowser.Document%2A>のプロパティ、 <xref:System.Windows.Forms.WebBrowser>コントロールです。 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted>ドキュメント全体が読み込まれた後にイベントが発生します。 アプリケーションで、実行時に例外が発生する恐れその前に、DOM を使用する場合。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
  
1.  アプリケーションまたは<xref:System.Windows.Forms.UserControl>マネージ HTML DOM にアクセスするために完全な信頼が必要 使用して Windows フォーム アプリケーションを展開する場合[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]、アクセス許可の昇格または信頼されたアプリケーションの配置を使用して完全な信頼を要求できます。 を参照してください[ClickOnce アプリケーションのセキュリティで保護する](../Topic/Securing%20ClickOnce%20Applications.md)詳細です。  
  
## <a name="see-also"></a>関連項目  
 [マネージ HTML ドキュメント オブジェクト モデルを使用します。](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)