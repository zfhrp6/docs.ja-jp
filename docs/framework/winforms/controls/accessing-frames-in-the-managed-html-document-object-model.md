---
title: "マネージ HTML DOM (Document Object Model) へのアクセス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTML [Windows Forms], dOM
- managed HTML DOM
- HTML [Windows Forms], managed
- HTML DOM [Windows Forms], managed
- frames [Windows Forms], accessing
- DOM [Windows Forms], accessing frames in managed HTML
ms.assetid: cdeeaa22-0be4-4bbf-9a75-4ddc79199f8d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8766e33f0fb253d532ff7161ed0a1e7842d0c50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-frames-in-the-managed-html-document-object-model"></a>マネージ HTML DOM (Document Object Model) へのアクセス
一部の HTML ドキュメントが不在で構成される*フレーム*、または独自の個別の HTML ドキュメントを持つウィンドウです。 フレームを使用すると、ページ内に 1 つ以上の静的な部分 (ナビゲーション バーなど) があり、その他のフレームでは内容が常に変化するような HTML ページを簡単に作成できます。  
  
 HTML の作成者は、2 つの方法のいずれかでフレームを作成できます。  
  
-   `FRAMESET` タグと `FRAME` タグを使用して、固定ウィンドウを作成する。  
  
 または  
  
-   `IFRAME` タグを使用して、実行時に移動できるフローティング ウィンドウを作成する。  
  
1.  フレームは HTML ドキュメントを含むため、DOM (Document Object Model) においてフレームはウィンドウ要素およびフレーム要素の両方として表されます  
  
2.  <xref:System.Windows.Forms.HtmlWindow> の Frames コレクションを使用して `FRAME` タグまたは `IFRAME` タグにアクセスすると、フレームに対応するウィンドウ要素を取得できます。 これは、現在の URL、ドキュメント、サイズなど、フレームのすべての動的プロパティを表します。  
  
3.  <xref:System.Windows.Forms.HtmlWindow> の <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> プロパティ、<xref:System.Windows.Forms.HtmlElement.Children%2A> コレクション、または <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> や <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> などのメソッドを使用して `FRAME` タグまたは `IFRAME` タグにアクセスすると、フレーム要素を取得できます。 これは、元の HTML ファイルに指定されている URL を含む、フレームの静的プロパティを表します。  
  
## <a name="frames-and-security"></a>フレームとセキュリティ  
 マネージ HTML DOM と呼ばれるセキュリティ手段が実装されているという事実によってフレームへのアクセスが複雑な*クロス フレーム スクリプティング セキュリティ*です。 異なるドメインに属する複数の `FRAME` を持つ `FRAMESET` がドキュメントに含まれる場合、これらの `FRAME` は相互にやり取りできません。 つまり、自分の Web サイトのコンテンツを表示する `FRAME` は、サード パーティのサイト (http://www.adatum.com/ など) をホストする `FRAME` 内の情報にアクセスできません このセキュリティは、<xref:System.Windows.Forms.HtmlWindow> クラスのレベルで実装されます 別の Web サイトをホストする `FRAME` に関する一般情報 (URL など) は取得できますが、Web サイトの <xref:System.Windows.Forms.HtmlWindow.Document%2A> へのアクセスや、ホストしている `FRAME` または `IFRAME` のサイズや位置の変更はできません。  
  
 この規則は、<xref:System.Windows.Forms.HtmlWindow.Open%2A> メソッドおよび <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> メソッドを使用して開くウィンドウにも適用されます。 開いたウィンドウが <xref:System.Windows.Forms.WebBrowser> コントロール内でホストされているページとは異なるドメインにある場合、そのウィンドウを移動したり、内容をチェックしたりできません。 このような制限は、<xref:System.Windows.Forms.WebBrowser> コントロールを使用して、Windows フォーム ベースのアプリケーションの配置に使用した Web サイトとは異なる Web サイトを表示する場合にも適用されます。 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 配置テクノロジを使用して Web サイト A からアプリケーションをインストールし、<xref:System.Windows.Forms.WebBrowser> を使用して Web サイト B を表示した場合、Web サイト B のデータにはアクセスできません。  
  
 クロスサイト スクリプティングの詳細については、次を参照してください。[に関するクロス フレームのスクリプティングとセキュリティ](http://msdn.microsoft.com/library/ms533028.aspx)です。  
  
## <a name="see-also"></a>関連項目  
 [フレーム要素 &#124;です。フレーム オブジェクト](http://msdn.microsoft.com/library/ms535250.aspx)  
 [マネージ HTML DOM (Document Object Model) の使用](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
