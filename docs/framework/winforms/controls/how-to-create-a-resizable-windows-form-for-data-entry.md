---
title: "方法 : データ入力用のサイズ変更可能な Windows フォームを作成する"
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
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 51e844dc49f75e2f27ad5bbaf9176e71f6e3388a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>方法 : データ入力用のサイズ変更可能な Windows フォームを作成する
レイアウトが優れていると、その親フォームの寸法の変更に柔軟に対応できます。 <xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用すると、フォームの寸法の変更に応じて一貫した方法でコントロールの位置とサイズが変更されるように、フォームのレイアウトを調整できます。 <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、コントロールの内容の変更によってレイアウトの変更が生じる場合にも便利です。 この手順で説明するプロセスは、Visual Studio 環境内で実行できます。  「[チュートリアル: データ入力用のサイズ変更可能な Windows フォームの作成](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))」も参照してください。  
  
## <a name="example"></a>例  
 ユーザーによるフォームのサイズ変更に適切に対応するレイアウトを <xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用して作成する方法を次の例に示します。 また、ローカリゼーションに適切に対応するレイアウトも示します。  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。 また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [方法: ローカリゼーションに対応した Windows フォーム レイアウトをデザインする](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Microsoft Windows ユーザー エクスペリエンス、ユーザー インターフェイスの開発者とデザイナーのための公式のガイドライン。Redmond、WA: Microsoft Press、1999 年。(USBN: 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)
