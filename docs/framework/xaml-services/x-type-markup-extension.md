---
title: "x:Type Markup Extension | Microsoft Docs"
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
  - "x:TypeExtension"
  - "Type"
  - "x:Type"
  - "xType"
  - "TypeExtension"
helpviewer_keywords: 
  - "x:Type markup extension [XAML Services]"
  - "XAML [XAML Services], x:Type markup extension"
  - "XAML [XAML Services], TargetType attribute"
  - "TargetType attribute [XAML Services]"
  - "Type markup extension in XAML [XAML Services]"
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
caps.latest.revision: 27
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 27
---
# x:Type Markup Extension
指定した XAML 型の基になる型の CLR <xref:System.Type> オブジェクトを指定します。  
  
## XAML 属性の使用方法  
  
```  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## XAML オブジェクト要素の使用方法  
  
```  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`prefix`|省略可能です。  既定以外の XAML 名前空間を割り当てるプレフィックス。  ほとんどの場合、プレフィックスは指定する必要がありません。  「解説」を参照してください。|  
|`typeNameValue`|必ず指定します。  現在の既定の XAML 名前空間で解決できる型名。`prefix` を指定した場合はその割り当てられたプレフィックス。|  
  
## 解説  
 `x:Type` マークアップ拡張機能は、[!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] の `typeof()` 演算子または [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] の `GetType` 演算子に似た機能を備えています。  
  
 `x:Type` マークアップ拡張機能は、型 <xref:System.Type> を使用するプロパティの文字列からの変換動作を指定します。  入力は XAML 型です。  入力 XAML 型と出力 CLR <xref:System.Type> との関係は、XAML スキーマ コンテキストとそのコンテキストが提供する <xref:System.Windows.Markup.IXamlTypeResolver> サービスに基づいて必須の <xref:System.Xaml.XamlType> を検索した後、出力 <xref:System.Type> が入力 <xref:System.Xaml.XamlType> の <xref:System.Xaml.XamlType.UnderlyingType%2A> であることです。  
  
 .NET Framework XAML サービスでは、このマークアップ拡張機能の処理は、<xref:System.Windows.Markup.TypeExtension> クラスによって定義されます。  
  
 特定のフレームワーク実装では、値として <xref:System.Type> を受け取る一部のプロパティは、型の名前 \(型の `Name` の文字列値\) を直接受け入れることができます。  ただし、このような動作を実装するのは複雑なシナリオとなります。  例については、後の「WPF の使用上の注意」を参照してください。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。  `x:Type` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.Markup.TypeExtension> 拡張クラスの <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 値として割り当てられます。  CLR 型に基づく、.NET Framework XAML サービスの既定の XAML スキーマ コンテキストでは、この属性の値は、対象の型の <xref:System.Reflection.MemberInfo.Name%2A> になるか、または、既定以外の XAML 名前空間割り当ての場合はプレフィックスが付加された <xref:System.Reflection.MemberInfo.Name%2A> を含みます。  
  
 `x:Type` マークアップ拡張機能は、オブジェクト要素構文で使用できます。  この場合、拡張機能を正しく初期化するには、<xref:System.Windows.Markup.TypeExtension.TypeName%2A> プロパティの値を指定する必要があります。  
  
 `x:Type` マークアップ拡張機能は詳細出力属性として使用することもできますが、この用法は一般的ではありません \(`<``object` `property``="{x:Type TypeName=``typeNameValue``}" .../>`\)。  
  
## WPF の使用上の注意  
  
### 既定の XAML 名前空間および型の割り当て  
 WPF プログラミングの既定の XAML 名前空間には、通常の XAML シナリオで必要なほとんどの XAML 型が含まれるため、通常は、XAML 型値を参照するときにプレフィックスを回避できます。  カスタム アセンブリ内の型を参照している場合、または WPF アセンブリ内に存在する型ではあるが、その型がある CLR 名前空間が既定の XAML 名前空間に割り当てられていない場合は、プレフィックスの割り当てが必要になることがあります。  プレフィックス、XML 名前空間、および CLR 名前空間の割り当ての詳細については、「[XAML 名前空間および WPF XAML の名前空間の割り当て](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)」を参照してください。  
  
### 文字列としての型名をサポートする型プロパティ  
 WPF は、`x:Type` マークアップ拡張機能を使用する必要なく、型 <xref:System.Type> の一部のプロパティの値を指定できる技術をサポートしています。  代わりに、型に名前を付ける文字列として値を指定できます。  この例としては、<xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=fullName> および <xref:System.Windows.Style.TargetType%2A?displayProperty=fullName> があります。  型コンバーターとマークアップ拡張機能は、どちらもこの動作をサポートしていません。  これは、<xref:System.Windows.FrameworkElementFactory> を通じて実装される遅延動作です。  
  
 Silverlight も同様の規則となります。  実際、Silverlight の XAML 言語の対応状況を見ると、現在 `{x:Type}` はサポートされていません。WPF から Silverlight への XAML の移行支援を意図した一部の状況を除いて、`{x:Type}` の使用は認められていません。  したがって、文字列としての型名の動作は、<xref:System.Type> が値となる、Silverlight のすべてのネイティブ プロパティの評価に組み込まれています。  
  
## XAML 2009  
 XAML 2009 はジェネリック型に対するサポートを強化し、このサポートを実現できるよう `x:TypeArguments` および `x:Type` の機能の動作を修正します。  
  
-   `x:TypeArguments` および汎用オブジェクトのインスタンス化で使用される関連オブジェクト要素は、ルート以外の要素上にあることがあります。  詳細については、「[x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md)」の「XAML 2009」のセクションを参照してください。  
  
-   XAML 2009 は、マークアップでジェネリック型の制約を指定する構文をサポートします。  これは、`x:TypeArguments`、`x:Type`、またはこれら 2 つの機能の組み合わせで使用できます。  
  
-   XAML 2009 の読み込みを処理する WPF の XAML 実装も、型 <xref:System.Type> を使用する特定のフレームワーク プロパティの暗黙的な型変換動作に対して、この機能を追加します。  
  
 WPF では XAML 2009 の機能を使用できますが、Loose XAML \(マークアップ コンパイルされていない XAML\) に限定されます。  WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。  
  
## 参照  
 <xref:System.Windows.Style>   
 [スタイルとテンプレート](../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [XAML の概要 \(WPF\)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [マークアップ拡張機能と WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)