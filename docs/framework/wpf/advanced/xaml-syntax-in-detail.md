---
title: "XAML 構文の詳細"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [WPF], namespaces
- XAML [WPF], parsing of attributes
- parsing of attributes [WPF]
- XAML [WPF], markup extensions
- attached properties [WPF]
- tag syntax [XAML]
- markup extensions [WPF]
- XAML [WPF], object element syntax
- XAML [WPF], syntax terminology
- attached events [WPF]
- lookup semantics [WPF]
- XAML [WPF], attached events
- XAML [WPF], content syntax
- XAML [WPF], lookup semantics
- content syntax [WPF]
- object element syntax [WPF]
- syntax terminology [XAML]
- XAML [WPF], attached properties
- attributes [XAML], parsing
- XAML [WPF], tag syntax
- XAML [WPF], attribute syntax
- property element syntax [WPF]
- terminology [XAML]
- namespaces [WPF], XML
- attribute syntax [XAML]
- XAML [WPF], property element syntax
ms.assetid: 67cce290-ca26-4c41-a797-b68aabc45479
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88e66210fd8066e82a11d07ea0cfeb83808d646c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-syntax-in-detail"></a>XAML 構文の詳細
このトピックでは、XAML 構文の要素の記述に使用する用語を定義します。 これらの条項は、具体的には、XAML や、XAML 言語レベルのサポート、System.Xaml で有効になっている基本的な XAML の概念を使用する他のフレームワークの WPF のドキュメントのどちらも、このドキュメントの残りの部分全体でよく使用されます。 このトピックのトピックで導入された基本的な用語を詳述[XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)です。  
  

  
<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>XAML 言語仕様  
 ここで定義された XAML 構文の用語の定義または、XAML 言語仕様内で参照されてもします。 XAML は、XML に基づく言語は、やに依存してまたは XML の構造的な規則について詳しく説明します。 用語の一部はから共有または XML 言語または XML ドキュメント オブジェクト モデルを記述する場合によく使用する用語に基づきます。  
  
 XAML 言語仕様の詳細については、ダウンロード[ \[MS-XAML\] ](http://go.microsoft.com/fwlink/?LinkId=114525) Microsoft ダウンロード センターからです。  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML と CLR  
 XAML は、マークアップ言語です。 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]により、ランタイムの実行、名によって、黙示、します。 XAML は単独で、CLR ランタイムによって直接使用される一般的な言語のいずれか。 代わりに、XAML の独自の型システムをサポートするいると考えることができます。 WPF によって使用される特定の XAML の解析を行ってシステムは、CLR および CLR 型システムで作成されています。 XAML の型は、wpf XAML が解析される際に、実行時の表現をインスタンス化する CLR 型にマップされます。 このため、このドキュメントの構文のディスカッションの残りの部分は、XAML 言語仕様で同等の構文の説明がない場合でも、CLR 型システムへの参照を含まれます。 (あたり、XAML 言語仕様レベルでは、XAML の型でしたにマップするその他の型システム、CLR であるはありませんが、作成して、別の XAML パーサーの使用が必要となります。)  
  
#### <a name="members-of-types-and-class-inheritance"></a>型のメンバーとクラスの継承  
 プロパティおよびの XAML メンバーとして表示されるときに、そのイベント、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]型が基本型から継承された多くの場合。 たとえば、次の例:`<Button Background="Blue" .../>`です。 <xref:System.Windows.Controls.Control.Background%2A>プロパティは使用されません直ちに宣言されたプロパティで、<xref:System.Windows.Controls.Button>クラス、クラス定義、リフレクション結果、またはドキュメントを確認する場合は。 代わりに、<xref:System.Windows.Controls.Control.Background%2A>ベースから継承された<xref:System.Windows.Controls.Control>クラスです。  
  
 クラスの継承の動作の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 要素は重要な従来の XML マークアップをスキーマによって課される解釈します。 クラスの継承は中間の基本クラスは抽象クラスで特に場合、またはインターフェイスが含まれている場合、複雑になることができます。 これは、1 つがある理由が XAML 要素およびその使用可能属性のセットを正確かつ完全には、スキーマ型を使用して表示するが困難に通常使用される[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]プログラミングでは、DTD または XSD 形式などです。 別の理由がその拡張機能と XAML 言語自体の型マッピングの機能の使用可能な型とメンバーのすべての固定表現の完全性を妨げるものでいます。  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>オブジェクト要素構文  
 *オブジェクトの要素の構文*XML 要素を宣言することによって、CLR クラスまたは構造体をインスタンス化する XAML マークアップの構文を示します。 この構文では、HTML などの他のマークアップ言語の要素の構文に似ています。 オブジェクトの要素の構文が左山かっこで始まる (\<)、クラスまたはインスタンス化されている構造体の型名ですぐにその後にします。 0 個以上のスペース名の後、型、および 0 個以上の属性が宣言することも、オブジェクト要素上のそれぞれの属性名を区切る 1 つ以上のスペースを含む ="value"ペア。 最後は、次のいずれかの必要があります。  
  
