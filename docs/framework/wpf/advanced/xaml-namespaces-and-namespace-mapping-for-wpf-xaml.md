---
title: "XAML 名前空間および WPF XAML の名前空間の割り当て | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アセンブリ, 割り当て (名前空間を)"
  - "クラス, 割り当て (名前空間を)"
  - "カスタム クラス, 割り当て (名前空間を)"
  - "割り当て (名前空間を)"
  - "名前空間の割り当て"
  - "名前空間"
  - "XAML, 名前空間の割り当て"
  - "XAML, 名前空間"
ms.assetid: 5c0854e3-7470-435d-9fe2-93eec9d3634e
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# XAML 名前空間および WPF XAML の名前空間の割り当て
ここでは、WPF XAML ファイルのルート タグに含まれることがよくある 2 つの XAML 名前空間の割り当ての存在と目的について説明します。  また、独自のコードや個別のアセンブリ内で定義されている要素を使用するために同様の割り当てを生成する方法についても説明します。  
  
   
  
## XAML 名前空間とは  
 XAML 名前空間は、XML 名前空間の概念を拡張したものです。  XAML 名前空間を指定する技法は、XML 名前空間の構文、名前空間識別子として URI を使用する規則、同じマークアップ ソースの複数の名前空間を参照する手段を提供するためのプレフィックスの使用などに依存します。  XAML 定義に追加された XML 名前空間の主な概念は、XAML 名前空間が、マークアップの使用に関する一意性の範囲を示すだけでなく、マークアップ エンティティが特定の CLR 名前空間と参照アセンブリによってどのようにサポートされる可能性があるかに影響を与えるということです。  後者の考慮事項は、XAML スキーマ コンテキストの概念の影響も受けます。  WPF が XAML 名前空間で機能する方法の目的を除けば、一般に、XAML 名前空間は、既定の XAML 名前空間、XAML 言語の名前空間、および XAML マークアップによって直接特定のバッキング CLR 名前空間と参照アセンブリに割り当てられるその他の XAML 名前空間として考えることができます。  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## WPF および XAML 名前空間宣言  
 多くの XAML ファイルのルート タグの名前空間宣言内には、通常 2 つの XML 名前空間宣言が含まれています。  最初の宣言では、次のように WPF クライアント\/フレームワークの XAML 名前空間全体を既定として割り当てます。  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 2 番目の宣言は、個別の XAML 名前空間を割り当てます \(通常は、`x:` プレフィックスに割り当てます\)。  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 これらの宣言の関係は、`x:` プレフィックスの割り当てによって XAML 言語定義の一部である組み込みをサポートし、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は XAML を言語として使用する 1 つの実装として、そのオブジェクトの XAML での語彙を定義するという位置付けになります。  WPF 語彙の使用は XAML 組み込みの使用に比べてはるかに一般的であるため、WPF 語彙が既定として割り当てられます。  
  
 XAML 言語組み込みのサポートを `x:` プレフィックスに割り当てる規則は、プロジェクト テンプレート、サンプル コード、およびこの [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 内の言語機能のドキュメントに適用されます。  XAML 名前空間は、基本的な WPF アプリケーションにも必要な一般的に使用されるさまざまな機能を定義します。  たとえば、部分クラスを使用して分離コードを XAML ファイルに結合するには、そのクラスの名前を、関連する XAML ファイルのルート要素の `x:Class` 属性として指定する必要があります。  または、アクセスする XAML ページでキーを持つリソースとして定義されている要素では、`x:Key` 属性を設定する必要があります。  XAML のこれらの面およびその他の面の詳細については、「[XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)」または「[XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)」を参照してください。  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## カスタム クラスおよびアセンブリへの割り当て  
 標準の WPF 名前空間と XAML 組み込み XAML 名前空間をプレフィックスに割り当てる場合と同じ方法で、`xmlns` プレフィックス宣言内の一連のトークンを使用して XML 名前空間をアセンブリに割り当てることができます。  
  
 構文には、次の名前のトークンおよび値を指定できます。  
  
 `clr-namespace:` 要素として公開するパブリック型を含むアセンブリ内で宣言される CLR 名前空間。  
  
 `assembly=` : 参照される [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 名前空間の一部またはすべてを含むアセンブリ。  通常、この値にはパスではなくアセンブリの名前のみを設定し、拡張子 \(.dll、.exe など\) は含めません。  そのアセンブリへのパスは、割り当てる XAML が格納されたプロジェクト ファイルのプロジェクト参照として確立される必要があります。  バージョン管理および厳密な名前の署名を組み込むために、`assembly` 値を、単純な文字列名ではなく <xref:System.Reflection.AssemblyName> によって定義されている文字列にすることもできます。  
  
 `clr-namespace` トークンとその値を区切る文字はコロン \(:\) ですが、`assembly` トークンとその値を区切る文字は等号 \(\=\) であることに注意してください。  これら 2 つのトークン間で使用する文字は、セミコロンです。  さらに、宣言内で空白は使用しないでください。  
  
### 基本的なカスタム マッピングの例  
 次のコードは、サンプルのカスタム クラスを定義しています。  
  
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
  
 次に、このカスタム クラスをライブラリにコンパイルすると、プロジェクト設定 \(この例には示されていません\) は `SDKSampleLibrary` という名前になります。  
  
 このカスタム クラスを参照するには、現在のプロジェクトの参照としてこれを含める必要があります。通常、これを行うには Visual Studio のソリューション エクスプローラー UI を使用します。  
  
 これで、クラスが含まれたライブラリおよびプロジェクト設定内のそれへの参照が作成され、XAML のルート要素の一部として次のプレフィックス割り当てを追加できます。  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 すべてをまとめると、ルート タグの通常の既定の割り当ておよび x: 割り当てに加え、カスタム マッピングが含まれた次の XAML になります。この後、プレフィックス付きの参照を使用してその UI の `ExampleClass` をインスタンス化します。  
  
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
  
### 現在のアセンブリへの割り当て  
 `assembly` は、参照される `clr-namespace` がカスタム クラスを参照しているアプリケーション コードと同じアセンブリ内で定義されている場合は省略できます。  または、等号の後に文字列トークンを設定せずに `assembly=` を指定すると、前述の場合と等価の構文になります。  
  
 同じアセンブリで定義されているカスタム クラスをページのルート要素として使用することはできません。  部分クラスを割り当てる必要はありません。XAML でクラスを要素として参照する場合、アプリケーションのページの部分クラスではないクラスのみを割り当てる必要があります。  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## アセンブリ内の XML 名前空間への CLR 名前空間の割り当て  
 WPF は、複数の CLR 名前空間を単一の XAML 名前空間に割り当てるために、XAML プロセッサが使用する CLR 属性を定義します。  この属性 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> は、アセンブリを生成するソース コードのアセンブリ レベルに配置されます。  WPF アセンブリ ソース コードでは、この属性を使用して、<xref:System.Windows> や <xref:System.Windows.Controls> などの一般的な各種名前空間が [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 名前空間に割り当てられます。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> には、XML\/XAML 名前空間名および CLR 名前空間名の 2 つのパラメーターがあります。  複数の <xref:System.Windows.Markup.XmlnsDefinitionAttribute> を使用して、複数の CLR 名前空間を同じ XML 名前空間に割り当てることができます。  必要に応じて、部分クラスの分離コード ページで適切な `using` ステートメントを指定することによって、割り当てられた名前空間のメンバーを完全修飾せずに参照することもできます。  詳細については、「<xref:System.Windows.Markup.XmlnsDefinitionAttribute>」を参照してください。  
  
## デザイナー名前空間および XAML テンプレートの他のプレフィックス  
 WPF XAML 用の開発環境やデザイン ツールを使用して作業している場合、XAML マークアップ内に他の定義済みの XAML 名前空間やプレフィックスが存在することがわかります。  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] では、通常 `d:` というプレフィックスに割り当てられるデザイナー名前空間が使用されます。  WPF 用の最近のプロジェクト テンプレートでは、[!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] と他のデザイン環境間で XAML を交換できるように、この XAML 名前空間が事前に割り当てられています。  このデザインの XAML 名前空間は、デザイナーで XAML ベースの UI をラウンド トリップするときにデザイン状態を永続化するために使用されます。  また、デザイナーでランタイム データ ソースを有効にする `d:IsDataSource` などの機能にも使用されます。  
  
 割り当てることがある別のプレフィックスは、`mc:` です。  `mc:` はマークアップ互換性のために用意され、必ずしも XAML 固有ではないマークアップ互換性パターンを使用しています。  マークアップ互換性機能は、複数のフレームワーク間で、またはバッキング実装の他の境界にまたがって、XAML を交換するために使用したり、複数の XAML スキーマ コンテキスト間で機能したり、デザイナーの制限されたモードに互換性を提供したりすることができます。  マークアップ互換性の概念、およびその概念が WPF にどのように関係するかについては、「[マークアップの互換性 \(mc:\) 言語機能](../../../../docs/framework/wpf/advanced/markup-compatibility-mc-language-features.md)」を参照してください。  
  
## WPF およびアセンブリの読み込み  
 WPF の XAML スキーマ コンテキストは WPF アプリケーション モデルと統合されて、CLR で定義された <xref:System.AppDomain> の概念を使用します。  次の手順は、XAML スキーマ コンテキストが、WPF における <xref:System.AppDomain> およびその他の要素の使用に基づいて、実行時またはデザイン時にどのようにアセンブリの読み込みまたは型の検索を行うかについて解釈する方法を示しています。  
  
1.  <xref:System.AppDomain> を反復処理して、名前のすべての要素が一致する読み込み済みのアセンブリを、最も新しく読み込まれたアセンブリから順に検索します。  
  
2.  名前が修飾されている場合は、修飾名で <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName> を呼び出します。  
  
3.  短い名前に修飾名の公開キー トークンを加えたものが、マークアップの読み込み元であるアセンブリに一致する場合は、そのアセンブリを返します。  
  
4.  短い名前と公開キー トークンを使用して、<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName> を呼び出します。  
  
5.  名前が修飾されていない場合は、<xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName> を呼び出します。  
  
 Loose XAML の場合は、読み込み元のアセンブリがないので手順 3. は適用されません。  
  
 WPF 向けにコンパイルされた XAML \(XamlBuildTask を使用して生成\) の場合は、<xref:System.AppDomain> からの読み込み済みアセンブリ \(手順 1.\) を使用しません。  また、XamlBuildTask 出力からの名前が修飾されないことはありません。したがって、手順 5. は適用されません。  
  
 BAML では修飾なしのアセンブリ名は含まれませんが、コンパイルされた BAML \(PresentationBuildTask を使用して生成\) の場合はすべての手順が適用されます。  
  
## 参照  
 [XML 名前空間入門](http://go.microsoft.com/fwlink/?LinkId=98069)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)