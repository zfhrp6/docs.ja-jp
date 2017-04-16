---
title: "WPF における分離コードと XAML | Microsoft Docs"
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
  - "分離コード ファイル, XAML"
  - "XAML, 分離コード"
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# WPF における分離コードと XAML
<a name="introduction"></a> 分離コードとは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページがマークアップ コンパイルされる際に、マークアップ定義オブジェクトによって結合されるコードを表す用語です。  ここでは、分離コードの要件と、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 内のコードの代替インライン コード機構について説明します。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [必要条件](#Prerequisites)  
  
-   [分離コードと XAML 言語](#codebehind_and_the_xaml_language)  
  
-   [WPF における分離コード、イベント ハンドラー、および部分クラスの要件](#Code_behind__Event_Handler__and_Partial_Class)  
  
-   [x:Code](#x_Code)  
  
-   [インライン コードの制限](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## 必要条件  
 このトピックでは、「[XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)」を通読していることと、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] およびオブジェクト指向プログラミングに関する基礎知識があることを前提にしています。  
  
<a name="codebehind_and_the_xaml_language"></a>   
## 分離コードと XAML 言語  
 XAML 言語には、コード ファイルをマークアップ ファイル側からマークアップ ファイルに関連付けることのできる言語レベルの機能が含まれています。  具体的には、XAML 言語で [x:Class ディレクティブ](../../../../docs/framework/xaml-services/x-class-directive.md)、[x:Subclass ディレクティブ](../../../../docs/framework/xaml-services/x-subclass-directive.md) および [x:ClassModifier ディレクティブ](../../../../docs/framework/xaml-services/x-classmodifier-directive.md) という言語機能が定義されています。  XAML 言語は、コードの生成方法、およびマークアップとコードの統合方法を正確に指定するものではありません。  コードの統合方法、アプリケーションとプログラミング モデルでの XAML の使用方法、これらの操作に必要なビルド アクションまたは他のサポート機能の判別は、WPF などのフレームワークで行います。  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## WPF における分離コード、イベント ハンドラー、および部分クラスの要件  
  
-   部分クラスは、ルート要素をサポートする型から派生する必要があります。  
  
-   マークアップ コンパイルによるビルド アクションの既定の動作では、分離コード側の部分クラス定義における派生を空白のままにできます。  コンパイル結果は、指定されていない場合でも、ページ ルートのバッキング型が部分クラスの基礎になると仮定されます。  ただし、この動作に依存することはお勧めしません。  
  
-   分離コードで記述したイベント ハンドラーは、インスタンス メソッドである必要があります。静的メソッドにすることはできません。  これらのメソッドは、`x:Class` で識別される CLR 名前空間内の部分クラスによって定義される必要があります。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサがイベント ハンドラーの検索を異なるクラス スコープ内のイベント接続で行うように、イベント ハンドラーの名前を修飾することはできません。  
  
-   ハンドラーは、バッキング型システム内の適切なイベントのデリゲートと一致する必要があります。  
  
-   [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] 言語の場合に限り、言語固有の `Handles` キーワードを使用すると、ハンドラーを、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 内の属性に関連付ける代わりに、ハンドラー宣言内のインスタンスとイベントに関連付けることができます。  ただし、この手法にはいくつかの制限もあります。一定のルーティング イベント シナリオや添付イベントなど、`Handles` キーワードでサポートできない [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベント システムの特定機能が存在するためです。  詳細については、「[Visual Basic と WPF のイベント処理](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)」を参照してください。  
  
<a name="x_Code"></a>   
## x:Code  
 [x:Code](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md) は、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で定義されるディレクティブ要素です。`x:Code` ディレクティブ要素には、インラインのプログラミング コードを含めることができます。  インラインで定義されたコードは、同一ページ上の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] と対話できます。  [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] のインライン コードを次の例に示します。  コードは `x:Code` 要素内に含まれており、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] のコンテンツをエスケープする `<CDATA[`...`]]>` でコードを囲んでいるのは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] プロセッサ \([!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] スキーマまたは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] スキーマを解釈\) がこのコンテンツをリテラルに [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] として解釈しないようにする必要があるためです。  
  
 [!code-xml[XAMLOvwSupport#ButtonWithInlineCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## インライン コードの制限  
 インライン コードを使用しないようにするか、限定的に使用することを考慮する必要があります。  アーキテクチャおよびコーディングの原理という点では、マークアップと分離コードを切り離しておくことによって、デザイナーと開発者の役割もはっきりと区別できます。  より技術的なレベルで言えば、インライン コードとして作成するコードは記述が面倒な場合があります。常に [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] に生成された部分クラス内に記述することとなり、既定の XML 名前空間のマッピングしか使用できないためです。  `using` ステートメントを追加できないため、作成する [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 呼び出しの多くを完全に修飾する必要があります。  既定の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] マッピングには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アセンブリ内に存在する [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 名前空間のほとんどが含まれますが、すべての名前空間が含まれるのではありません。他の CLR 名前空間内に含まれる型とメンバーへの呼び出しを完全に修飾することが必要になります。  また、インライン コードでは部分クラス以外を定義することはできません。参照するすべてのユーザー コード エンティティが、生成された部分クラス内のメンバーまたは変数として存在する必要があります。  マクロ、グローバル変数やビルド変数に対する `#ifdef` など、言語固有のその他のプログラミング機能も使用できません。  詳細については、「[x:Code 組み込み XAML 型](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)」を参照してください。  
  
## 参照  
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [x:Code 組み込み XAML 型](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)   
 [WPF アプリケーションのビルド](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)   
 [XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)