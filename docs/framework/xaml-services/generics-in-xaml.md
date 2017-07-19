---
title: "Generics in XAML | Microsoft Docs"
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
  - "generics [XAML Services]"
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
caps.latest.revision: 8
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 8
---
# Generics in XAML
System.Xaml に実装されている .NET Framework XAML サービスは、汎用的な CLR 型の使用をサポートします。  このサポートには、型引数としてのジェネリックの制約の指定、およびジェネリック コレクションのケースに適した `Add` メソッドを呼び出すことでの制約の適用が含まれます。  このトピックでは、XAML のジェネリック型の使用および参照に関するさまざまな側面を説明します。  
  
## x:TypeArguments  
 `x:TypeArguments` は、XAML 言語によって定義されているディレクティブです。  ジェネリック型によってサポートされる XAML 型のメンバーとして使用された場合、`x:TypeArguments` は、ジェネリックの制約型引数をバッキング コンストラクターに渡します。  構文例を含む、`x:TypeArguments` の .NET Framework XAML サービスでの使用に関する参照構文については、「[x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md)」を参照してください。  
  
 `x:TypeArguments` は文字列を受け取り、型コンバーターをサポートしているため、通常、XAML の使用方法においては属性として宣言されます。  
  
 XAML ノード ストリームでは、`x:TypeArguments` によって宣言される情報は、ノード ストリーム内の `StartObject` の位置にある <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=fullName> から取得できます。  <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=fullName> の戻り値は、<xref:System.Xaml.XamlType> 値の一覧です。  <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=fullName> を呼び出すことで、XAML の型がジェネリック型を表してるかどうかを判断できます。  
  
## XAML におけるジェネリックの規則および構文の表記規則  
 XAML では、ジェネリック型は常に制約されたジェネリック型として表される必要があります。制約のないジェネリック型は、XAML 型システムまたは XAML ノード ストリームには決して現れず、XAML マークアップで表すことはできません。  ジェネリックの入れ子にされた型の制約が `x:TypeArguments` によって参照されている場合、または `x:Type` がジェネリック型の CLR 型参照を指定している場合は、XAML 属性構文内でジェネリックを参照できます。  これは、.NET Framework XAML サービスによって定義された <xref:System.Xaml.Schema.XamlTypeTypeConverter> クラスを通じてサポートされます。  
  
 <xref:System.Xaml.Schema.XamlTypeTypeConverter> によって有効化された XAML 属性構文形式では、型の山かっことジェネリックの制約を使用する通常の MSIL\/CLR 構文表記規則が変更され、代わりに制約コンテナー用のかっこが代用されます。  例については、「[x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md)」を参照してください。  
  
## ジェネリックと XAML 2009 の機能  
 一般的な言語プリミティブの XAML 型を取得するために CLR 基本データ型をマッピングする代わりに、XAML 2009 を使用する場合は、[XAML 2009 組み込み型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)を `x:TypeArguments` の情報項目として使用できます。  たとえば、次を宣言できます \(プレフィックス マッピングは示されていません。`x` は XAML 2009 の XAML 言語 XAML 名前空間です\)。  
  
```  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## WPF と他の Framework 3.5 でのジェネリックのサポート  
 特に WPF を対象として XAML 2006 を使用している場合は、`x:TypeArguments` と同じ要素上に [x:Class](../../../docs/framework/xaml-services/x-class-directive.md) も指定する必要があり、その要素を XAML ドキュメントのルート要素にする必要があります。  ルート要素は最低 1 つの型引数と共にジェネリック型にマッピングする必要があります。  <xref:System.Windows.Navigation.PageFunction%601> はその一例です。  
  
 ジェネリックの使用をサポートするための考えられる代替手段として、ジェネリック型を返すことができるカスタム マークアップ拡張を定義するか、ジェネリック型から派生するが自身のクラス定義内でジェネリック制約を平坦化するラッピング クラス定義を提供します。  
  
 WPF で、[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] を対象としている場合は、XAML 2009 の機能を `x:TypeArguments` と共に使用できますが、Loose XAML \(マークアップ コンパイルされていない XAML\) に限定されます。  WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。  
  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] の [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] におけるカスタム ワークフローでは、ジェネリック XAML の使用をサポートしていません。  
  
## 参照  
 [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md)   
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [Built\-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)