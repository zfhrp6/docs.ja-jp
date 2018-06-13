---
title: x:Subclass ディレクティブ
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: b04982ff0b7685b4e4b809255e3bbe541b42cb9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566419"
---
# <a name="xsubclass-directive"></a>x:Subclass ディレクティブ
XAML マークアップのコンパイルの動作を変更してとき`x:Class`も用意されています。 基になっている部分クラスを作成する代わりに`x:Class`、提供されている`x:Class`、中間クラスとして作成された基になる、指定された派生クラスを想定し、`x:Class`です。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`namespace`|任意。 含む CLR 名前空間が指定`classname`です。 場合`namespace`を指定すると、ドット (.) で区切られます`namespace`と`classname`です。|  
|`classname`|必須。 読み込まれた XAML およびその XAML の分離コードで接続する部分クラスの CLR 名を指定します。 「解説」を参照してください。|  
|`subclassNamespace`|任意。 異なっていてもかまいません`namespace`他の各名前空間を解決できない場合。 含む CLR 名前空間が指定`subclassName`です。 場合`subclassName`を指定すると、ドット (.) で区切られます`subclassNamespace`と`subclassName`です。|  
|`subclassName`|必須。 サブクラスの CLR 名を指定します。|  
  
## <a name="dependencies"></a>依存関係  
 [X:class ディレクティブ](../../../docs/framework/xaml-services/x-class-directive.md)も、同じオブジェクトに提供される必要があり、そのオブジェクトは XAML の運用環境のルート要素である必要があります。  
  
## <a name="remarks"></a>コメント  
 `x:Subclass` 使用状況は、主に、部分クラス宣言をサポートしない言語のものです。  
  
 として使用されるクラス、`x:Subclass`入れ子になったクラスにすることはできませんと`x:Subclass`「の依存関係」セクションで説明したように、ルート オブジェクトを参照する必要があります。  
  
 それ以外の場合の概念の意味`x:Subclass`.NET Framework XAML サービス実装では未定義です。 これは、.NET Framework XAML サービスの動作にどの XAML マークアップおよびコードのバックアップを接続、全体的なプログラミング モデルが指定されていないためです。 さらに概念の実装に関連する`x:Class`と`x:Subclass`プログラミング モデルまたはアプリケーションのモデルを使用して、XAML マークアップ、コンパイルされたマークアップ、および CLR ベースの分離コードを接続する方法を定義する特定のフレームワークによって実行されます。 各フレームワークには、いくつかの動作、またはビルド環境に含める必要がある特定のコンポーネントを有効にする、独自のビルド アクションがあります。 フレームワーク内でビルド アクションも異なります分離コードに使用される特定の CLR 言語。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 `x:Subclass` ページのルートでまたはを指定できます、<xref:System.Windows.Application>を既に持っているアプリケーション定義のルート`x:Class`です。 宣言`x:Subclass`ページまたはアプリケーションのルート、または、no を指定する以外の任意の要素で`x:Class`が存在し、コンパイル時エラーが発生します。  
  
 その作業を正しく派生を作成するクラス、`x:Subclass`シナリオは非常に複雑です。 中間ファイル (プロジェクトの obj フォルダーの名前には、.xaml ファイル名と、マークアップ コンパイルによって生成される .g ファイル) を確認する必要があります。 これらの中間ファイルは、コンパイルされたアプリケーションに参加している、部分クラスで特定のプログラミング構成要素の起点を特定するのに役立ちます。  
  
 派生クラスでイベント ハンドラーがある必要があります`internal override`(`Friend Overrides` Microsoft Visual Basic で) コンパイル時に中間クラスで作成されると、ハンドラーのスタブをオーバーライドするためにします。 それ以外の場合、派生クラスの実装には、(シャドウ)、中間クラスの実装が非表示にし、中間クラスのハンドラーは呼び出されません。  
  
 両方を定義するときに`x:Class`と`x:Subclass`、によって参照されているクラスのすべての実装を提供する必要はありません`x:Class`です。 のみを使用して名前を指定する必要があります、`x:Class`属性のコンパイラに中間ファイル (コンパイラ選択しません、既定の名前でも) で作成するクラスについてガイダンスを持つようにします。 付与できる、`x:Class`クラスの実装です。 ただし、これは、典型的なシナリオの両方を使用して`x:Class`と`x:Subclass`です。  
  
## <a name="see-also"></a>関連項目  
 [x:Class ディレクティブ](../../../docs/framework/xaml-services/x-class-directive.md)  
 [WPF における XAML とカスタム クラス](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
