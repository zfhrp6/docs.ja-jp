---
title: "方法 : カスタム コントロールでインクを消去する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], erasing ink on
- ink [WPF], erasing on custom control
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 23d234d97d6b25394df87016f0671d86b10a2853
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-erase-ink-on-a-custom-control"></a>方法 : カスタム コントロールでインクを消去する
<xref:System.Windows.Ink.IncrementalStrokeHitTester>現在描画ストロークに別の線が交差するかどうかを決定します。  ストロークの一部を消去するユーザーを有効にするコントロールを作成するのに便利ですが、方法、ユーザーが、<xref:System.Windows.Controls.InkCanvas>ときに、<xref:System.Windows.Controls.InkCanvas.EditingMode%2A>に設定されている<xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>です。  
  
## <a name="example"></a>例  
 次の例では、ユーザーがストロークの一部を消去できるようにするカスタム コントロールを作成します。  この例が初期化される場合は、インクを含むコントロールを作成します。  インクを収集するコントロールを作成するを参照してください。[インク入力コントロールを作成する](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)です。  
  
 [!code-csharp[HowToEraseInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
