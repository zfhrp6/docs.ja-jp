---
title: XAML での空白の処理
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], whitespace processing
- whitespace processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 9f7d7ca900955b8899322533f9d69338042d88ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565546"
---
# <a name="whitespace-processing-in-xaml"></a>XAML での空白の処理
XAML の言語規則では、空白の意味は [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] プロセッサの実装によって処理する必要があると定められています。 ここでは、それらの XAML 言語規則について説明します。 また、XAML プロセッサの [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 実装およびシリアル化用の XAML ライターで定義されている追加の空白処理についても説明します。  
  
<a name="whitespace_definition"></a>   
## <a name="whitespace-definition"></a>空白の定義  
 [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]と調和して、 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] の空白文字は、スペース、改行、およびタブです。これらは、それぞれ [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] 値の 0020、000A、および 0009 に対応します。  
  
<a name="whitespace_normalization"></a>   
## <a name="whitespace-normalization"></a>空白の正規化  
 既定では、 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] プロセッサで [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ファイルを処理する際に、次に示す空白の正規化が行われます。  
  
1.  東アジア言語の文字間の改行文字が削除されます。 この用語の定義については、後の「東アジア言語の文字」を参照してください。  
  
2.  すべての空白文字 (スペース、改行、タブ) は、スペースに変換されます。  
  
3.  連続した複数のスペースはすべて削除され、1 つのスペースに置換されます。  
  
4.  開始タグの直後にあるスペースは削除されます。  
  
5.  終了タグの直前にあるスペースは削除されます。  
  
 "既定" とは、 [xml:space](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md) 属性の既定値で表される状態に対応します。  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="whitespace-in-inner-text-and-string-primitives"></a>内部テキスト内の空白、および文字列プリミティブ  
 前の正規化規則は、XAML 要素内で検出された内部テキストに適用されます。 正規化の後、XAML プロセッサは、次のようにして、すべての内部テキストを適切な型に変換します。  
  
-   プロパティの型がコレクションでなく、直接的に <xref:System.Object> 型でもない場合、XAML プロセッサはその型の型コンバーターを使用して、その型への変換を試みます。 その際、変換に失敗すると、コンパイル時のエラーが発生します。  
  
-   プロパティの型がコレクションで、内部テキストが連続している (間に要素タグがない) 場合、その内部テキストは単一の <xref:System.String>として解析されます。 そのコレクション型が <xref:System.String>を受け入れない場合にも、コンパイル時のエラーが発生します。  
  
-   プロパティの型が <xref:System.Object>である場合、その内部テキストは単一の <xref:System.String>として解析されます。 その内部テキストの中に要素タグが含まれている場合には、コンパイル時のエラーが発生します。これは、 <xref:System.Object> 型は単一のオブジェクト (<xref:System.String> またはそれ以外) であることを意味しているためです。  
  
-   プロパティの型がコレクションであり、内部テキストが連続していないことがあります。この場合、最初の部分文字列は <xref:System.String> に変換されてコレクション項目として追加されます。中間にある要素はコレクション項目として追加され、この要素の後に続く部分文字列 (存在する場合) は 3 番目の <xref:System.String> 項目としてコレクションに追加されます。  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-whitespace"></a>空白の保持  
 ソース [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] で空白を保持し、 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] プロセッサによる空白の正規化の影響を受けずに最終的に表示されるようにするには、いくつかの手法があります。  
  
 **xml:space ="preserve"**: 空白を保持する必要がある要素のレベルで、この属性を指定します。 この場合、要素を視覚的にわかりやすい入れ子として "美しく表示する" ためにコード編集アプリケーションによって追加されたスペースも含めて、すべての空白が保持されます。 ただし、これらのスペースが表示されるかどうかは、スペースを含んでいる要素のコンテンツ モデルによって決まります。 オブジェクト モデルの大多数では、属性の設定にかかわらず、空白に意味があるとは見なされないため、 `xml:space="preserve"` をルート レベルで指定しないでください。 グローバルに `xml:space` を設定すると、一部の実装で XAML 処理 (特にシリアル化) のパフォーマンスに影響することがあります。 この属性は、文字列内の空白を表示する必要のある要素のレベル、または空白が意味を持つコレクションである要素のレベルでのみ設定することをお勧めします。  
  
 **エンティティおよび改行しないスペース**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] では、テキスト オブジェクト モデル内に任意の [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] エンティティを配置できます。 非区切りスペースなどの専用のエンティティを使用できます ((& a)\#160; utf-8 エンコードで)。 また、改行しないスペース文字をサポートするリッチ テキスト コントロールを使用することもできます。 インデントなどのレイアウト特性をシミュレートするためにエンティティを使用する場合には、エンティティの実行時出力が、一般的なレイアウト システムにおけるインデントの生成機能を使用した場合よりも多くの要因 (パネルや余白の適切な使用など) に基づいて変化するため、注意が必要です。 たとえば、エンティティはフォントにマッピングされ、ユーザーのフォント選択に応じてサイズが変わる可能性があります。  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>東アジア言語の文字  
 "東アジア言語の文字" は、U+20000 ～ U+2FFFD および U+30000 ～ U+3FFFD の範囲の [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] 文字のセットとして定義されています。 このサブセットは、「CJK 表意文字」と呼ばれることもあります。 詳細については、「[http://www.unicode.org](http://www.unicode.org/)」を参照してください。  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="whitespace-and-text-content-models"></a>空白とテキスト コンテンツ モデル  
 実際には、空白の保持は、すべてのコンテンツ モデルのサブセットに関してのみ問題になります。 このサブセットに含まれるのは、ある種のシングルトン <xref:System.String> 型、専用の <xref:System.String> コレクション、または <xref:System.String> や <xref:System.Collections.IList> コレクションでの <xref:System.Collections.Generic.ICollection%601> と他の型の組み合わせをとることのできるコンテンツ モデルです。  
  
### <a name="whitespace-and-text-content-models-in-wpf"></a>WPF での空白とテキスト コンテンツ モデル  
 一例として、このセクションの残りの部分では、WPF によって定義されている特定の型について説明します。 ここで説明する空白の処理機能は、一般に .NET Framework XAML サービスと WPF の両方に当てはまります。 これらの動作を実際に見るには、何かの WPF XAML マークアップを使用し、オブジェクト グラフでその結果を確認し、再度マークアップにシリアル化してください。  
  
 文字列をとることのできるコンテンツ モデルの場合でも、そのコンテンツ モデル内での既定の動作では、残っているすべての空白は、意味のある空白としては扱われません。 たとえば、 <xref:System.Windows.Controls.ListBox> は <xref:System.Collections.IList>を使用しますが、空白 (各 <xref:System.Windows.Controls.ListBoxItem>の間の改行など) は保持も表示もされません。 改行文字を <xref:System.Windows.Controls.ListBoxItem> 項目の文字列間の区切り記号として使用しても、まったく機能しません。改行文字で区切られた文字列は、1 つの文字列および 1 つの項目として扱われます。  
  
 空白を意味のあるものとして扱うコレクションは、通常、フロー ドキュメント モデルの一部分です。 空白を保持する動作をサポートする主なコレクションには、 <xref:System.Windows.Documents.InlineCollection>があります。 このコレクション クラスは <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>を使用して宣言します。この属性が検出されると、 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] プロセッサはコレクション内の空白を意味のあるものとして扱います。 `xml:space="preserve"` と、 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> を指定したコレクション内の空白の組み合わせでは、すべての空白は保持され、表示されます。 `xml:space="default"` と、 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 内の空白の組み合わせでは、前に説明した空白の初期正規化が行われます。この場合、一定の位置に 1 つのスペースが残され、そのスペースは保持され、表示されます。 どちらの動作が望ましいかは、開発者の意図によって異なります。そのため、 `xml:space` は、必要な動作が有効となるように、選択的に使用する必要があります。  
  
 また、フロー ドキュメント モデルで改行を意味する特定のインライン要素では、空白が意味を持つコレクションでも、余分なスペースを挿入しないように注意する必要があります。 たとえば、<xref:System.Windows.Documents.LineBreak>要素と同じ目的には、 \<BR/> にタグを付ける[!INCLUDE[TLA2#tla_html](../../../includes/tla2sharptla-html-md.md)]、マークアップでは、読みやすくするため、通常、<xref:System.Windows.Documents.LineBreak>はで改行を入れて後続のテキストから区切られます。 その改行は、正規化されて後続の行の先頭のスペースになってはなりません。 その動作を有効にするために、 <xref:System.Windows.Documents.LineBreak> 要素のクラス定義は <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>を適用します。これは、 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] を囲む空白を常にトリミングするという意味に <xref:System.Windows.Documents.LineBreak> プロセッサによって解釈されます。  
  
## <a name="see-also"></a>関連項目  
 [XAML の概要 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [XML 文字エンティティと XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)  
 [XAML における xml:space の処理](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md)