-   要素とタグは、右の山かっこ (>) がすぐに続くフォワード スラッシュ (/) で閉じる必要があります。  
  
-   開始タグは、右の山かっこ (>) で完了する必要があります。 他のオブジェクト要素、プロパティ要素、または内部のテキストは、開始タグをに従ってできます。 コンテンツをここで含めることが正確には通常、要素のオブジェクト モデルによって制限されます。 対応するオブジェクトの要素のタグを終了する必要がありますも適切な入れ子でが存在し、その他の開始と終了タグのペアとのバランスをとる。  
  
 .NET によって実装される XAML では、型、プロパティまたはイベント、および XAML 名前空間の CLR 名前空間とアセンブリに属性にオブジェクトの要素をマップするルールのセットがあります。 WPF と .NET Framework では、XAML オブジェクト要素にマップされる[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]で定義されている型参照アセンブリ、およびそれらの型のメンバー、属性にマップします。 XAML での CLR 型を参照するときにもその型の継承されたメンバーへのアクセスがあります。  
  
 たとえば、次の例は、オブジェクト要素の構文の新しいインスタンスをインスタンス化する、<xref:System.Windows.Controls.Button>クラス、およびも指定して、<xref:System.Windows.FrameworkElement.Name%2A>属性とその属性の値。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 次の例は、XAML コンテンツ プロパティの構文を含むオブジェクト要素の構文です。 その内部テキ スト内に含まれる設定に使用される、 <xref:System.Windows.Controls.TextBox> XAML コンテンツ プロパティ、<xref:System.Windows.Controls.TextBox.Text%2A>です。  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>コンテンツ モデル  
 クラスは、構文の観点から XAML オブジェクト要素として、使用法をサポートする場合がありますがその要素はのみが正しく機能アプリケーションやページで、全体的なコンテンツ モデルまたは要素ツリーの適切な位置に配置されている場合。 たとえば、<xref:System.Windows.Controls.MenuItem>通常のみに配置するの子として、<xref:System.Windows.Controls.Primitives.MenuBase>などのクラスを派生<xref:System.Windows.Controls.Menu>です。 コンテンツ コントロールやその他のクラスのページで、「解説」の一部として特定要素モデルが記載されている[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 要素として使用できるクラスです。  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>オブジェクトの要素のプロパティ  
 XAML のプロパティは、さまざまな使用できる構文によって設定されます。 特定のプロパティの構文を使用できますが、に応じて変わります、基になる型システム プロパティの特性は、設定します。  
  
 プロパティの値を設定または追加する機能の特性オブジェクトに、実行時のオブジェクト グラフ内に存在するためです。 オブジェクトの要素から作成されたオブジェクトの初期状態は、既定のコンス トラクターの動作に基づきます。 通常、アプリケーションは、完全に既定のインスタンスの任意のオブジェクト以外に使用されます。  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>属性構文 (プロパティ)  
 属性構文は、既存のオブジェクト要素の属性を宣言することで、プロパティの値を設定する XAML マークアップの構文です。 属性名は、関連するオブジェクトの要素をサポートするクラスのプロパティの CLR メンバー名と一致する必要があります。 属性名には、代入演算子 (=) が続きます。 属性値には、引用符で囲まれた文字列を指定する必要があります。  
  
> [!NOTE]
>  代替の引用符を使用して、属性内のリテラル二重引用符を配置することができます。 インスタンス内に二重引用符文字を含む文字列を宣言するのに手段として単一引用符を使用することができます。 一重引用符または二重引用符を使用するかどうかの属性値の文字列を開いたり、閉じたりする一致するペアを使用する必要があります。 ありますエスケープ シーケンスやその他の手法の特定の XAML 構文で文字の制限を回避するために使用できます。 参照してください[XML 文字エンティティと XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)です。  
  
 属性構文で、設定するためには、プロパティは、パブリックである必要があり、書き込み可能である必要があります。 バッキング型システムのプロパティの値は、値型である必要があります。 または必要がありますの参照型をインスタンス化したり、関連するアクセスするときに、XAML プロセッサによって参照されているバックアップの種類。  
  
 WPF XAML イベント属性名として参照されているイベントではパブリックであるおよびパブリック デリゲートを持つ必要があります。  
  
 プロパティまたはイベント クラスまたはオブジェクトのコンテナーの要素によってインスタンス化される構造体のメンバーである必要があります。  
  
### <a name="processing-of-attribute-values"></a>属性値の処理  
 開始タグと終了引用符内に含まれる文字列値は、XAML プロセッサによって処理されます。 プロパティの場合は、既定の動作の処理を基になる CLR プロパティの型によって決まります。  
  
 属性の値が、次のいずれかで埋められた次の処理順序を使用します。  
  
1.  XAML プロセッサでは、中かっこまたはから派生したオブジェクトの要素が検出されると<xref:System.Windows.Markup.MarkupExtension>し、参照先のマークアップ拡張機能が最初に評価を文字列として値の処理ではなく、およびマークアップ拡張機能によって返されるオブジェクトとして使用します値。 多くの場合は、既存のオブジェクト、または実行時まで評価されないし、新しくインスタンス化されたオブジェクトではない式への参照が、マークアップ拡張機能によって返されるオブジェクトになります。  
  
2.  プロパティが宣言されている場合、属性付きで<xref:System.ComponentModel.TypeConverter>、またはそのプロパティの値の型が宣言されていると、属性付き<xref:System.ComponentModel.TypeConverter>属性の文字列値は変換の入力として、型コンバーターに送信され、は、コンバーターを返します、新しいオブジェクト インスタンス。  
  
3.  ある場合ありません<xref:System.ComponentModel.TypeConverter>プロパティの型への直接変換が試行されます。 この最後のレベルは、XAML 言語プリミティブ型、または列挙型 (パーサーにアクセスして、一致する値) の名前付き定数の名前のチェックの間のパーサー ネイティブ値に直接変換です。  
  
#### <a name="enumeration-attribute-values"></a>列挙型の属性値  
 XAML での列挙は、XAML パーサーで本質的に処理され、列挙型の名前付き定数のいずれかの文字列名を指定することで列挙体のメンバーを指定する必要があります。  
  
 フラグ列挙値の場合は、ネイティブな動作は、属性値の文字列を処理し、列挙値のいずれかに解決です。 形式で、列挙型を指定しない*列挙*.*値*コードの場合と、します。 代わりに、のみを指定した*値*、および*列挙*を設定するプロパティの型が推論されます。 内の属性を指定する場合、*列挙*.*値*形式が正しく解決されません。  
  
 フラグ列挙体の場合、動作がに基づいて、<xref:System.Enum.Parse%2A?displayProperty=nameWithType>メソッドです。 フラグ列挙体の複数の値は、それぞれの値をコンマで区切って指定できます。 ただし、フラグはない列挙値を組み合わせることはできません。 インスタンスを作成しようとするコンマ構文を使用することはできません、<xref:System.Windows.Trigger>フラグ列挙体の複数の条件で動作します。  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 XAML で設定可能な属性をサポートするフラグ列挙体は、WPF ではまれです。 ただし、このような 1 つの列挙は<xref:System.Windows.Media.StyleSimulations>します。 「解説」に示した例を変更するフラグ属性のコンマ区切り構文を使用することで、インスタンスの<xref:System.Windows.Documents.Glyphs>クラスです。`StyleSimulations = "BoldSimulation"`状態になる`StyleSimulations = "BoldSimulation,ItalicSimulation"`です。 <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType>1 つ以上の列挙値を指定することができますを別のプロパティにです。 ただし、このプロパティは、特殊なケースであるため、<xref:System.Windows.Input.ModifierKeys>列挙体は、独自の型コンバーターをサポートしています。 修飾子の型コンバーターは、コンマ (,) ではなく、区切り記号として、正符号 (+) を使用します。 この変換には、"Ctrl + Alt"などの Microsoft Windows プログラミングでのキーの組み合わせを表す従来の構文がサポートしています。  
  
### <a name="properties-and-event-member-name-references"></a>プロパティとイベント メンバー名の参照  
 属性を指定する場合は、任意のプロパティやイベントを含むオブジェクト要素のためにインスタンス化した CLR 型のメンバーとして存在するを参照できます。  
  
 または、添付プロパティを参照するか、添付イベントを含むオブジェクト要素の独立しました。 (添付プロパティは、後のセクションで説明しますされます)。  
  
 使用して既定の名前空間を介してアクセス可能な任意のオブジェクトからすべてのイベントを付けることができます、 *typeName*.*イベント*部分修飾名です。 ルーティング イベントのハンドラーのアタッチをサポートしていますが、子要素が、親要素からルーティング イベントを処理するハンドラーは、ここでがないそのイベントのメンバー テーブルにこの構文です。 この構文には、添付イベントの構文が似ていますが、イベントをここでは、true 添付イベントではありません。 代わりに、修飾名を持つイベントを参照しています。 詳細については、次を参照してください。[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)です。  
  
 一部のシナリオでは、プロパティ名は属性名ではなく、属性の値として提供される場合があります。 プロパティ名は、フォームで指定されたプロパティなどの修飾子を含めることができますも*ownerType*.*dependencyPropertyName*です。 このシナリオは、XAML でスタイルまたはテンプレートを作成する場合に共通です。 属性値として指定したプロパティ名の処理規則が異なっているし、設定されるプロパティのタイプまたは特定の WPF サブシステムの動作によって制御されます。 詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)です。  
  
 プロパティ名の別の使用方法では属性値には、プロパティ間のリレーションシップがについて説明します。 この機能は、データ バインディングとストーリー ボードのターゲットが使用されで有効になって、<xref:System.Windows.PropertyPath>クラスとその型コンバーター。 参照セマンティクスの詳細については、次を参照してください。 [PropertyPath 構文は XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)です。  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>プロパティ要素構文  
 *プロパティ要素構文*やや要素の基本的な XML 構文規則から逸脱した構文です。 XML では、属性の値は、事実上文字列、可能な唯一のバリエーション文字列エンコード方式が使用されているです。 XAML では、他のオブジェクト要素のプロパティの値であることを割り当てることができます。 この機能は、プロパティ要素構文を有効にします。 要素タグ内の属性として指定されているプロパティではなく、プロパティが指定されて、開始要素を使用してにタグを付ける*elementTypeName*.*propertyName*フォーム内で、プロパティの値が指定されておよびプロパティ要素が閉じられるします。  
  
 具体的には、構文から始まります左山かっこ (\<)、クラスまたはプロパティ要素構文に含まれる構造体の型名ですぐにその後にします。 これが続きますすぐに 1 つのドット (.)、プロパティの名前でし、右の山かっこ (>)。 属性の構文とそのプロパティは、指定した型の宣言されたパブリック メンバー内でが必要です。 プロパティに割り当てられる値は、プロパティ要素内に含まれます。 通常は、値が、1 つ以上のオブジェクトの要素を指定したをアドレスにプロパティ要素構文は、シナリオでは、値としてオブジェクトを指定することがあるためです。 最後に、同じを指定すると同等の終了タグ*elementTypeName*.*propertyName*で適切な入れ子構造とその他の要素タグとのバランス、組み合わせを指定する必要があります。  
  
 たとえば、プロパティ要素構文を次に示します、<xref:System.Windows.FrameworkElement.ContextMenu%2A>のプロパティ、<xref:System.Windows.Controls.Button>です。  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 プロパティ要素内の値も指定できます指定されているプロパティの型がプリミティブ値型の場合、内部テキ ストとしてなど<xref:System.String>、または名前が指定されている列挙体です。 単純な属性の構文を使用することもこれらの各ケースがあるために、これら 2 つの使用方法はあまり一般的ではありません。 文字列にプロパティ要素を 1 つのシナリオは、XAML コンテンツ プロパティではない UI テキストの表示のために使用されるプロパティと、改行などの特定の空白要素はその UI テキストに表示するために必要なです。 属性構文は、改行文字を保持できません。 がアクティブで重要な空白を保持する限り、プロパティ要素構文ができます (詳細については、「 [XAML での空白の処理](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md))。 別のシナリオができるように[X:uid Directive](../../../../docs/framework/xaml-services/x-uid-directive.md) property 要素に適用でき、ため、WPF をローカライズする必要がありますを値の出力 BAML またはその他の手法によって内の値をマークします。  
  
 プロパティ要素は、WPF の論理ツリーでは表されません。 プロパティ要素は、プロパティの設定の特定の構文だけであり、インスタンスまたはオブジェクトを持つ要素ではありません。 (論理ツリーの概念の詳細については、「 [wpf ツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md))。  
  
 属性とプロパティの両方の要素の構文がサポートされている場合、プロパティの 2 つの構文では、空白の処理などの微妙なできます多少の違いの構文が、同じ結果が一般にあります。  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>コレクションの構文  
 XAML の仕様では、XAML プロセッサの実装、値の型がコレクションのプロパティを識別する必要があります。 .NET の一般的な XAML プロセッサの実装はマネージ コードと、CLR に基づいており、次のいずれかの方法でコレクション型を示します。  
  
