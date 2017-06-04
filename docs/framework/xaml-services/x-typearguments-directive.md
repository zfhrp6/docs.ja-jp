---
title: "x:TypeArguments Directive | Microsoft Docs"
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
  - "x:TypeArguments"
  - "xTypeArguments"
  - "TypeArguments"
helpviewer_keywords: 
  - "x:TypeArguments attribute [XAML Services]"
  - "TypeArguments attribute in XAML [XAML Services]"
  - "XAML [XAML Services], x:TypeArguments attribute"
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
caps.latest.revision: 18
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 18
---
# x:TypeArguments Directive
ジェネリックの制約型引数をジェネリック型のコンストラクターに渡します。  
  
## XAML 属性の使用方法  
  
```  
<object x:TypeArguments="typeString" .../>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`object`|CLR ジェネリック型によってサポートされる XAML 型のオブジェクト要素の宣言。  `object` が、既定の XAML 名前空間から派生していない XAML 型である場合、`object` は `object` が存在する XAML 名前空間を示すプレフィックスを必要とします。|  
|`typeString`|CLR ジェネリック型に型引数を提供する、1 つ以上の XAML 型名を文字列として宣言する文字列。  構文の注意事項の詳細については、「解説」を参照してください。|  
  
## 解説  
 ほとんどの場合、`typeString` 文字列の情報項目として使用される XAML 型には、プレフィックスが付加されます。  CLR ジェネリック制約 \(<xref:System.Int32>、<xref:System.String> など\) の一般的な型は、CLR 基本クラス ライブラリから派生します。  これらのライブラリは一般的なフレームワーク固有の既定の XAML 名前空間にマッピングされないので、XAML の使用方法に対応するプレフィックスのマッピングが必要になります。  
  
 コンマを区切り記号として使用することで、複数の XAML 型名を指定できます。  
  
 ジェネリック制約自体がジェネリック型を使用している場合、ネストされた制約型引数はかっこ \(\) で囲むことができます。  
  
 この `x:TypeArguments` の定義は、.NET Framework XAML サービスに固有で、CLR バッキングを使用していることに注意してください。  言語レベルの定義については、「[\[MS\-XAML\] 第 5.3.11 節](http://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
## 使用例  
 この例では、次の XAML 名前空間の定義が宣言されていることを前提としています。  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### List\<String\>  
 `<scg:List x:TypeArguments="sys:String" ...>` は、<xref:System.String> 型引数で新しい <xref:System.Collections.Generic.List%601> をインスタンス化します。  
  
### Dictionary\<String,String\>  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` は、2 つの <xref:System.String> 型引数で新しい <xref:System.Collections.Generic.Dictionary%602> をインスタンス化します。  
  
### Queue\<KeyValuePair\<String,String\>\>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` は、内部制約型引数 <xref:System.String> および <xref:System.String> で <xref:System.Collections.Generic.KeyValuePair%602> の制約がある新しい <xref:System.Collections.Generic.Queue%601> をインスタンス化します。  
  
## XAML 2006 および WPF ジェネリック XAML の使用方法  
 XAML 2006 の使用方法と、WPF アプリケーションで使用される XAML では、通常、XAML からの `x:TypeArguments` とジェネリック型の使用方法に対して、次のような制約があります。  
  
-   ジェネリック型を参照するジェネリック XAML の使用方法をサポートできるのは、XAML ファイルのルート要素のみに限定されます。  
  
-   ルート要素は最低 1 つの型引数と共にジェネリック型にマッピングする必要があります。  <xref:System.Windows.Navigation.PageFunction%601> はその一例です。  ページ関数は、WPF でジェネリック XAML の使用方法をサポートする主なシナリオです。  
  
-   ジェネリック対応のルート要素の XAML オブジェクト要素も、`x:Class` を使用して特定のクラスを宣言する必要があります。  これは、WPF ビルド アクションを定義する場合にも当てはまります。  
  
-   `x:TypeArguments` は、ネストされたジェネリック制約を参照できません。  
  
## XAML 2009、または WPF 3.0\/3.5 に依存しない XAML 2006  
 XAML 2006 または XAML 2009 の .NET Framework XAML サービスでは、ジェネリック XAML の使用方法に対する WPF 関連の制約が緩和されています。  バッキング型システムとオブジェクト モデルがサポートできる XAML マークアップの任意の位置で、汎用オブジェクト要素をインスタンス化できます。  
  
 XAML 2009 を使用している場合は、一般的な言語プリミティブを取得するために CLR 基本型をマッピングする代わりに、[共通の XAML 言語プリミティブの組み込み型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)を `typeString` の情報アイテムとして使用できます。  たとえば、次を宣言できます \(プレフィックス マッピングは示されていません。x は XAML 2009 の XAML 言語 XAML 名前空間です\)。  
  
```  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 WPF で、[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] を対象としている場合は、XAML 2009 の機能を `x:TypeArguments` と共に使用できますが、Loose XAML \(マークアップ コンパイルされていない XAML\) に限定されます。  WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。  XAML をマークアップ コンパイルする必要がある場合、「XAML 2006 および WPF ジェネリック XAML の使用方法」に記載された制約に従って操作する必要があります。  
  
## 参照  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [x:Type Markup Extension](../../../docs/framework/xaml-services/x-type-markup-extension.md)   
 [共通の XAML 言語プリミティブの組み込み型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)   
 [Generics in XAML](../../../docs/framework/xaml-services/generics-in-xaml.md)