---
title: "x:FactoryMethod Directive | Microsoft Docs"
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
  - "XAML. x:FactoryMethod directive [XAML Services]"
  - "FactoryMethod directive in XAML [XAML Services]"
  - "x:FactoryMethod directive [XAML Services]"
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: 8
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 8
---
# x:FactoryMethod Directive
XAML プロセッサが、バッキング型を解決した後にオブジェクトを初期化するために使用する、コンストラクター以外のメソッドを指定します。  
  
## XAML 属性の使用方法、x:Arguments なし  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## XAML 属性の使用方法、要素としての x:Arguments  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`methodname`|XAML プロセッサが、`object` として指定されるインスタンスを初期化するために、XAML プロセッサが呼び出すメソッドの文字列メソッド名。  「解説」を参照してください。|  
|`oneOrMoreObjectElements`|ファクトリ メソッド パラメーターを指定するオブジェクトの、1 つ以上のオブジェクト要素。  ファクトリ メソッドに引数が渡される順序を指定するので、順序は重要です。|  
  
## 解説  
 `methodname` がインスタンス メソッドである場合、修飾できません。  
  
 ファクトリ メソッドとしての静的メソッドはサポートされます。  `methodname` が静的メソッドである場合、`methodname` は *typeName*.*methodName* の組み合わせとして指定されます。ここで、*typeName* は、静的ファクトリ メソッドを定義するクラスの名前です。  *typeName* は、マップされた xmlns の型を表す場合は、プレフィックスで修飾されています。  *typeName* は、`typeof(``object``)` とは異なる型のこともあります。  
  
 ファクトリ メソッドは、関連するオブジェクト要素をサポートする型の、宣言済みパブリック メソッドである必要があります。  
  
 ファクトリ メソッドは、関連オブジェクトに割り当てることができるインスタンスを返す必要があります。  ファクトリ メソッドが null 値を返すことはありません。  
  
 `x:Arguments` は、ファクトリ メソッドのシグネチャの最優先の一致の原則に従います。  一致においては、最初にパラメーター数が評価されます。  パラメーター数に 1 つ以上の一致が見られる場合、パラメーター型が評価され、最優先の一致が決定されます。  評価のこのフェーズの後にあいまいさが残る場合は、XAML プロセッサの動作は未定義です。  
  
 `x:FactoryMethod` 要素の使用方法は、一般的な意味合いにおけるプロパティ要素の使用方法ではありません。これは、ディレクティブのマークアップは、格納オブジェクトの要素の型を参照しないためです。  要素の使用方法は、属性の使用方法よりも一般的ではないとされています。  `x:Arguments` \(属性または要素の使用方法\) は、`x:FactoryMethod` 要素の使用方法と共に使用できますが、「使用方法」のセクションには具体的に示されません。  
  
 要素としての `x:FactoryMethod` はその他のプロパティ要素、要素として指定される `x:Arguments`、およびコンテンツ\/内部テキスト\/初期化テキストの前に配置される必要があります。  
  
## 参照  
 [x:Arguments Directive](../../../docs/framework/xaml-services/x-arguments-directive.md)