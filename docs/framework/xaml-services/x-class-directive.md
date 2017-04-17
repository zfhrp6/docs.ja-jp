---
title: "x:Class Directive | Microsoft Docs"
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
  - "x:Class"
  - "xClass"
  - "Class"
helpviewer_keywords: 
  - "Class attribute in XAML [XAML Services]"
  - "XAML [XAML Services], x:Class attribute"
  - "x:Class attribute [XAML Services]"
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
caps.latest.revision: 27
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 26
---
# x:Class Directive
マークアップと分離コード間を部分クラスで結合するように、XAML のマークアップ コンパイルを構成します。  コードの部分クラスは、[!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] 言語で個別のコード ファイル内に定義され、マークアップの部分クラスは、通常 XAML のコンパイル時にコード生成によって作成されます。  
  
## XAML 属性の使用方法  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`namespace`|省略可能です。  `classname` で識別される部分クラスを含む [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] 名前空間を指定します。  `namespace` を指定する場合は、`namespace` と `classname` をドット \(.\) で区切ります。  「解説」を参照してください。|  
|`classname`|必ず指定します。  読み込まれた XAML、およびその XAML の分離コードを接続する部分クラスの [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] 名を指定します。|  
  
## 依存関係  
 `x:Class` は、XAML 稼動環境のルート要素でのみ指定できます。  `x:Class` は、XAML 稼動環境内に親を持つ任意のオブジェクトで無効です。  詳細については、「[\[MS\-XAML\] 第 4.3.1.6 節](http://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
## 解説  
 `namespace` の値には、関連する名前空間を名前の階層に編成するために追加のドットを含めることができます。これは、.NET Framework プログラミングの一般的な手法です。  `x:Class` の値の文字列に含まれる最後のドットのみが、`namespace` と `classname` の区切りとして解釈されます。`x:Class` として使用するクラスは、入れ子にできません。  入れ子になったクラスが許可されると `x:Class` 文字列のドットの意味の判断があいまいになるので、入れ子になったクラスは許可されません。  
  
 `x:Class` を使用する既存のプログラミング モデルの `x:Class` は、分離コードを一切持たない XAML ページが存在することはまったく問題ないという意味で省略可能です。  ただし、XAML を使用するフレームワークによって実装されたビルド アクションにはこの機能が作用します。  また、さまざまな種類の XAML 固有コンテンツがアプリケーション モデル内や対応するビルド アクションにおいて担う役割も、`x:Class` の機能に影響します。  イベント処理属性の値を XAML で宣言する場合や、\(定義しているクラスが分離コード クラスに存在するような\) カスタム要素を XAML でインスタンス化する場合には、分離コードの該当クラスに対する `x:Class` ディレクティブ参照 \(または [x:Subclass](../../../docs/framework/xaml-services/x-subclass-directive.md)\) を指定する必要があります。  
  
 `x:Class` ディレクティブの値は、クラスの完全修飾名を指定する文字列です。ただし、アセンブリの情報は含まれません \(<xref:System.Type.FullName%2A?displayProperty=fullName> に相当します\)。  単純なアプリケーションの場合、CLR 名前空間情報を省略することもできますが、分離コードもそのように構成されている \(コード定義がクラス レベルで開始する\) ことが条件となります。  
  
 ページまたはアプリケーション定義の分離コード ファイルは、コンパイル済みアプリケーションを作成しマークアップ コンパイルに関与するプロジェクトの一部として含まれているコード ファイル内にある必要があります。  CLR クラスの名前規則に従う必要があります。  詳細については、「[Framework デザイン ガイドライン](../../../ml/index.xml)」を参照してください。  既定では、分離コード クラスは `public` である必要がありますが、[x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)を使用して、異なるアクセス レベルとして定義できます。  
  
 この `x:Class` 属性の解釈が当てはまるのは、CLR ベースの XAML 実装、特に、.NET Framework XAML サービスのみです。  CLR に基づかず、.NET Framework XAML サービスを使用しない他の XAML 実装では、XAML マークアップと対応するランタイム コードを関連付けるために異なる解決式を使用する場合があります。  `x:Class` の一般的な解釈の詳細については、「[\[MS\-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
 特定レベルのアーキテクチャでは、`x:Class` の意味は、.NET Framework XAML サービスで定義されていません。  これは、.NET Framework XAML サービスで、XAML マークアップと対応するコードが関連付けられるプログラミング モデルが指定されていないためです。  `x:Class` ディレクティブの用途は他にも考えられます。XAML マークアップと CLR ベースの分離コードを関連付ける方法を定義する目的で、そうした用途が、プログラミング モデルまたはアプリケーション モデルを使用する特定のフレームワークによって実装される場合があります。  それぞれのフレームワークは、一部の動作を実現する独自のビルド アクションや、ビルド環境に含める必要のある特定のコンポーネントを備えています。  フレームワーク内では、分離コードで使用される特定の CLR 言語に応じてビルド アクションは変化することもあります。  
  
## WPF プログラミング モデルの x:Class  
 WPF アプリケーションおよび WPF アプリケーション モデルでは、`x:Class` を、XAML ファイルのルートで、コンパイルされている任意の要素の属性 \(XAML が `Page` ビルド アクションによって WPF アプリケーション プロジェクトに組み込まれている場合\)、またはコンパイル済み WPF アプリケーションのアプリケーション定義の <xref:System.Windows.Application> ルートの属性として宣言できます。  [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] および [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] の WPF XAML コンパイラでは、ページ ルートまたはアプリケーション ルート以外の要素、あるいはコンパイルされていない WPF XAML ファイルで `x:Class` を宣言すると、コンパイル時エラーが発生します。  WPF の `x:Class` 処理に関連したその他の情報については、「[WPF における分離コードと XAML](../../../ocs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)」を参照してください。  
  
## Windows Workflow Foundation の x:Class  
 Windows Workflow Foundation の場合、`x:Class` によって名前指定されるのは、完全に XAML で構成されたカスタム アクティビティのクラスか、または分離コードを持つアクティビティ デザイナー用の XAML ページの部分クラスです。  
  
## Silverlight の使用上の注意  
 Silverlight 用の `x:Class` に関しては、別途ドキュメントが用意されています。  詳細については、「[XAML 名前空間 \(x:\) 言語機能 \(Silverlight\)](http://go.microsoft.com/fwlink/?LinkId=199081)」を参照してください。  
  
## 参照  
 [x:Subclass Directive](../../../docs/framework/xaml-services/x-subclass-directive.md)   
 [WPF における XAML とカスタム クラス](../../../ocs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)   
 [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)   
 [Types Migrated from WPF to System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)