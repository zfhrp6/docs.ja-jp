---
title: "DynamicResource のマークアップ拡張機能 | Microsoft Docs"
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
  - "DynamicResource"
  - "DynamicResourceExtension"
helpviewer_keywords: 
  - "DynamicResource のマークアップ拡張機能"
  - "XAML, DynamicResource マークアップ拡張機能"
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# DynamicResource のマークアップ拡張機能
定義されたリソースに対する参照になる値を優先させることによって、任意の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロパティ属性の値を指定します。  そのリソースに関する検索動作は、実行時検索に似ています。  
  
## XAML 属性の使用方法  
  
```  
<object property="{DynamicResource key}" .../>  
```  
  
## XAML プロパティ要素の使用方法  
  
```  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`key`|要求したリソースのキー。  リソースがマークアップで作成された場合、このキーは [x:Key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)によって最初に割り当てられたものです。リソースがコードで作成された場合は、<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=fullName> を呼び出すときに `key` パラメーターで指定されたものです。|  
  
## 解説  
 `DynamicResource` は、初期コンパイル中に一時的な式を作成し、それによって、要求されたリソース値がオブジェクトを構成するために実際に必要になるまで、リソースに関する検索を遅延します。  これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページが読み込まれた後になる可能性があります。  リソース値は、すべてのアクティブなリソース ディクショナリに対して、現在のページ スコープを開始点としてキー検索を実行することで検出され、コンパイル時に設定されたプレースホルダー式と置き換えられます。  
  
> [!IMPORTANT]
>  依存関係プロパティの優先順位という点では、`DynamicResource` 式は、動的リソース参照が適用される位置と同じになります。  以前に `DynamicResource` 式をローカル値として持っていたプロパティにローカル値を設定すると、`DynamicResource` は完全に削除されます。  詳細については、「[依存関係プロパティ値の優先順位](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)」を参照してください。  
  
 ある種のリソース アクセス シナリオは、[StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)とは対照的に、`DynamicResource` に特に適しています。  `DynamicResource` と `StaticResource` のメリットの比較、およびパフォーマンスへの影響の詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
 指定した <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> は、ページ、アプリケーション、使用可能なコントロール テーマと外部リソース、またはシステム リソースで [x:Key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)によって指定された既存のリソースに対応するキーでなければなりません。また、リソースのルックアップはキーの指定順に行われます。  静的リソースと動的リソースのリソース検索の詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
 リソース キーは、[XamlName の文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)で定義されている任意の文字列にすることができます。  <xref:System.Type> などの他のオブジェクト型にすることもできます。  <xref:System.Type> キーは、コントロールをテーマごとにどのようにデザインするかを決定するのに重要です。  詳細については、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。  
  
 リソース値の検索に使用する <xref:System.Windows.FrameworkElement.FindResource%2A> などの [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] は、`DynamicResource` で使用されるものと同じリソース検索ロジックに従います。  
  
 これとは別の、リソース参照の宣言的手段には、[StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)を使用する方法があります。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。  `DynamicResource` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.DynamicResourceExtension> 拡張クラスの <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 値として割り当てられます。  
  
 `DynamicResource` は、オブジェクト要素構文で使用できます。  この場合、<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> プロパティの値の指定は必須です。  
  
 `DynamicResource` は、<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> プロパティをプロパティおよび値のペアとして指定する詳細出力属性使用でも使用できます。  
  
```  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 詳細出力の使用は、複数の設定可能プロパティを持つ拡張機能や、一部のプロパティがオプションである場合に役立ちます。  `DynamicResource` には、必須の設定可能プロパティが 1 つしか存在しないため、このような詳細出力の使用は一般的ではありません。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサ実装では、このマークアップ拡張機能の処理は、<xref:System.Windows.DynamicResourceExtension> クラスによって定義されます。  
  
 `DynamicResource` はマークアップ拡張機能です。  一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] のすべてのマークアップ拡張機能では、それぞれの属性構文で { と } の 2 つの記号を使用します。これは規約であり、これに従って [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサは、マークアップ拡張機能で属性を処理する必要があることを認識します。  詳細については、「[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
## 参照  
 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [リソースとコード](../../../../docs/framework/wpf/advanced/resources-and-code.md)   
 [x:Key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)   
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)