-   型を実装して<xref:System.Collections.IList>です。  
  
-   型を実装して<xref:System.Collections.IDictionary>です。  
  
-   型から派生して<xref:System.Array>(XAML での配列の詳細については、次を参照してください[X:array のマークアップ拡張機能](../../../../docs/framework/xaml-services/x-array-markup-extension.md)。)。  
  
 プロパティの型がコレクションの場合、推論されるコレクション型をオブジェクト要素としてのマークアップで指定する必要はありません。 代わりに、コレクション内の項目となる要素は、プロパティ要素の 1 つまたは複数の子要素として指定されます。 それらの各項目が読み込み時にオブジェクトを評価し、呼び出すことによって、コレクションに追加、`Add`暗黙的コレクションのメソッドです。 たとえば、<xref:System.Windows.Style.Triggers%2A>プロパティ<xref:System.Windows.Style>は特殊なコレクション型を受け取り<xref:System.Windows.TriggerCollection>を実装する<xref:System.Collections.IList>です。 インスタンスを作成する必要はありません、<xref:System.Windows.TriggerCollection>マークアップ内のオブジェクトの要素。 1 つ以上を指定する代わりに、<xref:System.Windows.Trigger>項目内の要素として、`Style.Triggers`プロパティ要素場所<xref:System.Windows.Trigger>(または派生クラス) は、項目の種類である必要が厳密に型指定されたと暗黙の型です。<xref:System.Windows.TriggerCollection>です。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 プロパティがコレクション型とその型の XAML コンテンツ プロパティの両方になる可能性があり、派生型、これは、このトピックの次のセクションでについて説明します。  
  
 暗黙的コレクションの要素は、マークアップで要素としてがいない場合でも、論理ツリーで表されたメンバーを作成します。 通常、親の型のコンス トラクターは、そのプロパティのいずれかであるコレクションのインスタンス化を実行し、最初に空のコレクションのオブジェクト ツリーの一部になります。  
  
