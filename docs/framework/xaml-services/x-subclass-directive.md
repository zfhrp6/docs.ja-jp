---
title: "x:Subclass Directive | Microsoft Docs"
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
  - "Subclass"
  - "xSubclass"
  - "x:Subclass"
helpviewer_keywords: 
  - "x:Subclass attribute [XAML Services]"
  - "XAML [XAML Services], x:Subclass attribute"
  - "Subclass attribute in XAML [XAML Services]"
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
caps.latest.revision: 20
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 20
---
# x:Subclass Directive
`x:Class` も提供される場合の XAML マークアップのコンパイル動作を変更します。  `x:Class` クラスに基づいて部分クラスを作成する代わりに、提供された `x:Class` を中間クラスとして作成し、ユーザーが提供した派生クラスは `x:Class` に基づくものと想定されます。  
  
## XAML 属性の使用方法  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`namespace`|省略可能です。  `classname` を含む CLR 名前空間を指定します。  `namespace` を指定する場合は、`namespace` と `classname` をドット \(.\) で区切ります。|  
|`classname`|必ず指定します。  読み込まれた XAML、およびその XAML の分離コードを接続する部分クラスの CLR 名を指定します。  「解説」を参照してください。|  
|`subclassNamespace`|省略可能です。  各名前空間が他の名前空間を解決できる場合、`namespace` と異なっていてもかまいません。  `subclassName` を含む CLR 名前空間を指定します。  `subclassName` を指定する場合は、`subclassNamespace` と `subclassName` をドット \(.\) で区切ります。|  
|`subclassName`|必ず指定します。  サブクラスの CLR 名を指定します。|  
  
## 依存関係  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) も同じオブジェクトに提供される必要があり、そのオブジェクトは XAML 稼動環境のルート要素である必要があります。  
  
## 解説  
 `x:Subclass` は、主として、部分クラス宣言をサポートしない言語のためのものです。  
  
 `x:Subclass` として使用されるクラスは入れ子のクラスにすることはできず、`x:Subclass` は、「依存関係」のセクションで説明したとおり、ルート オブジェクトを参照している必要があります。  
  
 それ以外の点について、`x:Subclass` の概念的な意味は、.NET Framework XAML サービス実装では定義されていません。  これは、.NET Framework XAML サービスの動作で、XAML マークアップと対応するコードが関連付けられるプログラミング モデル全体が指定されていないためです。  `x:Class` と `x:Subclass` に関連するその他の概念の実装は、XAML マークアップ、コンパイルされたマークアップ、および CLR ベースの分離コードを関連付ける方法を定義するために、プログラミング モデルまたはアプリケーション モデルを使用する特定のフレームワークによって実行されます。  それぞれのフレームワークは、一部の動作を実現する独自のビルド アクションや、ビルド環境に含める必要のある特定のコンポーネントを備えています。  フレームワーク内では、分離コードで使用される特定の CLR 言語に応じてビルド アクションは変化することもあります。  
  
## WPF の使用上の注意  
 `x:Subclass` は、ページ ルート上に配置することも、既に `x:Class` を持つアプリケーション定義内の <xref:System.Windows.Application> ルート上に配置することもできます。  `x:Subclass`  を、ページ ルートまたはアプリケーション ルート以外の要素で宣言すると、または `x:Class` が存在しない場所で指定すると、コンパイル時エラーが発生します。  
  
 `x:Subclass` のシナリオで正しく動作する派生クラスを作成するのは、かなり複雑な作業です。  中間ファイル \(マークアップ コンパイルによってプロジェクトの obj フォルダーに生成される .g ファイルで、名前には .xaml ファイル名が含まれる\) の確認が必要になる場合があります。  これらの中間ファイルは、コンパイル済みアプリケーション内の結合された部分クラスにおいて、特定のプログラミング構造の起点を特定するのに役立ちます。  
  
 コンパイル時に中間クラスで作成されるハンドラーのスタブをオーバーライドするには、派生クラス内のイベント ハンドラーが `internal override` \([!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] では `Friend Overrides`\) でなければなりません。  それ以外の場合は、派生クラスの実装が中間クラスの実装を隠し \(シャドウ\)、中間クラスのハンドラーは呼び出されません。  
  
 `x:Class` と `x:Subclass` の両方を定義する場合、`x:Class` によって参照されるクラスの実装を提供する必要はありません。  コンパイラが中間ファイルで作成するクラスについてガイダンスを得られるよう、`x:Class` 属性を使用して名前を指定することだけが必要です \(この場合、コンパイラは既定の名前を選択しません\)。  `x:Class` クラスに実装を提供してもかまいませんが、これは `x:Class` と `x:Subclass` の両方を使用する標準的なシナリオでは行いません。  
  
## 参照  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [WPF における XAML とカスタム クラス](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)