---
title: "x:Null Markup Extension | Microsoft Docs"
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
  - "NullExtension"
  - "x:NullExtension"
  - "x:Null"
  - "Null"
  - "xNull"
helpviewer_keywords: 
  - "Null markup extension in XAML [XAML Services]"
  - "x:Null markup extension [XAML Services]"
  - "XAML [XAML Services], x:Null markup extension"
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
caps.latest.revision: 20
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 20
---
# x:Null Markup Extension
XAML メンバーの値として `null` を指定します。  
  
## XAML 属性の使用方法  
  
```  
<object property="{x:Null}" .../>  
```  
  
## 解説  
 [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] および [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] における null 参照のキーワードは null です。  null 参照の [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] キーワードは `Nothing` ですが、どの分離コード言語が XAML と関連付けられているかに関係なく、XAML の使用方法としては常に `{x:Null}` を使用してください。  
  
 `x:Null` のマークアップ拡張機能には、設定可能なプロパティはありません。  
  
 null の使用方法は多くの場合、CLR <xref:System.Nullable%601> 値の XAML メンバーの公開と関連付けられます。  
  
 XAML のあらゆるマークアップ拡張機能と同様、`x:Null` マークアップ拡張機能は、属性値の処理をリテラルやイベント ハンドラー参照以外にエスケープする場合、中かっこ \(`{,}`\) を使用します。  属性構文は、このマークアップ拡張機能で最も多く使用される構文です。  `x:Null` マークアップ拡張機能では位置指定パラメーターや構築引数は使用されないので、オブジェクト要素構文 `<x:Null />` は技術的には使用できますが、使用されることはまれです。  
  
 マークアップ拡張機能については、「[マークアップ拡張機能と WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
 .NET Framework XAML サービスでは、このマークアップ拡張機能の処理は、<xref:System.Windows.Markup.NullExtension> クラスによって定義されます。  
  
## WPF の使用上の注意  
 `null` は、参照型の依存関係プロパティの初期未設定値であるとは限らないことに注意してください。  初期既定値は、依存関係プロパティごとに異なることがあります。また、プロパティ固有のメタデータに基づいていることがあります。  依存関係プロパティの多くは、その検証コールバックの実装により、マークアップまたはコードのいずれによる場合でも、`null` を値として許容しません。  依存関係プロパティの詳細については、「[依存関係プロパティの概要](../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.DependencyProperty.UnsetValue>   
 [XAML の概要 \(WPF\)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [マークアップ拡張機能と WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)