> [!NOTE]
>  リストとディクショナリのジェネリック インターフェイス (<xref:System.Collections.Generic.IList%601>と<xref:System.Collections.Generic.IDictionary%602>) コレクション検出はサポートされていません。 ただし、使用することができます、<xref:System.Collections.Generic.List%601>を基底クラスとしてクラスを実装するため<xref:System.Collections.IList>直接、または<xref:System.Collections.Generic.Dictionary%602>を基底クラスとして実装するため<xref:System.Collections.IDictionary>直接です。  
  
 コレクション型の .NET リファレンス ページにあるコレクションのオブジェクト要素の意図的に省略構文が示されている場合、XAML 構文のセクションで暗黙の型のコレクション構文として。  
  
 ルート要素を除くは実際には、次の場合のいずれかである要素に別の要素の子要素として入れ子になっている XAML ファイル内のすべてのオブジェクト要素その親要素の暗黙的なコレクション プロパティのメンバー。、または要素を親要素 (XAML コンテンツ プロパティは、次のセクションで説明) の XAML コンテンツ プロパティの値を指定します。 つまり、親要素と、マークアップ ページ内の子要素のリレーションシップは、ルートにある 1 つのオブジェクトとすべてのオブジェクト要素のルートの下には、親のプロパティの値を提供する 1 つのインスタンス、または、列内のアイテムのいずれか親のコレクション型プロパティ値でも lection します。 このシングル ルート概念を XML に共通で、XAML を読み込むなどの Api の動作の強化は頻繁に<xref:System.Windows.Markup.XamlReader.Load%2A>です。  
  
 次の例は、コレクションのオブジェクト要素の構文 (<xref:System.Windows.Media.GradientStopCollection>) を明示的に指定します。  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <GradientStopCollection>  
      <GradientStop Offset="0.0" Color="Red" />  
      <GradientStop Offset="1.0" Color="Blue" />  
    </GradientStopCollection>  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
 ある常にコレクションを明示的に宣言することに注意してください。 インスタンスを宣言しようとして<xref:System.Windows.TriggerCollection>で明示的に、前に示した<xref:System.Windows.Style.Triggers%2A>の例は失敗します。 コレクションを明示的に宣言する場合は、コレクション クラスが既定のコンス トラクターをサポートする必要がある必要がありますと<xref:System.Windows.TriggerCollection>既定コンス トラクターがありません。  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>XAML コンテンツ プロパティ  
 XAML コンテンツ構文は、指定のクラスでのみ有効になっている構文、<xref:System.Windows.Markup.ContentPropertyAttribute>クラス宣言の一部として。 <xref:System.Windows.Markup.ContentPropertyAttribute>要素 (派生クラスを含む) の種類のコンテンツ プロパティは、プロパティ名を参照します。 XAML プロセッサによって処理されるとき、すべての子要素や開始タグと終了タグのオブジェクト要素の間で検出された内部テキ ストをそのオブジェクトの XAML コンテンツ プロパティの値に割り当てられますは。 コンテンツのプロパティの明示的なプロパティ要素を指定することは、この使用法は、通常 XAML 構文セクションでは、.NET リファレンスには表示されません。 /Verbose 明示的な手法がマークアップわかりやすくするために、またはマークアップ スタイルの問題としてが通常コンテンツ プロパティの目的をマークアップを効率化できるように、親-子として直感的に関連する要素が直接入れ子にすることができます。 他のプロパティ要素のプロパティ要素タグが厳密な XAML 言語の定義では; ごとには、"content"として割り当てられていません以前、XAML パーサーの処理順序で処理し、「コンテンツ」であると見なされない。  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>XAML コンテンツ プロパティの値が連続している必要があります。  
 XAML コンテンツ プロパティの値は、そのオブジェクト要素の前に、またはその他のすべてのプロパティ要素の後、指定する必要があります。 これは、文字列、または 1 つまたは複数のオブジェクトとして、XAML コンテンツ プロパティの値が指定されているかどうか。 たとえば、次のマークアップを解析できません。  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 これは基本的に法的いない場合はこの構文は、コンテンツのプロパティのプロパティ要素構文を使用して明示的に行われた、し、コンテンツのプロパティが 2 回設定するため。  
  
