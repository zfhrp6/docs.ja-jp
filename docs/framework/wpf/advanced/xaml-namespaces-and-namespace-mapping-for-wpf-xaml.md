---
title: "XAML 名前空間および WPF XAML の名前空間の割り当て"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom classes [WPF], mapping namespaces to
- XAML [WPF], namespaces
- namespace mapping [WPF]
- assemblies [WPF], mapping namespaces to
- mapping namespaces [WPF]
- XAML [WPF], namespace mapping
- classes [WPF], mapping namespaces to
- namespaces [WPF]
ms.assetid: 5c0854e3-7470-435d-9fe2-93eec9d3634e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2798659d3b53cb32af8e5976d4fee69780266633
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>XAML 名前空間および WPF XAML の名前空間の割り当て
さらに、このトピックでは、存在と WPF XAML ファイルのルート タグにある多くの場合、2 つの XAML 名前空間のマッピングの目的について説明します。 独自のコード内や個別のアセンブリ内で定義されている要素を使用するためのようなマッピングを生成する方法についても説明します。  
  
  
## <a name="what-is-a-xaml-namespace"></a>XAML Namespace とは何ですか。  
 XAML 名前空間は、実際には、XML 名前空間の概念の拡張です。 XAML 名前空間を指定するための手法を使用して、XML 名前空間の構文、Uri を使用して、同じのマークアップのソースから複数の名前空間を参照する手段を提供するプレフィックスを使用して、名前空間の識別子としての規約に依存して、。 XML 名前空間の XAML 定義に追加される主要な概念は XAML 名前空間が両方の一意性のスコープ マークアップの使用を意味し、マークアップのエンティティが可能性のある特定の CLR 名前空間によってバックアップされ参照方法にも影響アセンブリ。 後者の考慮事項は、XAML スキーマ コンテキストの概念の影響も受けます。 XAML 名前空間での WPF の連携のため、こともできる一般に既定の XAML 名前空間、言語の XAML 名前空間、および、さらに XAML 名前空間として特定のバッキング CLR に直接、XAML マークアップでマップされている面での XAML 名前空間の名前空間と参照先アセンブリ。  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## <a name="the-wpf-and-xaml-namespace-declarations"></a>WPF および XAML Namespace 宣言  
 多くの XAML ファイルのルート タグである名前空間宣言内では、2 つの XML 名前空間宣言が通常表示されます。 最初の宣言では、マップ全体の WPF クライアント/既定値としてフレームワークの XAML 名前空間。  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 2 番目の宣言 (通常) にマップすること、別の XAML 名前空間をマップする、`x:`プレフィックス。  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 これらの宣言の間のリレーションシップは、`x:`プレフィックスのマッピングは、XAML 言語の定義の一部である組み込みをサポートしていると[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]言語としての XAML を使用しのボキャブラリを定義する 1 つの実装は、そのXAML のオブジェクト。 あるため、WPF ボキャブラリの使用法が XAML の組み込みの使用方法よりもはるかに一般的、WPF ボキャブラリは、既定値としてマップされます。  
  
 `x:`プレフィックス規約のプロジェクト テンプレートの後に、XAML 言語の組み込みサポートをマッピングするサンプル コード、および言語のドキュメントの機能[!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]します。 XAML 名前空間では、基本的な WPF アプリケーションにも必要なは一般的に使用される多くの機能を定義します。 たとえば、分離コードを部分クラスを使用して XAML ファイルを結合するのに名前を付けてとそのクラス、`x:Class`関連する XAML ファイルのルート要素の属性です。 または、キー付きのリソースには、アクセスする XAML ページで定義されているいずれかの要素、`x:Key`属性が「対象の要素に設定します。 これらおよびその他の XAML の詳細については「 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)または[XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)です。  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## <a name="mapping-to-custom-classes-and-assemblies"></a>カスタム クラスやアセンブリへのマッピング  
 XML 名前空間をマップするには、一連の内のトークンを使用してアセンブリを`xmlns`プレフィックス宣言、プレフィックスを標準的な WPF と XAML 組み込み XAML 名前空間をマップする方法に似ています。  
  
 構文には、次の名前のトークンと次の値。  
  
 `clr-namespace:`CLR 名前空間は要素として公開するパブリック型を格納するアセンブリ内で宣言されています。  
  
 `assembly=`参照先の一部またはすべてを含むアセンブリ[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]名前空間。 この値は、パスではなく、アセンブリの名前だけでは通常、(.dll または .exe) など、拡張機能は含まれません。 マップしようとして XAML を含むプロジェクト ファイル内のプロジェクト参照としては、そのアセンブリへのパスを確立する必要があります。 バージョン管理とを厳密な名前の署名を反映するために、`assembly`値で定義されている文字列であることができます<xref:System.Reflection.AssemblyName>、単純な文字列名ではなくです。  
  
 文字を分離することに注意してください、`clr-namespace`値からトークンがありますが、コロン (:) 文字の分離、`assembly`値からトークンが等号 (=)。 これら 2 つのトークンの間で使用する文字は、セミコロンです。 またの空白任意の場所に含めない宣言します。  
  
