---
title: "方法 : ToolStripPanel を結合する"
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
- toolbars [Windows Forms], joining together
- ToolStripPanel control [Windows Forms], joining together
ms.assetid: 4eadda6d-e3b8-4151-aaf2-a8d564fbe6b3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d77d29526656da0c149ee4b8e940f4ad9e87ca3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-join-toolstrippanels"></a>方法 : ToolStripPanel を結合する
実行時に <xref:System.Windows.Forms.ToolStrip> コントロールを <xref:System.Windows.Forms.ToolStripPanel> に結合でき、これによりマルチ ドキュメント インターフェイス (MDI) アプリケーションの柔軟性を提供します。  
  
## <a name="example"></a>例  
 次のコード例は、<xref:System.Windows.Forms.ToolStrip> コントロールを <xref:System.Windows.Forms.ToolStripPanel> に結合する方法を示します。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#11)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#11)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System.Design、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。 また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripPanel>  
 [方法: ToolStripPanel を MDI で使用する](../../../../docs/framework/winforms/controls/how-to-use-toolstrippanels-for-mdi.md)
