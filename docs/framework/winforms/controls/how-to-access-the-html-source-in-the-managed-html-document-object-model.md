---
title: "方法 : マネージ HTML DOM (Document Object Model) の HTML ソースにアクセスする | Microsoft Docs"
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
  - "HTML, アクセス (Windows フォームで)"
  - "マネージ HTML DOM"
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : マネージ HTML DOM (Document Object Model) の HTML ソースにアクセスする
<xref:System.Windows.Forms.WebBrowser> コントロールの <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> プロパティおよび <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> プロパティは、現在のドキュメントが最初に表示されたときに存在した HTML を返します。  ただし、<xref:System.Windows.Forms.HtmlElement.AppendChild%2A> や <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A> のようなメソッド呼び出しやプロパティ呼び出しを使用してページを変更すると、<xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> や <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> を呼び出したときにこれらの変更は表示されません。  DOM の最新の HTML ソースを取得するには、HTML 要素の <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> プロパティを呼び出す必要があります。  
  
 次の手順では、動的ソースを取得し、別のショートカット メニューに表示する方法を示します。  
  
### OuterHtml プロパティを使用した動的ソースの取得  
  
1.  新しい Windows フォーム アプリケーションを作成します。  まず、<xref:System.Windows.Forms.Form> を 1 つ作成し、`Form1` という名前を付けます。  
  
2.  Windows フォーム アプリケーションで <xref:System.Windows.Forms.WebBrowser> コントロールをホストし、`WebBrowser1` という名前を付けます。  詳細については、「[方法 : Windows フォーム アプリケーションに Web ブラウザーの機能を追加する](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)」を参照してください。  
  
3.  アプリケーション内で、`CodeForm` という 2 番目の <xref:System.Windows.Forms.Form> を作成します。  
  
4.  <xref:System.Windows.Forms.RichTextBox> コントロールを `CodeForm` に追加し、その <xref:System.Windows.Forms.Control.Dock%2A> プロパティを `Fill` に設定します。  
  
5.  `CodeForm` に `Code` というパブリック プロパティを作成します。  
  
     [!code-csharp[DisplayWebBrowserCode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  `Button1` という名前の <xref:System.Windows.Forms.Button> コントロールを <xref:System.Windows.Forms.Form> に追加し、<xref:System.Windows.Forms.Control.Click> イベントを監視します。  イベントの監視の詳細については、「[イベント](../../../../docs/standard/events/index.md)」を参照してください。  
  
7.  <xref:System.Windows.Forms.Control.Click> イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[DisplayWebBrowserCode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## 信頼性の高いプログラミング  
 <xref:System.Windows.Forms.WebBrowser.Document%2A> の値を取得する前に、必ずテストしてください。  現在のページの読み込みが完了していない場合、<xref:System.Windows.Forms.WebBrowser.Document%2A> またはその 1 つ以上の子オブジェクトが初期化されていない可能性があります。  
  
## 参照  
 [マネージ HTML DOM \(Document Object Model\) の使用](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)   
 [WebBrowser コントロールの概要](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)