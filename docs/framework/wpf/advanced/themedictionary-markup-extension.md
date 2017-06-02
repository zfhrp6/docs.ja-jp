---
title: "ThemeDictionary のマークアップ拡張機能 | Microsoft Docs"
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
  - "ThemeDictionaryExtension"
  - "ThemeDictionary"
helpviewer_keywords: 
  - "ThemeDictionary マークアップ拡張機能"
  - "XAML, ThemeDictionary マークアップ拡張機能"
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# ThemeDictionary のマークアップ拡張機能
カスタム コントロールの作成者やサードパーティ コントロールを組み込むアプリケーションに、テーマ固有のリソース ディクショナリを読み込んでコントロールのスタイル設定に使用する方法を提供します。  
  
## XAML 属性の使用方法  
  
```  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## XAML オブジェクト要素の使用方法  
  
```  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`assemblyUri`|テーマ情報を格納するアセンブリの[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]。  通常、これはより大きなパッケージ内のアセンブリを参照するパッケージの URI です。  アセンブリ リソースとパッケージの URI により、展開の問題が単純化されます。  詳細については、「[WPF におけるパッケージの URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)」を参照してください。|  
  
## 解説  
 この拡張機能は、1 つの特定のプロパティ値 \(<xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=fullName> の値\) のみを設定するためのものです。  
  
 この拡張機能を使用することにより、いくつかのスタイルを含むリソースのみのアセンブリを 1 つだけ指定し、一部のスタイルはユーザーのシステムに [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] テーマが適用されている場合にのみ使用し、一部のスタイルは Luna テーマがアクティブの場合に使用するということが可能になります。  また、必要に応じて、コントロール固有のリソース ディクショナリのコンテンツを自動的に無効化したり再度読み込んだりして、別のテーマに固有なコンテンツにすることもできます。  
  
 `assemblyUri` 文字列 \(<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> プロパティ値\) は、特定のテーマに適用するディクショナリを識別する名前付け規則の基礎です。  `ThemeDictionary` の <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> ロジックは、プリコンパイル済みのリソース アセンブリに格納されている特定のテーマ ディクショナリ バリアントを指す[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] を生成することにより、この規則を完成させます。  この名前付け規則や、テーマの一般的なコントロールのスタイル設定およびページ\/アプリケーション レベルのスタイル設定の操作に関する概念については、ここでは一部しか説明していません。  `ThemeDictionary` を使用する基本シナリオは、アプリケーション レベルで宣言された `ResourceDictionary` の <xref:System.Windows.ResourceDictionary.Source%2A> プロパティを指定することです。  直接 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を指定するのではなく、`ThemeDictionary` 拡張機能を介してアセンブリの [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を指定した場合は、システムのテーマが変更されるたびに適用される無効化ロジックが拡張機能のロジックから提供されます。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。  `ThemeDictionary` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.ThemeDictionaryExtension> 拡張クラスの <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> 値として割り当てられます。  
  
 `ThemeDictionary` は、オブジェクト要素構文でも使用できます。  この場合、<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> プロパティの値の指定は必須です。  
  
 `ThemeDictionary` は、<xref:System.Windows.Markup.StaticExtension.Member%2A> プロパティをプロパティおよび値のペアとして指定する詳細出力属性使用でも使用できます。  
  
```  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 詳細出力の使用は、複数の設定可能プロパティを持つ拡張機能や、一部のプロパティがオプションである場合に役立ちます。  `ThemeDictionary` には、必須の設定可能プロパティが 1 つしか存在しないため、このような詳細出力の使用は一般的ではありません。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサ実装では、このマークアップ拡張機能の処理は、<xref:System.Windows.ThemeDictionaryExtension> クラスによって定義されます。  
  
 `ThemeDictionary` はマークアップ拡張機能です。  一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] のすべてのマークアップ拡張機能では、それぞれの属性構文で { と } の 2 つの記号を使用します。これは規約であり、これに従って [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサは、マークアップ拡張機能で属性を処理する必要があることを認識します。  詳細については、「[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
## 参照  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)