```xml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 同様に不正な例は、コンテンツ プロパティは、コレクションと、子要素のプロパティ要素が混じっているかどうかです。  
  
```xml  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>   
## <a name="content-properties-and-collection-syntax-combined"></a>コンテンツのプロパティとコレクション構文の組み合わせ  
 そのまま使用するために複数のコンテンツとして 1 つのオブジェクト要素コンテンツ プロパティの型具体的には型でなければなりませんコレクション。 コレクション型のプロパティ要素構文と同様に、XAML プロセッサ必要がありますによって型が識別コレクション型。 要素に、XAML コンテンツ プロパティがあり、ユーザーが XAML コンテンツ プロパティの型がコレクションは、暗黙的なコレクション型はオブジェクト要素としてのマークアップで指定する必要はありません。 し、XAML コンテンツ プロパティはプロパティ el として指定する必要はありません。ement です。 そのため、マークアップで明らかなコンテンツ モデル今すぐ 1 つ以上の子要素、コンテンツとして割り当てられることができます。 コンテンツの構文は、次の<xref:System.Windows.Controls.Panel>クラスを派生します。 すべて<xref:System.Windows.Controls.Panel>派生クラスを確立する XAML のコンテンツ プロパティ<xref:System.Windows.Controls.Panel.Children%2A>、型の値を必要となる<xref:System.Windows.Controls.UIElementCollection>です。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 なおのどちらのプロパティ要素の<xref:System.Windows.Controls.Panel.Children%2A>も、要素の<xref:System.Windows.Controls.UIElementCollection>マークアップで必要なです。 これは、機能は、デザイン XAML の再帰的に定義する要素が含まれているように、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]間にプロパティ要素タグなしの直接の親の子要素の関係を持つ入れ子になった要素のツリーとして表されるより直感的には、またはコレクション オブジェクト。 実際には、<xref:System.Windows.Controls.UIElementCollection>できません明示的に指定するマークアップで、オブジェクト要素として設計します。 そのだけ使用目的は、暗黙の型のコレクションとしてため<xref:System.Windows.Controls.UIElementCollection>はパブリックの既定のコンス トラクターを公開せず、そのため、オブジェクト要素としてインスタンス化できることはできません。  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>プロパティ要素とコンテンツのプロパティを持つオブジェクトのオブジェクト要素の混在  
 XAML の仕様では、XAML プロセッサが、XAML コンテンツ内のプロパティ オブジェクト要素の塗りつぶしに使用されるオブジェクトの要素は、連続している必要があり、いません混在させる必要がありますを適用できることを宣言します。 によってプロパティ要素とコンテンツの混合に対してこの制限が適用されます、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML プロセッサ。  
  
 オブジェクトの子要素は、オブジェクト要素内の最初の即時マークアップとして持つことができます。 プロパティ要素を導入できます。 または、1 つまたは複数のプロパティ要素では、コンテンツ、さらにプロパティ要素を指定することができます。 プロパティ要素のコンテンツに依存して、さらにそのコンテンツを導入することはできません、プロパティ要素にのみ追加することができます。  
  
 このコンテンツのコンテンツとして使用される内部のテキストにプロパティ要素の順序の要件は適用されません。 ただし、マークアップにスタイルを内部テキ ストを重要なホワイト スペースがプロパティ要素は、内部テキ ストが混在している場合に、マークアップで視覚的に検出するが困難になるため、連続したままではまだです。  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>XAML 名前空間  
 上記の構文例の指定された既定の XAML 名前空間以外の XAML 名前空間ありません。 一般的な[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]に指定するアプリケーション、既定の XAML 名前空間、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]名前空間。 既定の XAML 名前空間以外の XAML 名前空間を指定し、同様の構文を引き続き使用できます。 次に、任意の場所で、クラスの名前は、既定の XAML 名前空間内でアクセス可能ではないクラス名に前指定しなければなりません XAML 名前空間のプレフィックスを持つように対応する CLR 名前空間にマップします。 たとえば、`<custom:Example/>`オブジェクト要素の構文のインスタンスをインスタンス化するには、`Example`クラス、そのクラス (および可能性のある外部アセンブリ情報をバッキング型を含む) を含む CLR 名前空間を以前にマップされて、`custom`プレフィックス。  
  
 XAML 名前空間の詳細については、次を参照してください。 [XAML 名前空間と WPF XAML のマッピングの Namespace](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)です。  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>マークアップ拡張機能  
 XAML では、通常 XAML プロセッサの処理は、文字列の属性値またはオブジェクトの要素からエスケープを有効にし、バッキング クラスに処理を延期するエンティティをプログラミングするマークアップ拡張機能を定義します。 始め中かっこ ({})、右中かっこ (}) 以外の文字で後に、属性の構文を使用するときに、XAML プロセッサにマークアップ拡張機能を識別する文字。 始め中かっこの後の最初の文字列には、その部分文字列が真のクラス名の一部である場合に、"Extension"を参照が、部分文字列を含めない場合があります、特定の拡張機能の動作に提供するクラスを参照する必要があります。 その後、1 つのスペースが表示されますし後続の各文字を使用して入力として拡張機能の実装で中かっこが発生するまでです。  
  
 .NET の XAML 実装を使用して、<xref:System.Windows.Markup.MarkupExtension>すべてでサポートされているマークアップ拡張機能の基礎として抽象クラス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]他のフレームワークまたはテクノロジとします。 マークアップ拡張機能を[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]具体的には実装が他の既存のオブジェクトを参照するか、実行時に評価されるオブジェクトへの遅延の参照を作成する手段を提供する多くの場合、対象としています。 指定して、単純な WPF データ バインディングを行うなど、`{Binding}`通常受け取る特定のプロパティ値の代わりに、マークアップ拡張機能です。 WPF のマークアップ拡張機能の多くは、属性の構文を利用できないプロパティの属性の構文が有効にします。 たとえば、<xref:System.Windows.Style>オブジェクトは、比較的複雑な型を入れ子になった一連のオブジェクトとプロパティを含むです。 WPF のスタイルでは、通常のリソースとして定義されます、 <xref:System.Windows.ResourceDictionary>、し、リソースを要求する WPF のマークアップの 2 つの拡張機能のいずれかで参照します。 マークアップ拡張機能リソースの検索するプロパティ値の評価を延期し、値を提供できるように、<xref:System.Windows.FrameworkElement.Style%2A>プロパティの型を取得<xref:System.Windows.Style>で、属性の例を次の構文。  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 ここでは、`StaticResource`を識別、<xref:System.Windows.StaticResourceExtension>マークアップ拡張機能の実装を提供するクラス。 次の文字列`MyStyle`、既定以外の入力として使用される<xref:System.Windows.StaticResourceExtension>コンス トラクター、拡張子の文字列から取得したように、パラメーターが、要求されたを宣言<xref:System.Windows.ResourceKey>です。 `MyStyle`できると予想される、 [X:key](../../../../docs/framework/xaml-services/x-key-directive.md)の値、<xref:System.Windows.Style>リソースとして定義します。 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)使用状況が提供するリソースを使用することを要求、<xref:System.Windows.Style>読み込み時に静的リソースの検索ロジックを使用してプロパティ値。  
  
 マークアップ拡張機能の詳細については、 「[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。 マークアップ拡張機能とその他の XAML プログラミングの一般的な .NET の XAML 実装で有効になっている機能の参照、次を参照してください[XAML Namespace (x:)。言語機能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)します。 WPF 固有のマークアップ拡張機能を参照してください。 [WPF XAML 拡張](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)です。  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>アタッチされるプロパティ  
 アタッチされるプロパティは、XAML のプロパティを所有しているし、特定の型によって定義されたで導入されたプログラミングの概念の任意の要素の属性またはプロパティ要素としてが設定されています。 主に、すべての要素の間で広く共有オブジェクト モデルを必要とせず、親要素に情報を報告するマークアップ構造内の子要素を有効にするのにはアタッチされるプロパティを意図しています。 逆に、アタッチされるプロパティは、子要素に情報を報告する親要素によって使用できます。 アタッチされるプロパティと、独自に作成する方法の目的に関する詳細情報には、プロパティが接続されているを参照してください[添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)です。  
  
 添付プロパティを指定することも一見プロパティ要素構文に似た構文を使用して、 *typeName*.*propertyName*の組み合わせ。 次の 2 つの重要な違いがあります。  
  
-   使用することができます、 *typeName*.*propertyName*属性構文で添付プロパティを設定する場合は偶数の組み合わせ。 添付プロパティが場合のみ、プロパティ名を修飾する属性の構文の要件です。  
  
-   添付プロパティのプロパティ要素構文を使用することもできます。 ただし、一般的なプロパティ要素構文を*typeName*プロパティ要素が含まれるオブジェクトの要素を指定します。 添付プロパティを参照している場合、 *typeName*を含むオブジェクト要素ではなく、添付プロパティを定義するクラスです。  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>アタッチされるイベント  
 アタッチされるイベントは、XAML でイベントを特定の型によって定義できますが、任意のオブジェクト要素のハンドラーをアタッチすることがありますで導入された別のプログラミング概念です。 実装では、WOF 添付イベントを定義する型が、サービスを定義する静的な型を多くの場合、および添付イベントが、ルーティングされたイベントで別名、サービスを公開する型によって公開される場合があります。 添付イベントのハンドラーは、属性構文で指定します。 許可する添付イベントのアタッチされたイベントは、属性の構文が展開した状態、 *typeName*.*eventName*使用法、場所*typeName*を提供するクラスは、`Add`と`Remove`添付イベント インフラストラクチャのイベント ハンドラーのアクセサーおよび*eventName*イベントの名前を指定します。  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>XAML ルート要素の構造  
 次の表は、一般的な XAML ルート要素は、のルート要素の特定の属性の表示を示しています。  
  
|||  
|-|-|  
|`<Page`|ルート要素の開始オブジェクト要素|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|既定値 ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) の XAML 名前空間|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|XAML 言語の XAML 名前空間|  
|`x:Class="ExampleNamespace.ExampleCode"`|部分クラスのマークアップを分離コードに接続する部分クラス宣言の定義|  
|`>`|ルートのオブジェクト要素の終了。 要素には、子要素が含まれているために、オブジェクトはまだ閉じられていません|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>省略可能な非推奨の XAML の使用方法  
 次のセクションでは、技術的には XAML プロセッサによってサポートされているが、詳細度または他の見た目問題に干渉する場合の人間が判読できる残りの XAML ファイルを生成する XAML の使用方法を説明する、XAML ソースを含むアプリケーションの開発.  
  
