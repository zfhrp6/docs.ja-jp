---
title: "方法 : Freezable が固定されているかどうかを判別する"
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
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5eed85f982687bfc90f53e57ab1ec3949820097e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a>方法 : Freezable が固定されているかどうかを判別する
この例を決める方法を説明するかどうか、<xref:System.Windows.Freezable>オブジェクトが固定されています。 固定された変更を行う場合<xref:System.Windows.Freezable>オブジェクトをスロー、<xref:System.InvalidOperationException>です。 この例外がスローされることを避けるためを使用して、<xref:System.Windows.Freezable.IsFrozen%2A>のプロパティ、<xref:System.Windows.Freezable>が固定されているかどうかを決定するオブジェクト。  
  
## <a name="example"></a>例  
 次の例がフリーズする、<xref:System.Windows.Media.SolidColorBrush>を使用してテストし、その、<xref:System.Windows.Freezable.IsFrozen%2A>が固定されているかどうかを決定するプロパティです。  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 詳細については<xref:System.Windows.Freezable>、オブジェクトを参照してください、 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.IsFrozen%2A>  
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
