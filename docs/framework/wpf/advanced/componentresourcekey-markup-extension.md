---
title: "ComponentResourceKey マークアップ拡張機能 | Microsoft Docs"
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
  - "ComponentResourceKey"
  - "ComponentResourceKeyExtension"
helpviewer_keywords: 
  - "ComponentResourceKey マークアップ拡張機能"
  - "XAML, ComponentResourceKey マークアップ拡張機能"
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# ComponentResourceKey マークアップ拡張機能
外部アセンブリから読み込まれるリソースのキーを定義および参照します。  これにより、アセンブリ内またはクラスで明示的にリソース ディクショナリを指定する代わりに、リソース ルックアップによってアセンブリ内の対象の型を指定することが可能になります。  
  
## XAML 属性の使用方法 \(キー設定、コンパクト\)  
  
```  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## XAML 属性の使用方法 \(キー設定、詳細\)  
  
```  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## XAML 属性の使用方法 \(リソース要求、コンパクト\)  
  
```  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## XAML 属性の使用方法 \(リソース要求、詳細\)  
  
```  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`targetTypeName`|リソース アセンブリ内で定義されているパブリック[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 型の名前。|  
|`targetID`|リソースのキー。  リソースを検索する場合、`targetID` はそのリソースの [x:Key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)と類似しています。|  
  
## 解説  
 上記の使用方法に示すように、{`ComponentResourceKey`} マークアップ拡張機能は次の 2 か所で使用されています。  
  
-   コントロールの作成者が指定したテーマ リソース ディクショナリ内のキーの定義  
  
-   アセンブリからテーマ リソースへのアクセス \(コントロールに対してテンプレートの再設定を行っているが、コントロールのテーマによって指定されたリソースからのプロパティ値を使用する場合\)  
  
 テーマからのコンポーネント リソースを参照するには、通常 `{StaticResource}` ではなく `{DynamicResource}` を使用することをお勧めします。  これは使用方法で示されています。  テーマ自体はユーザーが変更できるため、`{DynamicResource}` が推奨されます。  テーマのサポートに関するコントロールの作成者の意図に最も合ったコンポーネント リソースが必要な場合は、コンポーネント リソース参照を動的にできるようにする必要もあります。  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> は、そのリソースが実際に定義されている対象アセンブリに存在している型を識別します。  `ComponentResourceKey` は、<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> がどこで定義されているかが正確にわかっていない場合でも定義して使用できますが、最終的には、参照されているアセンブリによって型を解決する必要があります。  
  
 <xref:System.Windows.ComponentResourceKey> の一般的な使用方法は、後にクラスのメンバーとして公開するキーを定義することです。  この方法で使用する場合は、マークアップ拡張機能ではなく、<xref:System.Windows.ComponentResourceKey> クラス コンストラクターを使用します。  詳細については、<xref:System.Windows.ComponentResourceKey> または「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」の「テーマ リソース用のキーの定義と参照」セクションを参照してください。  
  
 キーを確立するときとキーを持つリソースを参照するときには、`ComponentResourceKey` マークアップ拡張機能には一般に属性構文が使用されます。  
  
 前に示したコンパクトな構文は、<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=fullName> コンストラクター シグネチャおよびマークアップ拡張機能の位置指定パラメーターの使用に依存します。  `targetTypeName` と `targetID` を設定する順序が重要です。  詳細な構文は、既定のコンストラクターである <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=fullName> に依存し、オブジェクト要素の実際の属性構文と同様の方法で <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> と <xref:System.Windows.ComponentResourceKey.ResourceId%2A> を設定します。  詳細な構文では、各プロパティを設定する順序は重要ではありません。  これら 2 つの方法 \(コンパクトと詳細\) の関係および機構の詳細については、「[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
 技術的には、`targetID` の値は任意のオブジェクトにすることができ、文字列にする必要はありません。  ただし、WPF での最も一般的な使用方法は、`targetID` 値を文字列であるフォームに合わせることです。このような文字列は、[XamlName の文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)で有効です。  
  
 `ComponentResourceKey` は、オブジェクト要素構文で使用できます。  この場合、拡張機能を正しく初期化するには、<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> プロパティと <xref:System.Windows.ComponentResourceKey.ResourceId%2A> プロパティの両方の値を指定する必要があります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] リーダー実装では、このマークアップ拡張機能の処理は、<xref:System.Windows.ComponentResourceKey> クラスによって定義されます。  
  
 `ComponentResourceKey` はマークアップ拡張機能です。  一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] のすべてのマークアップ拡張機能では、それぞれの属性構文で { と } の 2 つの記号を使用します。これは規約であり、これに従って [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサは、マークアップ拡張機能で属性を処理する必要があることを認識します。  詳細については、「[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.ComponentResourceKey>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)