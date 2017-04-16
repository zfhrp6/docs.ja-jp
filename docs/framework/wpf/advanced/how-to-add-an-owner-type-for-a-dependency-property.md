---
title: "方法 : 依存関係プロパティの所有者の種類を追加する | Microsoft Docs"
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
  - "クラス, 追加 (依存関係プロパティの所有者として)"
  - "依存関係プロパティ, 追加 (クラスを所有者として)"
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : 依存関係プロパティの所有者の種類を追加する
この例では、異なる型に対して登録された依存プロパティの所有者としてクラスを追加する方法を示します。  これにより、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] リーダーとプロパティ システムの両方が、プロパティの追加の所有者としてクラスを認識できるようになります。  さらに所有者として追加することで、追加するクラスが型固有のメタデータを提供できるようになります。  
  
 次の例では、`StateProperty` は `MyStateControl` クラスによって登録されるプロパティです。  `UnrelatedStateControl` クラスは、<xref:System.Windows.DependencyProperty.AddOwner%2A> メソッドを使用し、追加する型に存在する依存関係プロパティの新しいメタデータで使用可能なシグネチャを明示的に使用して、`StateProperty` の所有者として自分自身を追加します。  このとき、「[依存関係プロパティを実装する](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md)」の例に示すようなプロパティの[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] アクセサーを提供し、さらに、所有者として追加されるクラスに対する依存プロパティ識別子を再公開する必要がある点に注意してください。  
  
 ラッパーがなくても、プログラムによるアクセスという観点からは、依存プロパティは <xref:System.Windows.DependencyObject.GetValue%2A> または <xref:System.Windows.DependencyObject.SetValue%2A> を使用して動作できます。  ただし通常は、このプロパティシステム動作を [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティ ラッパーと合わせる必要があります。  ラッパーを使用すると、プログラムでの依存関係プロパティの設定が容易になり、プロパティを [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 属性として設定できるようになります。  
  
 既定のメタデータをオーバーライドする方法については、「[依存関係プロパティのメタデータをオーバーライドする](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md)」を参照してください。  
  
## 使用例  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## 参照  
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)