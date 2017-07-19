---
title: "x:Code Intrinsic XAML Type | Microsoft Docs"
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
  - "Code"
  - "x:Code"
  - "xCode"
helpviewer_keywords: 
  - "Code directive in XAML [XAML Services]"
  - "x:Code XAML directive element [XAML Services]"
  - "XAML [XAML Services], x:Code directive element"
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
caps.latest.revision: 19
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 19
---
# x:Code Intrinsic XAML Type
XAML 稼動環境内にコードを配置できます。  このようなコードは、XAML をコンパイルする XAML プロセッサ実装によってコンパイルすることもできれば、ランタイムによって解釈させるなど、後から使用するために XAML 稼動環境内に残しておくこともできます。  
  
## XAML オブジェクト要素の使用方法  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## 解説  
 `x:Code` XAML ディレクティブ要素内のコードも、指定された汎用 XML 名前空間と XAML 名前空間内で解釈されます。  したがって、`x:Code` 用に使用されるコードを `CDATA` セグメントで囲むことも通常は必要です。  
  
 `x:Code` は、どの XAML 稼動環境の配置機構でも使用できるとは限りません。  特定のフレームワーク \(たとえば、WPF\) では、コードはコンパイルする必要があります。  その他のフレームワークでは、`x:Code` の使用は一般に許可されていません。  
  
 マネージ `x:Code` コンテンツを許容するフレームワークの場合、`x:Code` コンテンツに対して使用される適切な言語コンパイラは、アプリケーションをコンパイルするために使用される格納元プロジェクトの設定とターゲットによって決定されます。  
  
## WPF の使用上の注意  
 WPF の場合、`x:Code` 内で宣言されるコードに関して、いくつかの制限事項があります。  
  
-   `x:Code` ディレクティブ要素は、XAML 稼動環境のルート要素の直接の子要素でなければなりません。  
  
-   [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) は、親ルート要素で提供される必要があります。  
  
-   コンパイル時に、`x:Code` 内に配置されているコードは、その XAML ページに対して既に作成された部分クラスのスコープ内にあるものとして扱われます。  このため、定義するすべてのコードは、その部分クラスのメンバーまたは変数である必要があります。  
  
-   部分クラスの内側にクラスを入れ子にすること以外の方法で、追加クラスを定義することはできません \(入れ子にすることはできますが、入れ子のクラスは XAML では参照できないので、一般的ではありません\)。  既存の部分クラスに対して使用されている名前空間以外の CLR 名前空間を定義したり追加したりすることはできません。  
  
-   部分クラスの CLR 名前空間の外側のコード エンティティに対する参照は、すべて完全修飾されている必要があります。  宣言されるメンバーが、部分クラスのオーバーライド可能なメンバーに対するオーバーライドである場合は、言語固有のオーバーライド キーワードを使用してこのことを指定する必要があります。  `x:Code` のスコープで宣言されたメンバーと、XAML から作成された部分クラスのメンバーとの間に、コンパイラから報告されるような競合がある場合は、XAML ファイルを読み込んだりコンパイルしたりすることはできません。  
  
## 参照  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [WPF における分離コードと XAML](../../../ocs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)   
 [XAML の概要 \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)