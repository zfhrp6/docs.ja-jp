---
title: '方法 : Windows フォーム アプリケーションに Web ブラウザーの機能を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
ms.openlocfilehash: d106736a288283c58bdc8020cd54b88859454fba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526850"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>方法 : Windows フォーム アプリケーションに Web ブラウザーの機能を追加する
<xref:System.Windows.Forms.WebBrowser> コントロールを使用して、Web ブラウザーの機能をアプリケーションに追加することができます。 コントロールは、既定では、Web ブラウザーのように動作します。 <xref:System.Windows.Forms.WebBrowser.Url%2A> プロパティを設定することで、最初の URL を読み込んだ後に、ハイパーリンクをクリックするか、キーボード ショートカットを使用して、ナビゲーション履歴で前または次に移動できます。 既定では、右クリックして表示されるショートカット メニューからその他のブラウザーの機能にアクセスできます。 また、コントロールにドロップすることで、新しいドキュメントを開くこともできます。 <xref:System.Windows.Forms.WebBrowser> コントロールには、Internet Explorer に似たユーザー インターフェイスの機能を実装するために使用できる、いくつかのプロパティ、メソッド、およびイベントもあります。  
  
 次のコード例では、アドレス バー、標準的なブラウザーのボタン、**[ファイル]** メニュー、ステータス バー、および現在のページのタイトルを表示するタイトル バーが実装されます。  
  
## <a name="example"></a>例  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `System,``System.Drawing` アセンブリおよび `System.Windows.Forms` アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。 この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。  また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.WebBrowser>  
 [WebBrowser コントロール](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
