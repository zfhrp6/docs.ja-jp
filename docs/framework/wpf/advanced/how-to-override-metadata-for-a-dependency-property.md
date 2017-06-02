---
title: "方法 : 依存関係プロパティのメタデータをオーバーライドする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "依存関係プロパティ, オーバーライド (メタデータを)"
  - "メタデータ, オーバーライド (依存関係プロパティの)"
  - "オーバーライド (依存関係プロパティのメタデータを)"
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : 依存関係プロパティのメタデータをオーバーライドする
この例では、継承したクラスの既定の依存関係プロパティのメタデータを、<xref:System.Windows.DependencyProperty.OverrideMetadata%2A> メソッドを呼び出して型固有のメタデータを提供することで、オーバーライドする方法を示します。  
  
## 使用例  
 <xref:System.Windows.PropertyMetadata> を定義することにより、クラスで[依存関係プロパティ](GTMT)の動作 \(既定値、プロパティ システム コールバックなど\) を定義できます。  多くの依存関係プロパティ クラスで、登録プロセスの一部として既定のメタデータが既に確立されています。  これには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] の一部である依存関係プロパティが含まれます。  クラス継承により依存関係プロパティを継承するクラスは、メタデータで変更できるプロパティの特性がサブクラス固有の要件に合致するように、元のメタデータをオーバーライドできます。  
  
 依存関係プロパティでのメタデータのオーバーライドは、そのプロパティがプロパティ システムによって使用される \(プロパティを登録するオブジェクトの特定のインスタンスがインスタンス化されるタイミングに相当\) 前に実行する必要があります。  <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> の呼び出しは、自身を <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> の `forType` パラメーターとして提供する型の静的なコンストラクター内で実行される必要があります。  所有者型のインスタンスが存在する場合にメタデータを変更しようとすると、例外は発生しませんが、プロパティ システムに不整合な動作が発生します。  また、メタデータは 1 つの型につき 1 回しかオーバーライドできません。  それ以降に同じ型のメタデータをオーバーライドしようとすると、例外が発生します。  
  
 次の例では、`MyAdvancedStateControl` カスタム クラスが、`MyAdvancedStateControl` によって `StateProperty` に提供されるメタデータを、新しいプロパティ メタデータでオーバーライドします。  たとえば、新しく構築された `MyAdvancedStateControl` インスタンスでプロパティが照会されると、`StateProperty` の既定値は `true` となります。  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## 参照  
 <xref:System.Windows.DependencyProperty>   
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [方法のトピック](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)