### <a name="a-basic-custom-mapping-example"></a>基本的なカスタム マッピング例  
 次のコードでは、サンプルのカスタム クラスを定義します。  
  
```csharp  
namespace SDKSample {  
    public class ExampleClass : ContentControl {  
        public ExampleClass() {  
        ...  
        }  
    }  
}  
```  
  
```vb  
Namespace SDKSample  
    Public Class ExampleClass  
        Inherits ContentControl  
         ...  
        Public Sub New()  
        End Sub  
    End Class  
End Namespace  
```  
  
 その後、このカスタム クラスは、プロジェクトの設定 (非表示) と呼ばれる、ライブラリにコンパイル`SDKSampleLibrary`です。  
  
 このカスタム クラスを参照するようにする必要がありますは、現在のプロジェクトへの参照として含める Visual Studio のソリューション エクスプ ローラーの UI を使用します。  
  
 これで、クラス、およびプロジェクトの設定への参照を含むライブラリがある場合は、XAML のルート要素の一部として次のプレフィックスのマッピングを追加できます。  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 すべて同時に言うと、ルート タグに、一般的な既定値と共にカスタム マッピングおよび x: マッピングが含まれていますし、プレフィックス付きの参照を使用してインスタンス化する XAML を次に示します`ExampleClass`その UI で。  
  
```xaml  
<Page x:Class="WPFApplication1.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"   
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary">  
  ...  
  <custom:ExampleClass/>  
...  
</Page>  
```  
  
