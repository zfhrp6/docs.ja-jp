---
title: "方法 : Freezable を読み取り専用にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aa6d3f7109e8258dff0a07556bc8572f6071c961
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-a-freezable-read-only"></a>方法 : Freezable を読み取り専用にする
この例では、作成、<xref:System.Windows.Freezable>呼び出すことによって、読み取り専用の<xref:System.Windows.Freezable.Freeze%2A>メソッドです。  
  
 固定することはできません、<xref:System.Windows.Freezable>オブジェクトのかどうか、次の条件のいずれかが`true`オブジェクトについて。  
  
-   アニメーション化されたか、データ バインドされたプロパティ。  
  
-   動的リソースによって設定されているプロパティがあります。 動的なリソースの詳細については、次を参照してください。、 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)です。  
  
-   含まれている<xref:System.Windows.Freezable>サブオブジェクトを固定することはできません。  
  
 これらの条件が場合`false`の<xref:System.Windows.Freezable>オブジェクトとする予定がない、変更、パフォーマンスの利点を固定することを検討してください。  
  
## <a name="example"></a>例  
 次の例がフリーズする、<xref:System.Windows.Media.SolidColorBrush>の型である<xref:System.Windows.Freezable>オブジェクト。  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 詳細については<xref:System.Windows.Freezable>、オブジェクトを参照してください、 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CanFreeze%2A>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
