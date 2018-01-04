---
title: "方法 : Windows フォーム アプリケーションに Web ブラウザーの機能を追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b061b62c782cf511d26d165d5b8bdf0c9c9486b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。 また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.WebBrowser>  
 [WebBrowser コントロール](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
