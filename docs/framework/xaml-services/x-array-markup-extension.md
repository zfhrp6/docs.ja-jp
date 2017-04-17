---
title: "x:Array Markup Extension | Microsoft Docs"
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
  - "x:Array"
  - "xArray"
helpviewer_keywords: 
  - "x:Array [XAML Services]"
  - "XAML [XAML Services], x:Array markup extension"
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
caps.latest.revision: 20
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 20
---
# x:Array Markup Extension
マークアップ拡張機能を通じ、XAML のオブジェクトの配列を全般的にサポートします。  これは、\[MS\-XAML\] の `x:ArrayExtension` XAML 型に対応します。  
  
## XAML オブジェクト要素の使用方法  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`typeName`|`x:Array` に格納される型の名前。  `typeName` は、XAML 型定義を含む XAML 名前空間のプレフィックスとなる場合があります \(通常はプレフィックスとなる\)。|  
|`arrayContents`|組み込みの `ArrayExtension.Items` プロパティに割り当てられた項目コンテンツ。  通常、これらの項目は `x:Array` 開始タグと終了タグに囲まれた 1 つ以上のオブジェクト要素として指定されます。  ここで指定されたオブジェクトは、`typeName` で指定された XAML 型に割り当て可能であることが予期されます。|  
  
## 解説  
 `Type` は、すべての `x:Array` オブジェクト要素に必須の属性です。  `Type` パラメーターの値には必ずしも `x:Type` マークアップ拡張機能を使用する必要はありません。型の短い名前が XAML 型であれば、文字列として指定することができます。  
  
 .NET Framework XAML サービス実装では、入力された XAML 型と作成された配列の出力 CLR <xref:System.Type> との関係は、マークアップ拡張機能のサービス コンテキストの影響下にあります。  出力される <xref:System.Type> は、入力された XAML 型の <xref:System.Xaml.XamlType.UnderlyingType%2A> ですが、その前に、XAML スキーマ コンテキストとそのコンテキストが提供する <xref:System.Windows.Markup.IXamlTypeResolver> サービスに基づいて必要な <xref:System.Xaml.XamlType> が検索されます。  
  
 処理時に、配列のコンテンツは `ArrayExtension.Items` 組み込みプロパティに割り当てられます。  <xref:System.Windows.Markup.ArrayExtension> 実装では、これは <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=fullName> によって表されます。  
  
 .NET Framework XAML サービス実装では、このマークアップ拡張機能の処理は、<xref:System.Windows.Markup.ArrayExtension> クラスによって定義されます。  <xref:System.Windows.Markup.ArrayExtension> はシールされておらず、カスタム配列の型にマークアップ拡張機能を実装する際の基礎として使用できます。  
  
 `x:Array` は XAML の一般的な言語拡張機能を対象にしています。  ただし `x:Array` は、XAML がサポートするコレクションを構造化プロパティ コンテンツとして受け入れる、特定のプロパティの XAML 値を指定する際にも役に立ちます。  たとえば、`x:Array` を使用して、<xref:System.Collections.IEnumerable> プロパティのコンテンツを指定できます。  
  
 `x:Array` はマークアップ拡張機能です。  一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。  `x:Array` は代替の属性値処理を指定する代わりに、その属性値の中のテキスト コンテンツを処理します。このことから、`x:Array` は、この規則とは一部異なります。  この動作によって、既存のコンテンツ モデルではサポートされない型を 1 つの配列にまとめ、後から分離コード内で、指定した配列にアクセスして参照することが可能となります。つまり、<xref:System.Array> を呼び出して、個々の配列項目を取得することができます。  
  
 XAML のすべてのマークアップ拡張機能では、それぞれの属性構文で中かっこ \({,}`)` を使用します。これは規約であり、これに従って XAML プロセッサは、マークアップ拡張機能で属性値を処理する必要があることを認識します。  一般的なマークアップ拡張機能の詳細については、「[Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)」を参照してください。  
  
 XAML 2009 では、`x:Array` はマークアップ拡張機能ではなく、言語のプリミティブ型として定義されています。  詳細については、「[Built\-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)」を参照してください。  
  
## WPF の使用上の注意  
 通常、`x:Array` を設定するオブジェクト要素は、[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] の XML 名前空間に存在する要素ではないため、既定以外の XAML 名前空間に対してプレフィックスのマッピングが必要です。  
  
 たとえば、以下に、2 つの文字列を持つ単純な配列があり、\(`x` に加えて\) `sys` プレフィックスが配列レベルで定義されています。  
  
 \[xaml\]  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 配列の要素として使用されるカスタム型については、クラスは XAML でオブジェクト要素としてインスタンス化できるという要件もサポートする必要があります。  詳細については、「[WPF における XAML とカスタム クラス](../../../ocs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)」を参照してください。  
  
## 参照  
 [マークアップ拡張機能と WPF XAML](../../../ocs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [Types Migrated from WPF to System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)