### <a name="mapping-to-current-assemblies"></a>現在のアセンブリへのマッピング  
 `assembly`場合は省略可能、`clr-namespace`参照先は、カスタム クラスを参照しているアプリケーション コードと同じアセンブリ内で定義されています。 この場合の同等の構文を指定するか、 `assembly=`、なし文字列トークンを等号の後にします。  
  
 カスタム クラスは、同じアセンブリで定義されている場合は、ページのルート要素として使用できません。 部分クラスが割り当てる必要はありません。アプリケーションが必要となる xaml 要素として参照する場合にマップするページの部分クラスではないクラスのみです。  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>アセンブリ内の XML 名前空間への CLR 名前空間のマッピング  
 WPF では、単一の XAML 名前空間に複数の CLR 名前空間をマップするために、XAML プロセッサによって使用される CLR 属性を定義します。 この属性は、<xref:System.Windows.Markup.XmlnsDefinitionAttribute>アセンブリを生成するソース コードにアセンブリ レベルで配置されます。 WPF アセンブリのソース コードでは、この属性を使用して、、さまざまな一般的な名前空間をマップ<xref:System.Windows>と<xref:System.Windows.Controls>を[!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]名前空間。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 2 つのパラメーター: XML と XAML 名前空間の名前と CLR 名前空間の名前。 1 つ以上<xref:System.Windows.Markup.XmlnsDefinitionAttribute>同じ XML 名前空間に複数の CLR 名前空間をマップする存在できます。 マップされると、それらの名前空間のメンバーも参照できます完全修飾せず、適切な提供することによって必要な場合は`using`部分クラスの分離コード ページ内のステートメント。 詳細については、「<xref:System.Windows.Markup.XmlnsDefinitionAttribute>」を参照してください。  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>デザイナーの名前空間と XAML テンプレートから他のプレフィックス  
 XAML の WPF の開発環境やデザイン ツールを使用している、する可能性がありますがわかりますがある他の定義済みの XAML 名前空間プレフィックスの XAML マークアップで/です。  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]通常、プレフィックスにマップされるデザイナー名前空間を使用して`d:`です。 WPF のプロジェクト テンプレートをより新しい場合があります、XAML との間のやり取りをサポートするためにこの XAML 名前空間をマップして事前[!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]およびその他のデザイン環境です。 この設計の XAML 名前空間は、ラウンドト リップ、デザイナーで XAML ベースの UI の中にデザインの状態を永続化に使用されます。 使用機能のように`d:IsDataSource`デザイナーでデータ ソースのランタイムを有効にします。  
  
 マップされている別のプレフィックスが表示されて`mc:`です。 `mc:`マークアップ互換性のためと、必ずしも XAML に固有ではないマークアップ互換性パターンを活用することができます。 ある程度はマークアップ互換性フレームワーク間またはその他の境界、補助的な実装の間で XAML を交換する機能を使用することができます XAML スキーマ コンテキスト間で作業デザイナーでは、制限付きのモードの互換性を提供され、します。 マークアップ互換性概念と WPF に関連付ける方法の詳細については、次を参照してください[マークアップの互換性 (mc:)。言語機能](../../../../docs/framework/wpf/advanced/markup-compatibility-mc-language-features.md)します。  
  
## <a name="wpf-and-assembly-loading"></a>WPF およびアセンブリの読み込み  
 WPF の XAML スキーマ コンテキスト 'æ˜aœg' の CLR で定義された概念を順番に使用して、WPF アプリケーション モデル、<xref:System.AppDomain>です。 次の順序は、XAML スキーマ コンテキストがアセンブリを読み込むかの WPF の使用状況に基づいて実行時またはデザイン時に、型を検出する方法をどのように解釈する方法について説明します<xref:System.AppDomain>およびその他の要因です。  
  
1.  反復処理する、<xref:System.AppDomain>名前のすべての側面に一致する読み込み済みアセンブリを探して、読み込まれたアセンブリを最も最近から開始します。  
  
2.  名前修飾する場合は、呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>修飾名にします。  
  
3.  短い名前と修飾名の公開キー トークンは、マークアップから読み込まれたアセンブリに一致すると、そのアセンブリを返します。  
  
4.  短い名前と公開キー トークンを使用して呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>です。  
  
5.  名前が修飾されていない場合は、呼び出す<xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>です。  
  
 Loose XAML は、手順 3; を使用しません読み込まれたアセンブリが存在しません。  
  
 WPF (XamlBuildTask を経由して生成される) にコンパイルされた XAML がから既に読み込まれているアセンブリを使用していない<xref:System.AppDomain>(ステップ 1)。 また、名前する必要がありますしない XamlBuildTask 出力から修飾されていないため、手順 5 が適用されません。  
  
 BAML も含めることはできませんの非修飾アセンブリ名が、コンパイル済みの BAML (PresentationBuildTask 経由で生成) はすべての手順を使用します。  
  
## <a name="see-also"></a>関連項目  
 [XML 名前空間を理解します。](http://go.microsoft.com/fwlink/?LinkId=98069)  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
