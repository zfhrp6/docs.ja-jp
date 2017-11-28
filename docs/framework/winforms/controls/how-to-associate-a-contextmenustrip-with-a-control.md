---
title: "方法 : ContextMenuStrip をコントロールに関連付ける"
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
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0681e837e324bd62f28e673c22e29103dbe0abcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a>方法 : ContextMenuStrip をコントロールに関連付ける
コントロールとショートカット メニューを作成した後、次の手順を使用することによって、ユーザーがコントロールを右クリックした時点で特定のショートカット メニューを表示します。 これらの手順は、<xref:System.Windows.Forms.ContextMenuStrip> を Windows フォームと <xref:System.Windows.Forms.ToolStrip> コントロールに関連付けます。  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a>ContextMenuStrip を Windows フォームに関連付けるには  
  
1.  <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> プロパティを関連付けられている <xref:System.Windows.Forms.ContextMenuStrip> の名前に設定します。  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a>ContextMenuStrip を ToolStrip コントロールに関連付けるには  
  
1.  コントロールの <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> プロパティを関連付けられている <xref:System.Windows.Forms.ContextMenuStrip> の名前に設定します。  
  
## <a name="example"></a>例  
 次のコード例では、Windows フォームと <xref:System.Windows.Forms.ToolStrip> を作成して、別の <xref:System.Windows.Forms.ContextMenuStrip> コントロールをそれぞれに関連付けています。  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。 また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>  
 <xref:System.Windows.Forms.ToolStrip>  
 [方法: メニュー項目を ContextMenuStrip に追加する](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)  
 [ContextMenuStrip コントロール](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
