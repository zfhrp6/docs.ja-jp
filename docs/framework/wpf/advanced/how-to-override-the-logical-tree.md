---
title: "方法: 論理ツリーをオーバーライドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cc6045d3505981d93f07347ebd49d57cd759774
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-override-the-logical-tree"></a>方法: 論理ツリーをオーバーライドする
ほとんどの場合は必要ありませんが、高度なコントロールを作成する場合は、必要に応じて論理ツリーをオーバーライドできます。  
  
## <a name="example"></a>例  
 この例ではサブクラス<xref:System.Windows.Controls.StackPanel>パネルがだけし、単一の子要素は表示のみの動作を適用ここでは、論理ツリーをオーバーライドします。 これは実際的には必ずしも好ましい動作ではありませんが、ここでは要素の通常の論理ツリーをオーバーライドするシナリオを説明するための手段として示します。  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 論理ツリーについて詳しくは、「[WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)」をご覧ください。
