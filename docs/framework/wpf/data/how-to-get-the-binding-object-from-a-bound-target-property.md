---
title: "方法 : バインドされているターゲット プロパティからのバインディング オブジェクトの取得"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 498849cc0205775f88c21d90d12b45c6b71a5dec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>方法 : バインドされているターゲット プロパティからのバインディング オブジェクトの取得
この例では、データにバインドされているターゲット プロパティからバインディング オブジェクトを取得する方法を示します。  
  
## <a name="example"></a>例  
 取得するには、次を行うことができます、<xref:System.Windows.Data.Binding>オブジェクト。  
  
 [!code-csharp[BindValidation#GetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  ターゲット オブジェクトの複数のプロパティがデータ バインディングを使用している可能性があるため、バインディングの依存関係プロパティを指定する必要があります。  
  
 また、取得することができます、<xref:System.Windows.Data.BindingExpression>の値を取得し、<xref:System.Windows.Data.BindingExpression.ParentBinding%2A>プロパティです。  
  
 コード例全体については、「[バインディングの検証のサンプル](http://go.microsoft.com/fwlink/?LinkID=159972)」をご覧ください。  
  
> [!NOTE]
>  バインドがある場合、<xref:System.Windows.Data.MultiBinding>を使用して<xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>です。 ある場合、<xref:System.Windows.Data.PriorityBinding>を使用して<xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>です。 かどうか、ターゲット プロパティを使用してバインドがない場合、 <xref:System.Windows.Data.Binding>、 <xref:System.Windows.Data.MultiBinding>、または<xref:System.Windows.Data.PriorityBinding>、使用することができます<xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>です。  
  
## <a name="see-also"></a>関連項目  
 [コードでバインディングを作成する](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
