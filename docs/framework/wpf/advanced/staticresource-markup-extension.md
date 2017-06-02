---
title: "StaticResource のマークアップ拡張機能 | Microsoft Docs"
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
  - "StaticResource"
  - "StaticResourceExtension"
helpviewer_keywords: 
  - "StaticResource のマークアップ拡張機能"
  - "XAML, StaticResource マークアップ拡張機能"
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# StaticResource のマークアップ拡張機能
既に定義されたリソースに対する参照を検索することによって、任意の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロパティ属性の値を指定します。  そのリソースに関する検索動作は、読み込み時検索に似ています。現在の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページのマークアップとその他のアプリケーション ソースとから既に読み込まれているリソースを検索し、ランタイム オブジェクト内のプロパティ値としてそのリソース値を生成します。  
  
## XAML 属性の使用方法  
  
```  
<object property="{StaticResource key}" .../>  
```  
  
## XAML オブジェクト要素の使用方法  
  
```  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`key`|要求したリソースのキー。  リソースがマークアップで作成された場合、このキーは [x:Key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)によって最初に割り当てられたものです。リソースがコードで作成された場合は、<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=fullName> を呼び出すときに `key` パラメーターで指定されたものです。|  
  
## 解説  
  
> [!IMPORTANT]
>  `StaticResource` では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル内の後方で語彙的に定義されているリソースに対する前方参照を行わないようにします。  この操作はサポートされていません。前方参照を試行すると、参照に失敗しなくても、<xref:System.Windows.ResourceDictionary> を示す内部ハッシュ テーブルが検索されるために読み込み時パフォーマンスが低下します。  リソース ディクショナリの構成を調整して、前方参照を回避できるようにすることをお勧めします。  前方参照を使用する必要がある場合は、代わりに [DynamicResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)を使用してください。  
  
 指定した <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> は、ページ、アプリケーション、使用可能なコントロール テーマと外部リソース、またはシステム リソースで [x:Key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)によって識別された、既存のリソースに対応するキーでなければなりません。  リソースの検索はその順序で行われます。  静的リソースと動的リソースのリソース検索動作の詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
 リソース キーは、[XamlName の文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)で定義されている任意の文字列にすることができます。  <xref:System.Type> などの他のオブジェクト型にすることもできます。  <xref:System.Type> キーは、暗黙のスタイル キーを通して、コントロールをテーマごとにどのようにデザインするかを決定するのに重要です。  詳細については、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。  
  
 これとは別の、リソース参照の宣言的手段には、[DynamicResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)を使用する方法があります。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。  `StaticResource` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.StaticResourceExtension> 拡張クラスの <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 値として割り当てられます。  
  
 `StaticResource` は、オブジェクト要素構文で使用できます。  この場合、<xref:System.Windows.StaticResourceExtension.ResourceKey%2A> プロパティの値の指定は必須です。  
  
 `StaticResource` は、<xref:System.Windows.StaticResourceExtension.ResourceKey%2A> プロパティをプロパティおよび値のペアとして指定する詳細出力属性使用でも使用できます。  
  
```  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 詳細出力の使用は、複数の設定可能プロパティを持つ拡張機能や、一部のプロパティがオプションである場合に役立ちます。  `StaticResource` には、必須の設定可能プロパティが 1 つしか存在しないため、このような詳細出力の使用は一般的ではありません。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサ実装では、このマークアップ拡張機能の処理は、<xref:System.Windows.StaticResourceExtension> クラスによって定義されます。  
  
 `StaticResource` はマークアップ拡張機能です。  一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] のすべてのマークアップ拡張機能では、それぞれの属性構文で { と } の 2 つの記号を使用します。これは規約であり、これに従って [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサは、マークアップ拡張機能で属性を処理する必要があることを認識します。  詳細については、「[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
## 参照  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [リソースとコード](../../../../docs/framework/wpf/advanced/resources-and-code.md)