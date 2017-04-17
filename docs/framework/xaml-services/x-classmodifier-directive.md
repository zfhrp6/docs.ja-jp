---
title: "x:ClassModifier Directive | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xClassModifier"
  - "x:ClassModifier"
  - "ClassModifier"
helpviewer_keywords: 
  - "XAML [XAML Services], x:ClassModifier attribute"
  - "x:ClassModifier attribute [XAML Services]"
  - "ClassModifier attribute in XAML [XAML Services]"
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
caps.latest.revision: 22
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 21
---
# x:ClassModifier Directive
`x:Class` も提供される場合の XAML のコンパイル動作を変更します。  特に、`Public` アクセス レベル \(既定レベル\) を持つ部分 `class` を作成する代わりに、提供された `x:Class` が `NotPublic` アクセス レベルで作成されます。  この動作は、生成されるアセンブリでのクラスのアクセス レベルに影響を与えます。  
  
## XAML 属性の使用方法  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|*NotPublic*|<xref:System.Reflection.TypeAttributes?displayProperty=fullName> か <xref:System.Reflection.TypeAttributes?displayProperty=fullName> かを指定するために渡す正確な文字列は、分離コードで使用されているプログラミング言語によって異なります。  「解説」を参照してください。|  
  
## 依存関係  
 [x:Class](../../../docs/framework/xaml-services/x-class-directive.md) も同じ要素に提供される必要があり、その要素はページのルート要素である必要があります。  詳細については、「[\[MS\-XAML\] 第 4.3.1.8 節](http://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
## 解説  
 .NET Framework XAML サービスの使用での `x:ClassModifier` の値は、プログラミング言語によって異なります。  使用する文字列は、各言語の <xref:System.CodeDom.Compiler.CodeDomProvider> の実装方法、その言語が <xref:System.Reflection.TypeAttributes?displayProperty=fullName> と <xref:System.Reflection.TypeAttributes?displayProperty=fullName> の意味を定義するために返す型コンバーター、およびその言語が大文字と小文字を区別するかどうかによって決まります。  
  
-   [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)] の場合、<xref:System.Reflection.TypeAttributes?displayProperty=fullName> を指定するために渡す文字列は `internal` です。  
  
-   [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)] の場合、<xref:System.Reflection.TypeAttributes?displayProperty=fullName> を指定するために渡す文字列は `Friend` です。  
  
-   [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)] の場合、XAML のコンパイルをサポートする既存のターゲットは存在しないため、渡す値は指定されていません。  
  
 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> \([!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)] では `public`、[!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)] では `Public`\) を指定することもできますが、<xref:System.Reflection.TypeAttributes?displayProperty=fullName> が既定の動作となっているため <xref:System.Reflection.TypeAttributes?displayProperty=fullName> を指定するのは一般的ではありません。  
  
 [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)] の `private` など、同等のユーザー コード アクセス レベル制限を持つ他の値は、`x:ClassModifier` として有効ではありません。XAML では入れ子になったクラス参照がサポートされないためであり、<xref:System.Reflection.TypeAttributes?displayProperty=fullName> 修飾子が同じ効果を持ちます。  
  
## セキュリティに関するメモ  
 `x:ClassModifier` で定義されているアクセス レベルは、特定のフレームワークとその機能によって解釈されます。  WPF には、対象のクラスが Pack URI 参照によって WPF リソースから参照される場合に、`x:ClassModifier` が `internal` である型を読み込んでインスタンス化する機能が用意されています。  このケースおよび他のフレームワークによって実装される同様のケースを踏まえて、可能性のあるすべてのインスタンス化をブロックするために `x:ClassModifier` だけに依存しないでください。  
  
## 参照  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [WPF における分離コードと XAML](../../../ocs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)   
 [x:FieldModifier Directive](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)   
 [セキュリティ \(WPF\)](../../../ocs/framework/wpf/security-wpf.md)   
 [Types Migrated from WPF to System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)