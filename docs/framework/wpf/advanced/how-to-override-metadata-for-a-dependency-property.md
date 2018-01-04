---
title: "方法 : 依存関係プロパティのメタデータをオーバーライドする"
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
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 78d90414d86d06040065ad8ae18a037412723ce0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a>方法 : 依存関係プロパティのメタデータをオーバーライドする
この例は、呼び出すことによって、継承クラスから取得した既定の依存関係プロパティのメタデータをオーバーライドする方法を示します、<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>メソッドと型に固有のメタデータを提供します。  
  
## <a name="example"></a>例  
 定義することでその<xref:System.Windows.PropertyMetadata>クラスがその既定値とプロパティのシステムのコールバックなどの依存関係プロパティの動作を定義できます。 多くの依存関係プロパティ クラスで、登録プロセスの一部として既定のメタデータが既に確立されています。 これには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] の一部である依存関係プロパティが含まれます。 クラス継承により依存関係プロパティを継承するクラスは、メタデータで変更できるプロパティの特性がサブクラス固有の要件に合致するように、元のメタデータをオーバーライドできます。  
  
 依存関係プロパティでのメタデータのオーバーライドは、そのプロパティがプロパティ システムによって使用される (プロパティを登録するオブジェクトの特定のインスタンスがインスタンス化されるタイミングに相当) 前に実行する必要があります。 呼び出す<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>としてそれ自体を提供する型の静的コンス トラクター内で実行する必要があります、`forType`のパラメーター<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>です。 所有者型のインスタンスが存在する場合にメタデータを変更しようとすると、例外は発生しませんが、プロパティ システムに不整合な動作が発生します。 また、メタデータは 1 つの型につき 1 回しかオーバーライドできません。 それ以降に同じ型のメタデータをオーバーライドしようとすると、例外が発生します。  
  
 次の例では、`MyAdvancedStateControl` カスタム クラスが、`MyAdvancedStateControl` によって `StateProperty` に提供されるメタデータを、新しいプロパティ メタデータでオーバーライドします。 たとえば、新しく構築された `MyAdvancedStateControl` インスタンスでプロパティが照会されると、`StateProperty` の既定値は `true` となります。  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.DependencyProperty>  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [方法トピック](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
