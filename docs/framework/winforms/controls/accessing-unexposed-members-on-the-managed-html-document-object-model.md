---
title: "マネージ HTML DOM (Document Object Model) の非公開メンバーへのアクセス | Microsoft Docs"
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
  - "マネージ HTML DOM, アクセス (非公開メンバーに)"
  - "非公開メンバー"
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# マネージ HTML DOM (Document Object Model) の非公開メンバーへのアクセス
マネージ HTML DOM \(Document Object Model\) には、すべての HTML 要素が共有するプロパティ、メソッド、およびイベントを公開する <xref:System.Windows.Forms.HtmlElement> というクラスが含まれています。  しかし、マネージ インターフェイスが直接公開しないメンバーへのアクセスが必要な場合があります。  ここでは、非公開メンバーにアクセスするための 2 つの方法について検討します。非公開メンバーには、Web ページ内部で定義される [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] 関数および VBScript 関数が含まれます。  
  
## マネージ インターフェイスを介した非公開メンバーへのアクセス  
 <xref:System.Windows.Forms.HtmlDocument> および <xref:System.Windows.Forms.HtmlElement> は、非公開メンバーへのアクセスを可能にする 4 つのメソッドを提供します。  非公開メンバーの型および対応するメソッドを次の表に示します。  
  
|メンバーの型|メソッド|  
|------------|----------|  
|プロパティ \(<xref:System.Windows.Forms.HtmlElement>\)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|メソッド|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|イベント \(<xref:System.Windows.Forms.HtmlDocument>\)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|イベント \(<xref:System.Windows.Forms.HtmlElement>\)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|イベント \(<xref:System.Windows.Forms.HtmlWindow>\)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 これらのメソッドを使用する場合、要素の基になる型が正しいことが前提になります。  ユーザーが `FORM` の値をサーバーに送信する前にいくつかの前処理を実行できるように、HTML ページにある `FORM` 要素の `Submit` イベントを待機するとします。  HTML を制御している場合、理想としては、一意の `ID` 属性を持つように `FORM` を定義します。  
  
```  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 このページを <xref:System.Windows.Forms.WebBrowser> コントロールに読み込むと、<xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> メソッドを使用して、実行時に `FORM` を取得できます。引数には、`form1` を使用します。  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## アンマネージ インターフェイスへのアクセス  
 各 DOM クラスによって公開されるアンマネージ コンポーネント オブジェクト モデル \(COM: Component Object Model\) インターフェイスを使用して、マネージ HTML DOM の非公開メンバーにアクセスすることもできます。  非公開メンバーに対して複数の呼び出しを行う必要がある場合や、マネージ HTML DOM によってラップされていない他のアンマネージ インターフェイスを非公開メンバーが返す場合には、この方法をお勧めします。  
  
 マネージ HTML DOM を通じて公開されるすべてのアンマネージ インターフェイスを次の表に示します。  各リンクをクリックすると、使用法の説明およびプログラム例が表示されます。  
  
|種類|アンマネージ インターフェイス|  
|--------|---------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 COM インターフェイスを使用する最も簡単な方法は、これはサポートされていませんがアプリケーションからアンマネージ HTML DOM ライブラリ （MSHTML.dll）への参照を追加します。  詳細については、 " " を参照してください [サポート技術情報の文書 934368](http://support.microsoft.com/kb/934368)。  
  
## スクリプト関数へのアクセス  
 HTML ページでは、[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] や VBScript などのスクリプト言語を使用して 1 つ以上の関数を定義できます。  これらの関数は HTML ページの `SCRIPT` ページの内部に配置され、要求に応じて、または DOM のイベントに応答して実行できます。  
  
 HTML ページに定義したスクリプト関数は、<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> メソッドを使用して呼び出すことができます。  スクリプト メソッドが HTML 要素を返す場合は、キャストを使用して、この返された結果を <xref:System.Windows.Forms.HtmlElement> に変換できます。  詳細とプログラム例については、<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> に関するトピックを参照してください。  
  
## 参照  
 [マネージ HTML DOM \(Document Object Model\) の使用](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)