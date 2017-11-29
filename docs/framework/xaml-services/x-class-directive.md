---
title: "x:Class ディレクティブ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:Class
- xClass
- Class
helpviewer_keywords:
- Class attribute in XAML [XAML Services]
- XAML [XAML Services], x:Class attribute
- x:Class attribute [XAML Services]
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 1828ef3614cc1f3a81d8aeff62c15ed5accfe380
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xclass-directive"></a>x:Class ディレクティブ
部分クラスのマークアップと分離コードの間で結合する XAML マークアップのコンパイルを構成します。 コードの部分クラスが個別のコード ファイル内で定義されている、[!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]言語、マークアップの部分クラスは、通常、XAML のコンパイル時にコード生成によって作成されします。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`namespace`|省略可能です。 指定します、[!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)]で識別される部分クラスを含む名前空間`classname`です。 場合`namespace`を指定すると、ドット (.) で区切られます`namespace`と`classname`です。 「解説」を参照してください。|  
|`classname`|必須です。 指定します、[!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)]読み込まれた XAML およびその XAML の分離コードで接続する部分クラスの名前。|  
  
## <a name="dependencies"></a>依存関係  
 `x:Class`XAML の運用環境のルート要素でのみ指定できます。 `x:Class`XAML の運用環境である親を持つ任意のオブジェクトで有効です。 詳細については、次を参照してください。 [ \[MS-XAML\]セクション 4.3.1.6](http://go.microsoft.com/fwlink/?LinkId=114525)です。  
  
## <a name="remarks"></a>コメント  
 `namespace`値は、.NET Framework プログラミングで一般的な手法は、名前の階層に関連する名前空間を整理する追加のドットを含めることがあります。 文字列の最後のドットのみ`x:Class`を区切るための値を解釈`namespace`と`classname.`として使用されるクラス`x:Class`入れ子になったクラスにすることはできません。 ドットの意味を決定するため、入れ子になったクラスは許可されません`x:Class`文字列が入れ子になったクラスが許可されている場合は、あいまいです。  
  
 既存のプログラミングを使用するモデル`x:Class`、`x:Class`を分離コードを持たない XAML ページが存在する有効な完全であるという意味では省略可能です。 ただし、その機能は、XAML を使用するフレームワークによって実装されているビルド アクションと対話します。 `x:Class`機能は、XAML で指定されたコンテンツのさまざまな分類が、アプリケーション モデルがあり、ビルド アクションで、対応するロールの影響も受けます。 指定する必要が、XAML では、イベント ハンドラー属性の値またはクラスを定義するには、分離コード クラスにあるカスタムの要素をインスタンス化を宣言する場合、`x:Class`ディレクティブ リファレンス (または[X:subclass](../../../docs/framework/xaml-services/x-subclass-directive.md)) に、分離コードの適切なクラスです。  
  
 値、`x:Class`ディレクティブは、アセンブリ情報がない場合は、クラスの完全修飾名を指定する文字列である必要があります (と同等、 <xref:System.Type.FullName%2A?displayProperty=nameWithType>)。 単純なアプリケーションは、分離コードがそのように (クラス レベルでコードの定義の開始) も構造化された場合、CLR 名前空間情報を省略できます。  
  
 ページまたはアプリケーション定義の分離コード ファイルは、コンパイルされたアプリケーションを作成し、マークアップのコンパイルでは、プロジェクトの一部として含まれているコード ファイル内になければなりません。 CLR クラスの名前規則に従う必要があります。 詳細については、次を参照してください。 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)です。 既定では、分離コード クラスがある必要があります`public`。 ただし、を使用して、異なるアクセス レベルで定義できる、 [X:classmodifier ディレクティブ](../../../docs/framework/xaml-services/x-classmodifier-directive.md)です。  
  
 この解釈、`x:Class`属性にのみ適用されます、CLR ベースの XAML 実装では、特に .NET Framework XAML サービスにします。 CLR には基づいていません、.NET Framework XAML サービスを使用しないその他の XAML 実装には、XAML マークアップを接続し、実行時のコードをバックアップするための解像度が異なる数式を使用できます。 一般的な意味の詳細については`x:Class`を参照してください[ \[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)です。  
  
 アーキテクチャの意味のあるレベルで`x:Class`.NET Framework XAML サービスでは未定義です。 これは、.NET Framework XAML サービスでどの XAML マークアップおよびコードのバックアップを接続するプログラミング モデルが指定されていないためです。 別の使用、`x:Class`ディレクティブが XAML のマークアップと CLR ベースの分離コードを接続する方法を定義するプログラミング モデルまたはアプリケーションのモデルを使用する特定のフレームワークによって実装される可能性があります。 各フレームワークには、ビルド アクションをいくつかの動作またはビルド環境に含める必要がある特定のコンポーネントを有効にすることができます。 フレームワーク内でのビルド アクションは、分離コードに使用される特定の CLR 言語によっても異なります。  
  
## <a name="xclass-in-the-wpf-programming-model"></a>WPF のプログラミング モデルでは、X:class  
 WPF アプリケーションと WPF アプリケーション モデルで`x:Class`を XAML ファイルのルートは、コンパイルしている任意の要素の属性として宣言することができます (と WPF アプリケーション プロジェクトでは、XAML が含まれている`Page`ビルド アクション)、または、「c4 > <xref:System.Windows.Application> コンパイル済みの WPF アプリケーションのアプリケーション定義のルートです。 宣言`x:Class`ページのルートまたはアプリケーションのルート以外の要素またはコンパイルされていない WPF XAML ファイルでは、コンパイル時エラーが発生、[!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]と[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]WPF XAML コンパイラです。 他の側面について`x:Class`WPF での処理を参照してください[分離コードと wpf XAML](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)です。  
  
## <a name="xclass-for-windows-workflow-foundation"></a>Windows Workflow Foundation の x: クラス  
 Windows Workflow foundation `x:Class` XAML で構成されるカスタム アクティビティのクラスの名前または分離コードを含むアクティビティ デザイナーに、XAML ページの部分クラスの名前を指定します。  
  
## <a name="silverlight-usage-notes"></a>Silverlight の使用上の注意  
 Silverlight 用の `x:Class` に関しては、別途ドキュメントが用意されています。 詳細については、次を参照してください[XAML Namespace (x:)。言語機能 (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081)です。  
  
## <a name="see-also"></a>関連項目  
 [x:Subclass ディレクティブ](../../../docs/framework/xaml-services/x-subclass-directive.md)  
 [WPF における XAML とカスタム クラス](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [x:ClassModifier ディレクティブ](../../../docs/framework/xaml-services/x-classmodifier-directive.md)  
 [WPF から System.Xaml に移行した型](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
