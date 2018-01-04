---
title: "方法 : バインディングをクリアする"
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
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af45d504eb4e7d45808f787925a90c8e0ed19476
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-clear-bindings"></a>方法 : バインディングをクリアする
この例では、オブジェクトからバインディングをクリアする方法を示します。  
  
## <a name="example"></a>例  
 オブジェクトの個々 のプロパティからバインドをクリアするには、呼び出す<xref:System.Windows.Data.BindingOperations.ClearBinding%2A>次の例で示すようにします。 次の例からバインドを削除する、<xref:System.Windows.Controls.TextBlock.TextProperty>の*mytext*、<xref:System.Windows.Controls.TextBlock>オブジェクト。  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 バインディングをクリアすると、バイディングが削除され、依存関係プロパティの値は、バインディングが存在していなかったときの値に変更されます。 この値は、既定値、継承された値、データ テンプレート バインディングの値などです。  
  
 オブジェクトのすべてのプロパティからバインドをクリアする<xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Data.BindingOperations>  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