### <a name="optional-property-element-usages"></a>省略可能なプロパティ要素の使用方法  
 省略可能なプロパティ要素の使用法には、明示的に書き込む要素のコンテンツ プロパティで、XAML プロセッサは暗黙的な考慮が含まれます。 内容を宣言する場合など、 <xref:System.Windows.Controls.Menu>、明示的に宣言することができます、<xref:System.Windows.Controls.ItemsControl.Items%2A>のコレクション、<xref:System.Windows.Controls.Menu>として、`<Menu.Items>`プロパティ要素タグおよび配置の各<xref:System.Windows.Controls.MenuItem>内`<Menu.Items>`ではなく、暗黙的な XAML プロセッサの動作を使用するよりものすべての子要素、<xref:System.Windows.Controls.Menu>する必要があります、<xref:System.Windows.Controls.MenuItem>に配置し、<xref:System.Windows.Controls.ItemsControl.Items%2A>コレクション。 省略可能な使用法はマークアップで表されるオブジェクトの構造を視覚的に明確にするために役立ちます。 またはが明示的にプロパティ要素の使用が技術的には、属性値内で入れ子になったマークアップ拡張機能など、視覚的に混乱しますが、機能するマークアップを回避することがあります。  
  
### <a name="full-typenamemembername-qualified-attributes"></a>修飾された完全 typeName.memberName 属性  
 *TypeName*.*memberName*フォーム ルーティング イベントの場合のみより汎用的な属性は実際に動作します。 他の状況ではそのフォームは不要でありのみマークアップ スタイルと読みやすさの原因の場合、これを避ける必要があります。 参照、3 つ次の例で、<xref:System.Windows.Controls.Control.Background%2A>属性が完全に等価です。  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`機能するためにそのプロパティの修飾参照<xref:System.Windows.Controls.Button>が成功した (<xref:System.Windows.Controls.Control.Background%2A>コントロールから継承された) と<xref:System.Windows.Controls.Button>はオブジェクト要素のクラスまたは基底クラス。 `Control.Background`機能するため、<xref:System.Windows.Controls.Control>クラスは、実際に定義<xref:System.Windows.Controls.Control.Background%2A>と<xref:System.Windows.Controls.Control>は、<xref:System.Windows.Controls.Button>基本クラスです。  
  
 ただし、次*typeName*.*memberName* form の例はコメントが付けられたため表示しては機能しません。  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>別の派生クラスは、 <xref:System.Windows.Controls.Control>、指定した場合と`Label.Background`内で、<xref:System.Windows.Controls.Label>オブジェクト要素の場合は、この使用法は有益です。 ただし、ため<xref:System.Windows.Controls.Label>クラスまたはの基本クラスではありません<xref:System.Windows.Controls.Button>、XAML プロセッサの動作を指定では、処理する`Label.Background`添付プロパティとして。 `Label.Background`使用可能な接続プロパティではなく、この使用法が失敗しました。  
  
### <a name="basetypenamemembername-property-elements"></a>baseTypeName.memberName プロパティ要素  
 操作方法、似たような方法で、 *typeName*.*memberName*フォームの動作属性の構文については、 *baseTypeName*.*memberName*構文のプロパティ要素構文に動作します。 たとえば、次の構文が動作します。  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 ここでは、プロパティ要素は、として指定されました`Control.Background`にプロパティ要素が含まれている場合でも`Button`です。  
  
 同じように、 *typeName*.*memberName*属性に関しては、フォーム*baseTypeName*.*memberName*マークアップでは、不適切なスタイルは、これを避ける必要があります。  
  
## <a name="see-also"></a>参照  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [XAML 名前空間 (x:) 言語機能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [WPF XAML 拡張機能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [TypeConverters および XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)  
 [WPF における XAML とカスタム クラス](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
