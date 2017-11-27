---
title: "Windows フォーム コントロールでのマージンと埋め込み"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 22d8a73963a8f9f1e3d8b80b6c16f189e0221c55
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="margin-and-padding-in-windows-forms-controls"></a>Windows フォーム コントロールでのマージンと埋め込み
フォーム上のコントロールを正確に配置することは、多くのアプリケーションで優先度の高い作業です。 <xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間は、これを実現する多くのレイアウト機能を提供します。 最も重要な 2 つは、<xref:System.Windows.Forms.Control.Margin%2A> プロパティと <xref:System.Windows.Forms.Control.Padding%2A> プロパティです。  
  
 <xref:System.Windows.Forms.Control.Margin%2A> プロパティは、その他のコントロールで、コントロールの枠線からの指定された距離を保持するコントロールの周囲のスペースを定義します。  
  
 <xref:System.Windows.Forms.Control.Padding%2A> プロパティは、コントロールの内容 (<xref:System.Windows.Forms.Control.Text%2A> プロパティの値など) で、コントロールの枠線からの指定した距離を保持するコントロールの内部のスペースを定義します。  
  
 次の図は、コントロールの <xref:System.Windows.Forms.Control.Padding%2A> プロパティと <xref:System.Windows.Forms.Control.Margin%2A> プロパティを示しています。  
  
 ![フォーム コントロールの Windows のパディングとマージン](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 Visual Studio では、この機能のデザイン時サポートがあります。  参照してください[チュートリアル: レイアウトを Windows フォーム コントロールを Padding、Margin、および AutoSize プロパティ](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.Control.Margin%2A>  
 <xref:System.Windows.Forms.Control.Padding%2A>  
 <xref:System.Windows.Forms.Control.LayoutEngine%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
