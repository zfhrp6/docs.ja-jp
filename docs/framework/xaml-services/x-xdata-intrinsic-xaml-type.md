---
title: "x:XData Intrinsic XAML Type | Microsoft Docs"
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
  - "x:XData"
  - "XData"
  - "xXData"
helpviewer_keywords: 
  - "XAML [XAML Services], x:XData directive element"
  - "XData in XAML [XAML Services]"
  - "x:XData XAML directive element [XAML Services]"
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
caps.latest.revision: 17
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 17
---
# x:XData Intrinsic XAML Type
XML データ アイランドを XAML 稼動環境内に配置できるようにします。  `x:XData` 内の XML 要素は、動作している既定の XAML 名前空間またはその他の XAML 名前空間の一部として扱うことはできません。  `x:XData` は、任意の整形式 XML を含むことができます。  
  
## XAML オブジェクト要素の使用方法  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`elementDataRoot`|囲まれたデータ アイランドの単一ルート要素。  ほとんどのコンシューマーでは、最終的に、単一のルートを持たない XML は無効と見なされます。  特に、`x:XData` が、WPF \(または XML ソースをデータ バインディングに使用するその他各種テクノロジ\) の XML データ ソースとして使用される場合、単一のルートが必要になります。|  
|`[elementData]`|省略可能です。  XML データを表す XML。  要素データとして任意の数の要素を含めることができる、入れ子にした要素を他の要素に含めることができるなど、XML の一般規則が適用されます。|  
  
## 解説  
 `x:XData` オブジェクト内の XML 要素は、このデータ内で、格納している側の XMLDOM のすべての考えられる名前空間およびプレフィックスを再宣言できます。  
  
 XML データおよび `x:XData` 組み込み XAML 型へのプログラムによるアクセスは、.NET Framework XAML サービスでは、<xref:System.Windows.Markup.XData> クラスを介して実行できます。  
  
## WPF の使用上の注意  
 The `x:XData` オブジェクトは主に、<xref:System.Windows.Data.XmlDataProvider> の子オブジェクトとして使用されるか、<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=fullName> プロパティ \(XAML では、通常、プロパティ要素構文で表される\) の子オブジェクトとして使用されます。  
  
 一般に、データ アイランド内では、基本 XML 名前空間を新しい既定の XML 名前空間として再定義する必要があります \(空の文字列に設定\)。  この方法は、単純なデータ アイランドの場合には最も簡単です。データを参照やバインドに <xref:System.Windows.Data.Binding.XPath%2A> 式を使用することでプレフィックスが不要になるからです。  より複雑なデータ アイランドでは、データのプレフィックスを複数定義し、ルートにある XML 名前空間に特定のプレフィックスを使用するという方法を選択できます。  この場合は、すべての <xref:System.Windows.Data.Binding.XPath%2A> 式参照において、名前空間にマップされた適切なプレフィックスを付ける必要があります。  詳細については、「[データ バインドの概要](../../../ocs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
 技術的には、`x:XData` は <xref:System.Xml.Serialization.IXmlSerializable> 型の任意のプロパティのコンテンツとして使用できます。  ただし、よく使用されているのは <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=fullName> の実装のみです。  
  
## 参照  
 <xref:System.Windows.Data.XmlDataProvider>   
 [データ バインドの概要](../../../ocs/framework/wpf/data/data-binding-overview.md)   
 [バインドのマークアップ拡張機能](../../../ocs/framework/wpf/advanced/binding-markup-extension.md)