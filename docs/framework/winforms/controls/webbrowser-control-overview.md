---
title: "WebBrowser コントロールの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WebBrowser"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Web ページ, 表示 (アプリケーション内に)"
  - "WebBrowser コントロール [Windows フォーム], 概要"
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# WebBrowser コントロールの概要
<xref:System.Windows.Forms.WebBrowser> コントロールは、WebBrowser ActiveX コントロール用のマネージ ラッパーを提供します。  マネージ ラッパーを使用すると、Windows フォーム クライアント アプリケーションで、Web ページを表示できます。  <xref:System.Windows.Forms.WebBrowser> コントロールを使用すると、アプリケーションで Internet Explorer の Web ブラウザー同様の機能を利用できます。または、Internet Explorer の既定の機能を無効にして、コントロールを単純な HTML ドキュメント ビューアーとして使用することもできます。  また、このコントロールを使用してフォームに DHTML ベースのユーザー インターフェイス要素を追加することによって、これらの機能が <xref:System.Windows.Forms.WebBrowser> コントロールでホストされているという事実を隠すこともできます。  この方法によって、Web コントロールと Windows フォーム コントロールとを 1 つのアプリケーションでシームレスに組み合わせることができます。  
  
## よく使用されるプロパティ、メソッド、およびイベント  
 <xref:System.Windows.Forms.WebBrowser> コントロールには、Internet Explorer のコントロールを実装するために利用できる複数のプロパティ、メソッド、およびイベントがあります。  たとえば、`Navigate` メソッドを使用すると、アドレス バーを実装でき、`GoBack` メソッド、`GoForward` メソッド、`Stop` メソッド、および `Refresh` メソッドを使用すると、ツール バー上の移動ボタンを実装できます。  `Navigated` イベントを処理すると、`Url` プロパティの値でアドレス バーを更新したり、`DocumentTitle` プロパティの値でタイトル バーを更新したりできます。  
  
 アプリケーション内で独自のページ コンテンツを作成する場合は、`DocumentText` プロパティを設定します。  HTML ドキュメント オブジェクト モデル \(DOM\) の知識があれば、`Document` プロパティを使用して、現在の Web ページのコンテンツを操作することもできます。  このプロパティを使用すると、複数のファイルを移動しなくても、メモリ内でドキュメントの格納および変更を行うことができます。  
  
 `Document` プロパティは、Web ページのスクリプト コードで実装されているメソッドを、クライアント アプリケーション コードから呼び出す場合にも使用できます。  スクリプト コードからクライアント アプリケーション コードにアクセスするには、`ObjectForScripting` プロパティを設定します。  指定したオブジェクトは、`window.external` オブジェクトとしてスクリプト コードによってアクセスできます。  
  
|名前|Description|  
|--------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A> プロパティ|現在の Web ページの HTML ドキュメント オブジェクト モデル \(DOM\) へのアクセスを管理するオブジェクトを取得します。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> イベント|Web ページの読み込みが完了した時点で発生します。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A> プロパティ|現在の Web ページから HTML コンテンツを取得または設定します。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> プロパティ|現在の Web ページのタイトルを取得します。|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A> メソッド|履歴内の前のページに移動します。|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A> メソッド|履歴内の次のページに移動します。|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A> メソッド|指定した URL へ移動します。|  
|<xref:System.Windows.Forms.WebBrowser.Navigating> イベント|移動を開始する前に発生し、アクションのキャンセルを可能にします。|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> プロパティ|Web ページのスクリプト コードでアプリケーションと通信するために使用するオブジェクトを取得または設定します。|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A> メソッド|現在の Web ページを印刷します。|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A> メソッド|現在の Web ページを再読み込みします。|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A> メソッド|現在の移動処理を中断し、サウンドやアニメーションなどの動的なページ要素を停止します。|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A> プロパティ|現在の Web ページの URL を取得または設定します。  このプロパティを設定すると、コントロールを新しい URL に移動できます。|  
  
## 参照  
 <xref:System.Windows.Forms.WebBrowser>   
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>   
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>   
 <xref:System.Windows.Forms.WebBrowserEncryptionLevel>   
 <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>   
 <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>   
 <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>   
 <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>   
 <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>   
 <xref:System.Windows.Forms.WebBrowserReadyState>   
 <xref:System.Windows.Forms.WebBrowserRefreshOption>   
 [方法 : WebBrowser コントロールで URL に移動する](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)   
 [方法 : WebBrowser コントロールを使用して印刷する](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)   
 [方法 : Windows フォーム アプリケーションに Web ブラウザーの機能を追加する](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)   
 [方法 : Windows フォーム アプリケーションで HTML ドキュメントビューアーを作成する](../../../../docs/framework/winforms/controls/how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)   
 [方法 : DHTML コードとクライアント アプリケーション コード間の双方向の通信を実装する](../../../../docs/framework/winforms/controls/implement-two-way-com-between-dhtml-and-client.md)   
 [WebBrowser セキュリティ](../../../../docs/framework/winforms/controls/webbrowser-security.md)