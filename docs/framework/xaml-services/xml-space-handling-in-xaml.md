---
title: "xml:space Handling in XAML | Microsoft Docs"
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
  - "XAML [XAML Services], xml:space attribute"
  - "XAML [XAML Services], whitespace processing"
  - "xml:space attribute [XAML Services]"
  - "whitespace processing [XAML Services]"
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
caps.latest.revision: 15
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 15
---
# xml:space Handling in XAML
`xml:space` 属性は XML で定義される属性であり、重要な空白の処理動作をオブジェクト要素内で宣言します。  この動作は、`xml:space` が宣言されている要素に含まれるすべてのコンテンツ \(内部テキスト\) に関連すると同時に、そのスコープは子要素にも及びます。  
  
## XAML 属性の使用方法  
  
```  
<object xml:space="preserve" />  
```  
  
 または  
  
```  
<object xml:space="default" />  
```  
  
## 解説  
 2 つの指定可能な値を含め、XAML の `xml:space` 属性の定義は、XML の W3C 仕様で "特別な属性" として定義されている `xml:space` から派生しています。  
  
 `xml:space` 属性の既定値は、リテラル値の `"default"` です。  値が `"default"` の場合、または `xml:space` がまったく示されていない場合、重要な空白の解析は、トピック「[Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)」で定義されているように、既定の動作で処理されます。  
  
 オブジェクト要素のコンテンツ内で空白を保持するには、そのオブジェクト要素で `xml:space="preserve"` を指定します。  
  
 ほとんどの解釈では、`xml:space` 属性の効果と属性の値は、子要素に反映されます。  
  
 XAML での空白の処理の詳細については、「[Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)」を参照してください。  
  
## 参照  
 [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)   
 [XAML の概要 \(WPF\)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)