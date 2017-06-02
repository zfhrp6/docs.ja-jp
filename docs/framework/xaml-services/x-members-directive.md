---
title: "x:Members Directive | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
caps.latest.revision: 5
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 5
---
# x:Members Directive
マークアップで定義された一連の \(親要素の x:Class に適用される\) メンバーを保持します。  
  
## XAML 属性の使用方法  
  
```  
  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`className`|XAML 稼動環境のバッキング クラスまたは部分クラスの名前。  「解説」を参照してください。|  
|`oneOrMoreMembers`|メンバーの定義を表す 1 つ以上のオブジェクト要素。  通常、これらは `x:Property` オブジェクト要素です。  「解説」を参照してください。|  
  
## 解説  
 .NET Framework XAML サービス実装では、`x:Members` に対するバッキング クラスや基になるメンバー実装は存在しません。  `x:Members` は、あらゆる型のメンバーとして存在できる特殊な XAML メンバーです。  XAML ノード ストリームにおいて、`x:Members` は、XAML 言語の XAML 名前空間の `Members` という名前のメンバーとして表されます。  メンバー `Members` には、`Member` オブジェクトの読み取り専用のジェネリック リストが格納されます。  通常のマークアップでは、個々のメンバーが `x:Property` プロパティの要素として指定されます。  `x:Property` は、型のプロパティ専用の明確な型であり、`x:Member` に割り当てることができます。  詳細については、「[x:Property Directive](../../../docs/framework/xaml-services/x-property-directive.md)」を参照してください。  
  
 マークアップでメンバー定義を指定する手段として `x:Members` を実際に使用できるようにするためには、変更可能なクラスにメンバーが関連付けられている必要があります。  想定されているモデルは、`x:Class` を指定する型のメンバーとして `x:Members` が存在することです。  ただし、型とメンバーを関連付けたり動的なメンバー定義を生成したりするためのメカニズムは、.NET Framework XAML サービス レベルではサポートされていません。  この点は、XAML に基づくメンバー定義に対応したアプリケーション モデルを持つ個々のフレームワークに委ねられています。  通常、そのような機能をサポートするためには、XAML をマークアップ コンパイルし、分離コードと統合するか、純粋な XAML 由来のアセンブリを生成する MSBUILD ビルド アクションが必要です。  
  
## Windows Workflow Foundation の x:Members  
 Windows Workflow Foundation の場合、`x:Members` に格納されるのは、完全に XAML で構成されたカスタム アクティビティのメンバーか、またはアクティビティ デザイナー用に分離コードと共に XAML で定義された動的メンバーです。  また、XAML 稼動環境のルート要素には、`x:Class` が指定されている必要があります。  これは、.NET Framework XAML サービス レベルの要件ではありませんが、カスタム アクティビティおよび Windows Workflow Foundation XAML 全般をサポートする MSBUILD ビルド アクションによって XAML 稼動環境が読み込まれた場合には、これが要件となります。  `x:Class` を宣言するオブジェクト要素のマークアップにおいて、`x:Members` は最初の子要素である必要があります。