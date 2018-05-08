---
title: マネージ HTML DOM (Document Object Model) の非公開メンバーへのアクセス
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
ms.openlocfilehash: d2fbccfb3ecd7716420ca951e86f728798d25258
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>マネージ HTML DOM (Document Object Model) の非公開メンバーへのアクセス
マネージ HTML ドキュメント オブジェクト モデル (DOM) と呼ばれるクラスが含まれています<xref:System.Windows.Forms.HtmlElement>プロパティ、メソッド、およびすべての HTML 要素に共通するイベントを公開します。 場合によっては、ただし、する必要があります、マネージ インターフェイスを直接公開しないメンバーにアクセスします。 このトピックは、非公開メンバーにアクセスするための 2 つの方法を調べて[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)]と Web ページ内で定義されている VBScript 関数。  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>マネージ インターフェイスを非公開メンバーへのアクセス  
 <xref:System.Windows.Forms.HtmlDocument> および<xref:System.Windows.Forms.HtmlElement>非公開メンバーへのアクセスを有効にする 4 つのメソッドを提供します。 次の表は、種類とその対応するメソッドを示します。  
  
|メンバーの型|メソッド|  
|-----------------|-----------------|  
|プロパティ (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|メソッド|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|イベント (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|イベント (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|イベント (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 これらのメソッドを使用する場合、適切な基になる型の要素があると見なされます。 リッスンするようにすると、`Submit`のイベント、 `FORM` HTML 要素をページにいくつかの事前処理を実行できるように、`FORM`の値は、ユーザー、サーバーに送信する前にします。 理想的には、HTML を制御する場合は、定義して、`FORM`を一意に`ID`属性。  
  
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
  
 このページを読み込んだ後、<xref:System.Windows.Forms.WebBrowser>制御を行うこともできます、<xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>を取得する方法、`FORM`を使用して実行時に`form1`引数として。  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>アンマネージ インターフェイスへのアクセス  
 マネージ HTML DOM の非公開メンバーは、各 DOM クラスによって公開されているアンマネージ コンポーネント オブジェクト モデル (COM) インターフェイスを使用してアクセスすることもできます。 非公開メンバーに対していくつかの呼び出しを行う必要がある場合、または非公開メンバーがマネージ HTML DOM によってラップされていないその他のアンマネージ インターフェイスを返す場合、これは推奨します。  
  
 次の表はすべてのマネージ HTML DOM を通じて公開されるアンマネージ インターフェイス 使用法と例のコードの詳細については、各リンクをクリックします。  
  
|型|アンマネージ インターフェイス|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 これはサポートされていませんが、アプリケーションから HTML DOM のアンマネージ ライブラリ (MSHTML.dll) への参照を追加する COM インターフェイスを使用する最も簡単な方法です。 詳細については、次を参照してください。[サポート技術情報の記事 934368](http://support.microsoft.com/kb/934368)です。  
  
## <a name="accessing-script-functions"></a>スクリプト関数へのアクセス  
 HTML ページなどのスクリプト言語を使用して、1 つまたは複数の関数を定義できます[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)]または VBScript です。 内のこれらの関数を配置している、 `SCRIPT`  ページで、ページ、DOM でイベントへの応答または要求時に実行できます。  
  
 HTML ページを使用して、定義するスクリプト関数を呼び出すことができます、<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>メソッドです。 スクリプト メソッドに HTML 要素が返される場合に返されるこの結果を変換する、キャストを使用することができます、<xref:System.Windows.Forms.HtmlElement>です。 詳細とコード例では、次を参照してください。<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>です。  
  
## <a name="see-also"></a>関連項目  
 [マネージ HTML DOM (Document Object Model) の使用](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
