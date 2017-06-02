---
title: "x:Reference Markup Extension | Microsoft Docs"
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
  - "x:Reference markup extension [XAML Services]"
  - "XAML [XAML Services], x:Reference Markup Extension"
  - "Reference markup extension [XAML Services]"
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
caps.latest.revision: 8
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 8
---
# x:Reference Markup Extension
XAML マークアップの別の場所で宣言されているインスタンスを参照します。  参照は、要素の `x:Name` を参照します。  
  
## XAML 属性の使用方法  
  
```  
<object property="{x:Reference instancexName}" .../>  
```  
  
## XAML オブジェクト要素の使用方法  
  
```  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`instancexName`|参照先のインスタンスの `x:Name` 値 \(または <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> によって識別されるプロパティの値\)。|  
  
## 解説  
 `x:Reference` は、WPF など、特定のフレームワークでは他の方法によって実装されていた要素の参照の概念に対して、XAML 言語レベルのサポートを提供します。  
  
## x:Reference と WPF  
 WPF と XAML 2006 では、要素の参照は、<xref:System.Windows.Data.Binding.ElementName%2A> バインディングのフレームワークレベル機能によって対応していました。  大半の WPF アプリケーションおよびシナリオでは、<xref:System.Windows.Data.Binding.ElementName%2A> バインディングを継続して使用する必要があります。  ただし、データ コンテキストまたはスコープに関するその他の考慮事項によってデータ バインディングが実用的ではなくなる場合や、マークアップ コンパイルを伴わない場合などは例外です。  
  
 `x:Reference` は、XAML 2009 で定義されている構造です。  WPF では XAML 2009 の機能を使用できますが、WPF マークアップ コンパイルされていない XAML に限定されます。  マークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 言語のキーワードと機能をサポートしていません。