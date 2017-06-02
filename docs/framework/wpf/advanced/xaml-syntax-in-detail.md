---
title: "XAML 構文の詳細 | Microsoft Docs"
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
  - "XML 名前空間"
  - "XAML 属性の解析"
  - "解析 (属性の)"
  - "XAML マークアップ拡張機能"
  - "添付プロパティ"
  - "タグ構文 [XAML]"
  - "マークアップ拡張機能"
  - "XAML オブジェクト要素構文"
  - "XAML 構文用語"
  - "添付イベント"
  - "検索セマンティクス"
  - "XAML では、アタッチされるイベント"
  - "XAML では、コンテンツの構文"
  - "XAML では、参照セマンティクス"
  - "コンテンツ構文"
  - "オブジェクト要素構文"
  - "構文用語 [XAML]"
  - "XAML では、添付プロパティ"
  - "解析属性 [XAML]"
  - "XAML では、タグ構文"
  - "XAML 属性の構文"
  - "プロパティ要素構文"
  - "用語 [XAML]"
  - "XML の名前空間"
  - "属性構文 [XAML]"
  - "XAML プロパティ要素構文"
ms.assetid: 67cce290-ca26-4c41-a797-b68aabc45479
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# XAML 構文の詳細
このトピックでは、XAML 構文の要素の説明に使用される用語を定義します。 これらの用語は、具体的には、XAML または System.Xaml レベルで XAML 言語のサポートを有効になっている基本的な XAML の概念を使用するその他のフレームワークも、このドキュメントでは WPF のドキュメントの両方の残りの部分でよく使用されます。 このトピックの展開」で説明する基本的な用語で[XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)します。  
  

  
<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>XAML 言語仕様  
 ここで定義されている XAML 構文の用語も定義されているか、XAML 言語仕様で参照されています。 XAML は XML に基づく言語に依存すると、XML の構造的な規則について詳しく説明します。 用語の一部から共有されてまたは、XML 言語または XML ドキュメント オブジェクト モデルを記述する場合によく使用する用語に基づきます。  
  
 XAML 言語仕様の詳細については、ダウンロード[ \[MS-XAML\] ](http://go.microsoft.com/fwlink/?LinkId=114525) Microsoft ダウンロード センターからです。  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML と CLR  
 XAML は、マークアップ言語です。 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]、その名前では、ランタイムの実行を有効にして、暗黙です。 XAML はないだけで、CLR ランタイムによって直接使用される一般的な言語のいずれかです。 代わりに、XAML の型システムをサポートするいると考えることができます。 WPF で使用される特定の XAML の解析システムは、CLR および CLR 型システムに基づいています。 XAML の型は、WPF の XAML が解析されるときに実行時の表現をインスタンス化する CLR 型にマップされます。 このため、このドキュメント内の構文のディスカッションの残りの部分は、XAML 言語仕様で同等の構文の説明がない場合でも、CLR 型システムへの参照を含まれます。 (個々 の XAML 言語仕様レベル XAML の型にマップすること、その他の型システムに、CLR のないが、作成してさまざまな XAML パーサーの使用を必要とします。)  
  
#### <a name="members-of-types-and-class-inheritance"></a>型のメンバーとクラスの継承  
 プロパティおよびの XAML メンバーとして表示されるイベント、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]型が基本型から継承された多くの場合。 たとえば、次の例:`<Button Background="Blue" .../>`です。 <xref:System.Windows.Controls.Control.Background%2A>プロパティは、すぐに宣言されているプロパティで、<xref:System.Windows.Controls.Button>クラス、クラス定義、リフレクション結果またはドキュメントを確認した場合。 代わりに、<xref:System.Windows.Controls.Control.Background%2A>ベースから継承された<xref:System.Windows.Controls.Control>クラスです。  
  
 クラスの継承の動作の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 要素が重要な従来の XML マークアップをスキーマによって適用されたに解釈します。 クラスの継承は中間の基本クラスは抽象クラスで特に場合、またはインターフェイスが含まれている場合、複雑になることができます。 これは、1 つの理由の XAML 要素およびその使用可能属性のセットが正確かつ完全には、スキーマ型を使用して表さ難しくに通常使用される[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]プログラミングでは、DTD または XSD 形式などです。 別の原因としては、その機能を拡張し、XAML 言語自体の型のマッピング機能が使用可能な型とメンバーのすべての固定表現の完全性を妨げるものでいます。  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>オブジェクト要素構文  
 *オブジェクト要素構文*XML 要素を宣言することで、CLR クラスまたは構造体をインスタンス化する XAML マークアップ構文を示します。 この構文では、HTML など他のマークアップ言語の要素の構文に似ています。 オブジェクト要素構文は、左山かっこ (で始まる\<), followed immediately by the type name of the class or structure being instantiated. followed="" immediately="" by="" the="" type="" name="" of="" the="" class="" or="" structure="" being="">\</), followed immediately by the type name of the class or structure being instantiated.> 0 個以上のスペースは、型名、および&0; 個以上の属性が宣言されてもオブジェクト要素のそれぞれの属性名を分離する&1; つ以上のスペースを含む =「値」ペア。 最後は、次のいずれかの必要があります。  
  
-   要素とタグは、右の山かっこ (>) がすぐに続くフォワード スラッシュ (/) によって終了する必要があります。  
  
-   右の山かっこ (>) では、開始タグを完了する必要があります。 その他のオブジェクトの要素、プロパティ要素、または内部テキ ストは、開始タグをフォローできます。 要素のオブジェクト モデルによっては、どのようなコンテンツをここで含めることが正確には制限が通常されます。 対応するオブジェクトの要素のタグを終了する必要がありますも適切な入れ子でが存在し、その他の開始と終了タグのペアとのバランスをとる。  
  
 .NET に実装された XAML オブジェクト要素にプロパティまたはイベント、および XAML 名前空間を CLR 名前空間とアセンブリに属性の種類にマップするルールのセットがあります。 WPF と .NET Framework では、XAML オブジェクト要素にマップされる[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]型で定義されているが、アセンブリを参照し、属性、それらの型のメンバーにマップします。 XAML で CLR 型を参照するときにもその型の継承されたメンバーへのアクセスがあります。  
  
 たとえば、次の例は、オブジェクト要素構文の新しいインスタンスをインスタンス化する、<xref:System.Windows.Controls.Button>クラスし、も指定、<xref:System.Windows.FrameworkElement.Name%2A>属性とその属性の値。  
  
 [!code-xml[XAMLOvwSupport#SyntaxOE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 次の例は、XAML コンテンツ プロパティの構文を含むオブジェクト要素構文です。 含まれる内部のテキストを使用して設定することは、 <xref:System.Windows.Controls.TextBox> XAML のコンテンツ プロパティ<xref:System.Windows.Controls.TextBox.Text%2A>します。  
  
 [!code-xml[XAMLOvwSupport#ThisIsATextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>コンテンツ モデル  
 クラスは、構文という点で、XAML オブジェクト要素としての使用方法をサポートする可能性がありますはその要素はのみ正しく機能のアプリケーションやページの全体的なコンテンツのモデルや要素ツリーの適切な位置に配置されている場合。 たとえば、 <xref:System.Windows.Controls.MenuItem>の子としてのみ配置通常、 <xref:System.Windows.Controls.Primitives.MenuBase>などのクラスを派生<xref:System.Windows.Controls.Menu>します。 コンテンツ コントロール、およびその他のクラスのページで、「解説」の一部として特定要素モデルが記載されている[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 要素として使用できるクラスです。  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>オブジェクト要素のプロパティ  
 XAML でのプロパティは、さまざまな構文で設定されます。 特定のプロパティの構文を使用できますが、に応じて変わりますを設定するプロパティの基になる型システムの特性。  
  
 プロパティの値を設定するには、機能や特性オブジェクトに追加するように、実行時のオブジェクト グラフ内に存在します。 オブジェクト要素から作成されたオブジェクトの初期状態は、既定のコンス トラクターの動作に基づきます。 通常、アプリケーションは、完全に既定のインスタンスの任意のオブジェクト以外に使用されます。  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>属性構文 (プロパティ)  
 属性構文では、既存のオブジェクト要素の属性を宣言することで、プロパティの値を設定する XAML マークアップの構文です。 属性名は、関連するオブジェクトの要素をサポートするクラスのプロパティの CLR メンバー名と一致する必要があります。 属性名には、代入演算子 (=) が続きます。 属性値には、引用符で囲まれた文字列を指定する必要があります。  
  
> [!NOTE]
>  代替の引用符を使用して、属性内のリテラル二重引用符を配置できます。 インスタンスの内部に二重引用符文字を含む文字列を宣言するのに手段として単一引用符を使用できます。 一重または二重引用符を使用するかどうかは、属性値の文字列を開いたり、閉じたりするため、一致するペアを使用してください。 ありますエスケープ シーケンスやその他の手法によって XAML の構文の特定の文字制限を回避するために使用できます。 参照してください[XML 文字エンティティと XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)します。  
  
 属性構文で設定するためにプロパティはパブリックであることし、書き込み可能である必要があります。 バッキング型のシステムのプロパティの値は、値型である必要があります。 または必要がある参照型をインスタンス化されたか、関連するアクセスするときに、XAML プロセッサによって参照されることができますバックアップの種類。  
  
 WPF XAML イベント属性名として参照されているイベントではパブリックであるおよびパブリック デリゲートを用意する必要があります。  
  
 プロパティまたはイベント クラスまたはオブジェクトのコンテナーの要素によってインスタンス化される構造体のメンバーである必要があります。  
  
### <a name="processing-of-attribute-values"></a>属性値の処理  
 開始タグと終わりの引用符内に含まれる文字列値は、XAML プロセッサによって処理されます。 プロパティの場合は、既定の処理動作を基になる CLR プロパティの型によって決まります。  
  
 属性の値が、次のいずれかで埋められた次の処理順序を使用します。  
  
1.  XAML プロセッサは、中かっこ、またはから派生するオブジェクト要素が発生すると<xref:System.Windows.Markup.MarkupExtension>し、参照先のマークアップ拡張機能が最初に評価を文字列として値の処理ではなく、およびマークアップ拡張機能によって返されるオブジェクトは、値として使用します。 多くの場合は、マークアップ拡張機能によって返されるオブジェクトを既存のオブジェクトまたは実行時まで評価されないし、新しくインスタンス化されたオブジェクトではない式への参照となります。  
  
2.  プロパティが宣言されている場合、属性付きで<xref:System.ComponentModel.TypeConverter>、またはそのプロパティの値の型が宣言されると、属性付き<xref:System.ComponentModel.TypeConverter>属性の文字列値が変換の入力として、型コンバーターに送信され、コンバーターは、新しいオブジェクト インスタンスを返します。  
  
3.  ある場合ない<xref:System.ComponentModel.TypeConverter>プロパティの型への直接変換が試行されます。 この最後のレベルは、XAML 言語プリミティブ型、または (パーサーは、一致する値をその後、アクセス) 列挙型の名前付き定数の名前のチェックの間のパーサー ネイティブ値に直接変換です。  
  
#### <a name="enumeration-attribute-values"></a>列挙属性値  
 XAML での列挙は、XAML パーサーで本質的に処理され、列挙型の名前付き定数のいずれかの文字列名を指定することで列挙体のメンバーを指定する必要があります。  
  
 フラグ列挙値の場合は、ネイティブな動作は、属性値の文字列を処理し、列挙値のいずれかに解決です。 形式の列挙型を指定しない*列挙*.*値*コードで行うようにします。 代わりに、だけを指定する*値*、および*列挙*を設定するプロパティの型により推測されます。 内の属性を指定する場合、*列挙*.*値*フォームに正しく解決されません。  
  
 フラグ列挙体の動作に基づく、 <xref:System.Enum.Parse%2A?displayProperty=fullName>メソッドです。 フラグ列挙体の複数の値は、それぞれの値をコンマで区切って指定できます。 ただし、フラグはない列挙値を組み合わせることはできません。 たとえば、コンマ構文を使用して作成しようとすることはできません、<xref:System.Windows.Trigger>フラグ列挙体の複数の条件に機能します。  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 XAML で設定できる属性をサポートするフラグ列挙体では、WPF ではまれです。 ただし、このような&1; つの列挙は<xref:System.Windows.Media.StyleSimulations>です。 「解説」に示した例を変更するフラグの属性をコンマで区切られた構文を使用するなど、<xref:System.Windows.Documents.Glyphs>クラスです。`StyleSimulations = "BoldSimulation"`なる`StyleSimulations = "BoldSimulation,ItalicSimulation"`します。 <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=fullName>別のプロパティでは、1 つ以上の列挙値を指定できます。 ただし、このプロパティがである特殊なケースであるため、<xref:System.Windows.Input.ModifierKeys>列挙体は、独自の型コンバーターをサポートしています。 修飾子の型コンバーターは、プラス記号 (+) をコンマ (,) ではなく、区切り記号として使用します。 この変換には、"Ctrl + Alt"などの Microsoft Windows プログラミングではキーの組み合わせを表す従来の構文がサポートしています。  
  
### <a name="properties-and-event-member-name-references"></a>プロパティおよびイベント メンバー名の参照  
 属性を指定する場合は、任意のプロパティまたはオブジェクトのコンテナー要素にインスタンス化された CLR 型のメンバーとして存在するイベントを参照できます。  
  
 また、添付プロパティを参照できるや、アタッチされるイベントの格納オブジェクト要素に依存しません。 (添付プロパティは、後のセクションで説明しますが)。  
  
 使用して既定の名前空間を介してアクセス可能なすべてのオブジェクトからイベントを名前も、 *typeName*.*イベント*部分修飾名。 ルーティング イベントのハンドラーのアタッチをサポートしていますが、子要素、親要素からルーティング イベントを処理するハンドラーは、ここでがないイベントのメンバー テーブルにこの構文です。 この構文には、アタッチされるイベントの構文が似ていますが、イベントをここでは、true アタッチされるイベントではありません。 代わりに、修飾名を持つイベントを参照しています。 詳細については、次を参照してください。[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)します。  
  
 シナリオによっては、プロパティ名が属性名ではなく、属性の値として提供される場合があります。 プロパティ名では、フォームで指定されたプロパティなどの修飾子を含めることも*ownerType*.*dependencyPropertyName*します。 スタイルまたはテンプレートを XAML に書き込むときに、このシナリオが一般的です。 属性値として指定したプロパティ名の処理規則では、仕様が異なると、設定されるプロパティのタイプまたは特定の WPF サブシステムの動作によって制御されます。 詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)します。  
  
 プロパティ名の他の使用方法は、属性値は、プロパティ間のリレーションシップを記述するときにです。 この機能は、データ バインドとストーリー ボードのターゲットに使用されで有効になって、 <xref:System.Windows.PropertyPath>クラスとその型コンバーター。 検索セマンティクスの詳細については、次を参照してください。 [PropertyPath の XAML 構文](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)します。  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>プロパティ要素構文  
 *プロパティ要素構文*やや要素の基本的な XML 構文規則から逸脱した構文です。 XML では、属性の値は、事実上文字列、可能なバリエーション文字列エンコード方式が使用されているです。 XAML では、他のオブジェクト要素のプロパティの値であることを割り当てることができます。 この機能は、プロパティ要素構文は有効です。 要素のタグ内の属性として指定されているプロパティではなく、プロパティが指定されて、開始要素を使用してタグに*elementTypeName*.*propertyName*フォーム内で、プロパティの値が指定されているし、property 要素が閉じられます。  
  
 構文は、左山かっこ (始め具体的には、\<), followed immediately by the type name of the class or structure that the property element syntax is contained within. followed="" immediately="" by="" the="" type="" name="" of="" the="" class="" or="" structure="" that="" the="" property="" element="" syntax="" is="" contained="">\</), followed immediately by the type name of the class or structure that the property element syntax is contained within.> これの直後&1; つのドット (.) し、プロパティの名前で、右の山かっこ (>)。 属性構文と同様、そのプロパティは、指定した型の宣言されたパブリック メンバーに配置する必要があります。 プロパティに割り当てられる値は、property 要素に含まれます。 通常、値が、1 つ以上のオブジェクトの要素を指定した、アドレス プロパティ要素構文は、シナリオは、値としてオブジェクトを指定するためです。 最後に、同じを指定することと同等の終了タグ*elementTypeName*.*propertyName*適切な入れ子や他の要素タグとのバランスがでの組み合わせを指定する必要があります。  
  
 次のプロパティ要素構文は、たとえば、 <xref:System.Windows.FrameworkElement.ContextMenu%2A>のプロパティ、<xref:System.Windows.Controls.Button>します。  
  
 [!code-xml[XAMLOvwSupport#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 プロパティ要素内の値できますとして指定することで指定されているプロパティの型がプリミティブ値型の場合の内部テキ ストなど<xref:System.String>、または名前が指定されている列挙します。 シンプルな属性構文を使用する可能性がありますもこれらの各ケースがあるために、2 つの用法は、それほど一般的ではありません。 XAML コンテンツ プロパティではありませんが、UI テキストの表示のために使用されるプロパティは文字列にプロパティ要素をシナリオの&1; つあり、改行などの特殊な空白要素はその UI テキストに表示するために必要な。 属性構文は、改行を保持できません。 が有意の空白の維持がアクティブな場合に限り、プロパティ要素構文ができます (詳細については、「 [XAML で空白の処理](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md))。 別のシナリオはように[X:uid ディレクティブ](../../../../docs/framework/xaml-services/x-uid-directive.md)プロパティ要素に適用されることができ、そのため、WPF のローカライズ必要がある値の出力 BAML またはその他の手法によって内の値をマークします。  
  
 Property 要素は、WPF の論理ツリーには表示されません。 Property 要素は、プロパティを設定するため特定の構文だけであり、インスタンスまたはオブジェクトを持つ要素ではありません。 (論理ツリーの概念の詳細については、「 [WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)。)  
  
 プロパティの属性とプロパティの両方の要素の構文がサポートされている場合、2 種類の構文では、構文の空白の処理などの細かい点が多少異なる場合が同じ結果が一般にいます。  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>コレクション構文  
 XAML 仕様書には、XAML プロセッサ実装で、値の型がコレクションのプロパティを識別する必要があります。 .NET での一般的な XAML プロセッサ実装はマネージ コードと、CLR に基づいており、次のいずれかの方法でコレクション型を識別します。  
  
-   入力を実装して<xref:System.Collections.IList>します。  
  
-   入力を実装して<xref:System.Collections.IDictionary>します。  
  
-   型から派生して<xref:System.Array>(XAML で配列の概要の詳細については、次を参照してください[X:array のマークアップ拡張機能](../Topic/x:Array%20Markup%20Extension.md)。)。  
  
 プロパティの型がコレクションの場合、推論されるコレクション型をマークアップには、object 要素として指定する必要はありません。 代わりに、コレクション内の項目となる要素はプロパティ要素の&1; つまたは複数の子要素として指定します。 それらの各項目が読み込み時にオブジェクトを評価し、呼び出すことによって、コレクションに追加、`Add`の暗黙的なコレクション メソッド。 たとえば、<xref:System.Windows.Style.Triggers%2A>プロパティの<xref:System.Windows.Style>は特殊なコレクション型を受け取り<xref:System.Windows.TriggerCollection>を実装する<xref:System.Collections.IList>します。 インスタンスを作成する必要はありません、 <xref:System.Windows.TriggerCollection>マークアップ内のオブジェクト要素。 代わりに、1 つまたは複数を指定<xref:System.Windows.Trigger>項目内の要素として、`Style.Triggers`プロパティ要素で<xref:System.Windows.Trigger> (または派生クラス) は厳密に型指定されたと暗黙的な項目の種類として期待される型です。 <xref:System.Windows.TriggerCollection>します。  
  
 [!code-xml[XAMLOvwSupport#SyntaxPECollection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 プロパティは、コレクション型とその型の XAML コンテンツ プロパティの両方になる場合があり、派生型は、このトピックの次へ セクションで説明します。  
  
 暗黙的コレクションの要素は、マークアップで要素としては表示しない場合でも、論理ツリーで表されたメンバーを作成します。 通常親の型のコンス トラクターは、そのプロパティの&1; つであるコレクションのインスタンス化を実行し、最初に空のコレクションのオブジェクト ツリーの一部になります。  
  
> [!NOTE]
>  ジェネリック リストおよび辞書インターフェイス (<xref:System.Collections.Generic.IList%601>と<xref:System.Collections.Generic.IDictionary%602>) コレクションの検出はサポートされていません\</TKey, TValue>。 ただし、使用することができます、<xref:System.Collections.Generic.List%601>クラスの基本クラスとして実装しているため<xref:System.Collections.IList>を直接または<xref:System.Collections.Generic.Dictionary%602>基底クラスとして実装しているため<xref:System.Collections.IDictionary>直接\</TKey, TValue>。  
  
 コレクション型の .NET のリファレンス ページをコレクションのオブジェクト要素の意図的に省略は、この構文はときどき XAML 構文セクションで暗黙の型のコレクション構文として説明します。  
  
 ルート要素を除き、本当に、次の場合の一方または両方にある要素に別の要素の子要素として入れ子になっている XAML ファイル内のすべてのオブジェクト要素: 親要素、または親要素 (XAML コンテンツ プロパティは、後のセクションで説明) の XAML コンテンツ プロパティの値を指定する要素の暗黙的なコレクション プロパティのメンバーです。 つまり、親要素とマークアップ ページ内の子要素のリレーションシップはルートで、1 つのオブジェクトと、ルートの直下にすべてのオブジェクト要素は、親のプロパティ値を提供する&1; つのインスタンスまたは親のコレクション型プロパティ値になっているコレクション内の項目のいずれかです。 このシングル ルート概念、xml に共通で、XAML を読み込むなどの Api の動作の頻度がより強化<xref:System.Windows.Markup.XamlReader.Load%2A>します。  
  
 次の例は、コレクションのオブジェクト要素構文 (<xref:System.Windows.Media.GradientStopCollection>) を明示的に指定します。  
  
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
  
 ある常に、コレクションを明示的に宣言することに注意してください。 インスタンスを宣言しよう<xref:System.Windows.TriggerCollection>前に示したで明示的に<xref:System.Windows.Style.Triggers%2A>の例は失敗します。 コレクションを明示的に宣言するには、コレクション クラスで既定のコンス トラクターがサポートしている必要があり、 <xref:System.Windows.TriggerCollection>既定のコンス トラクターがありません。  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>XAML コンテンツ プロパティ  
 XAML コンテンツ構文は、指定のクラスにのみ有効になっている構文、 <xref:System.Windows.Markup.ContentPropertyAttribute>クラス宣言の一部として。 <xref:System.Windows.Markup.ContentPropertyAttribute>要素 (派生クラスを含む) の種類のコンテンツ プロパティは、プロパティ名を参照します。 XAML プロセッサによって処理されるときにすべての子要素またはタグと終了タグのオブジェクト要素の間にある内部のテキストは、そのオブジェクトの XAML コンテンツ プロパティの値に割り当てるされます。 コンテンツ プロパティの明示的なプロパティ要素を指定する権限を持っているが、この使用法は、通常 XAML 構文セクションでは、.NET のリファレンスでは表示されません。 明示的な詳細な方法がマークアップわかりやすくするため、またはマークアップのスタイルの問題が、通常コンテンツ プロパティの目的は、親-子として直感的に関連する要素は、直接できます入れ子になったため、マークアップを効率化します。 要素の他のプロパティのプロパティ要素タグが厳密な XAML 言語定義ごとには、"content"に割り当てられていません。これらは、XAML パーサーの処理順序で以前に処理され、「コンテンツ」であると見なされないします。  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>XAML コンテンツ プロパティの値が連続している必要があります。  
 XAML のコンテンツ プロパティの値は、そのオブジェクト要素の前に、またはその他のすべてのプロパティ要素の後、指定する必要があります。 これは、文字列、または&1; つまたは複数のオブジェクトとして、XAML コンテンツ プロパティの値が指定されているかどうかに当てはまります。 たとえば、次のマークアップは解析されません。  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 これは基本的には正しくない場合はこの構文は、コンテンツ プロパティのプロパティ要素構文を使用して明示的に行われた、し、コンテンツのプロパティが&2; 回設定するため。  
  
```  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 同様に不正な例では、コンテンツのプロパティは、コレクションと、子要素のプロパティ要素が混じっているかどうかを示します。  
  
```  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>   
## <a name="content-properties-and-collection-syntax-combined"></a>コンテンツ プロパティとコレクション構文の組み合わせ  
 そのまま使用するために複数のコンテンツとして&1; つのオブジェクト要素コンテンツのプロパティの型必要があります具体的にはコレクション型であります。 コレクション型のプロパティ要素構文と同様に、XAML プロセッサ必要がありますによって型が識別コレクション型。 要素に XAML コンテンツ プロパティがあり、ユーザーが XAML コンテンツ プロパティの型がコレクションは、暗黙的なコレクション型はオブジェクト要素としてのマークアップで指定する必要はありませんし、XAML コンテンツ プロパティがプロパティ要素として指定する必要はありません。 したがって、マークアップで明らかなコンテンツ モデル今すぐ複数の子要素がコンテンツとして割り当てられていることができます。 コンテンツの構文を次に、<xref:System.Windows.Controls.Panel>クラスを派生します。 すべて<xref:System.Windows.Controls.Panel>派生クラスを確立する XAML のコンテンツ プロパティ<xref:System.Windows.Controls.Panel.Children%2A>、型の値がありますが、 <xref:System.Windows.Controls.UIElementCollection>します。  
  
 [!code-xml[XAMLOvwSupport#SyntaxContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 注意してくださいのいずれのプロパティ要素の<xref:System.Windows.Controls.Panel.Children%2A>の要素も、 <xref:System.Windows.Controls.UIElementCollection>マークアップに必要なです。 XAML のデザイン機能は、再帰的に定義する要素が含まれているようにこれは、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]より直感的にせず、介在するプロパティ要素のタグまたはコレクション オブジェクトの直接の親と子要素の関係を持つ入れ子になった要素のツリーとして表現されます。 実際には、 <xref:System.Windows.Controls.UIElementCollection>では指定できない明示的にマークアップでオブジェクト要素としてデザインします。 その唯一の用途を暗黙の型のコレクションとして<xref:System.Windows.Controls.UIElementCollection>パブリックの既定のコンス トラクターを公開しないと、そのため、オブジェクト要素としてインスタンス化できることはできません。  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>プロパティ要素とコンテンツのプロパティを持つオブジェクトのオブジェクト要素の混在  
 XAML 仕様書では、オブジェクト要素内の XAML コンテンツ プロパティが使用されているオブジェクトの要素が、連続する必要があり、混在させないでください XAML プロセッサが実施できることを宣言します。 プロパティ要素とコンテンツを混在させると、この制限が適用される、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML プロセッサ。  
  
 オブジェクトの子要素は、object 要素内の最初の即時マークアップとして設定できます。 プロパティ要素を導入できます。 または、1 つまたは複数のプロパティ要素では、コンテンツ、プロパティの多くの要素を指定することができます。 Property 要素コンテンツに依存して、さらにそのコンテンツを導入することはできません、のみプロパティ要素を追加することができます。  
  
 このコンテンツ]、[プロパティ要素の順序の要件は、コンテンツとして使用される内部のテキストには適用されません。 ただし、有意の空白はプロパティ要素の内部テキ ストが混じって場合は、マークアップで視覚的に検出が困難になるために、内部テキ ストの連続したを保持するマークアップのスタイルではまだです。  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>XAML 名前空間  
 上記の構文例は、既定の XAML 名前空間以外の XAML 名前空間を指定します。 一般的な[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション、既定の XAML 名前空間が指定されている、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]名前空間。 既定の XAML 名前空間以外の XAML 名前空間を指定し、同様の構文を使用できます。 次に、任意の場所ではという名前のクラスは、既定の XAML 名前空間内でアクセスできないクラス名にする必要がありますの前に、XAML 名前空間のプレフィックスように対応する CLR 名前空間にマップします。 たとえば、`<custom:Example/>`のインスタンスをインスタンス化するオブジェクト要素構文は、`Example`クラス、そのクラス (および場合によってはバッキング型を含む外部アセンブリ情報) を含む CLR 名前空間を以前に割り当てられて、`custom`プレフィックス。  
  
 XAML 名前空間の詳細については、次を参照してください。 [XAML 名前空間および WPF XAML のマッピング情報 Namespace](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)します。  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>マークアップ拡張機能  
 XAML では、通常 XAML プロセッサの処理は、文字列の属性値またはオブジェクトの要素からエスケープが有効にし、バッキング クラスに処理を延期するエンティティのプログラミング、マークアップ拡張機能を定義します。 中かっこ ({})、右中かっこ (}) 以外の文字で後に、属性の構文を使用するときに xaml マークアップ拡張機能を識別する文字。 中かっこの後の最初の文字列には、その部分文字列が真のクラス名の一部である場合、特定の拡張機能の動作は、参照が、部分文字列を含めない場合があります"Extension"を提供するクラスを参照する必要があります。 その後は単一の空白は見えますが、し、各文字を含めるが入力として使用拡張機能の実装で右中かっこが検出されるまでです。  
  
 .NET XAML の実装を使用して、<xref:System.Windows.Markup.MarkupExtension>でサポートされているマークアップ拡張機能のすべての基礎として抽象クラス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]だけでなく他のフレームワークやテクノロジです。 マークアップ拡張機能を[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]具体的には実装が他の既存のオブジェクトを参照するか、実行時に評価されるオブジェクトへの遅延の参照を作成する手段を提供する多くの場合、対象としています。 指定して単純な WPF データ バインドを行うなど、`{Binding}`通常受け取る特定のプロパティ値の代わりに、マークアップ拡張機能です。 WPF のマークアップ拡張機能の多くには、プロパティが属性構文を利用できないための属性構文が有効にします。 たとえば、<xref:System.Windows.Style>オブジェクトは、比較的複雑な型を入れ子になった一連のオブジェクトとプロパティを含みます。 WPF のスタイルでは、通常のリソースとして定義、 <xref:System.Windows.ResourceDictionary>リソースを要求 WPF マークアップの&2; つの拡張機能のいずれかを使用し、参照します。 マークアップ拡張機能リソースの検索対象のプロパティ値の評価されないしの値を提供できるように、<xref:System.Windows.FrameworkElement.Style%2A>プロパティには、型を取得<xref:System.Windows.Style>で、属性の構文例を次に示します。  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 ここでは、`StaticResource`を識別、 <xref:System.Windows.StaticResourceExtension>マークアップ拡張機能の実装を提供するクラス。 次の文字列`MyStyle`は、既定以外の入力として使用<xref:System.Windows.StaticResourceExtension>コンス トラクター、拡張子の文字列から取得したようにパラメーターが要求されたコマンドを宣言<xref:System.Windows.ResourceKey>します。 `MyStyle`できると予想される、 [X:key](../../../../docs/framework/xaml-services/x-key-directive.md)の値、<xref:System.Windows.Style>リソースとして定義します。 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)使用状況が提供する、リソースが使用することを要求、<xref:System.Windows.Style>の読み込み時に静的リソースの検索ロジックを使用してプロパティ値です。  
  
 マークアップ拡張機能の詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)します。 マークアップ拡張機能とプログラミング機能の全般的な .NET XAML 実装で有効になっている他の XAML の参照を次を参照してください[XAML Namespace (x:)。言語機能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)です。 WPF 固有のマークアップ拡張機能を参照してください。 [WPF XAML 拡張機能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)です。  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>アタッチされるプロパティ  
 添付プロパティは XAML のプロパティを所有しているし、特定の型によって定義されたそれによってで導入されたプログラミングの概念上の任意の要素が属性または要素のプロパティとして設定します。 主なシナリオは、すべての要素の間で広範囲に共有されたオブジェクト モデルを必要とせず、親要素に情報を報告するためのマークアップ構造内の子要素を有効にするのには、添付プロパティを意図しています。 逆に、添付プロパティは、子要素に情報をレポートする親要素によって使用できます。 アタッチされたプロパティと、独自に作成する方法の目的に関する詳細については、プロパティを接続を参照してください。[添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)します。  
  
 添付プロパティは、表面的プロパティ要素構文に似た構文を使用で指定することも、 *typeName*.*propertyName*の組み合わせ。 次の&2; つの重要な違いがあります。  
  
-   使用することができます、 *typeName*.*propertyName*属性構文で添付プロパティを設定した場合でもの組み合わせ。 添付プロパティは、だけ大文字と小文字プロパティ名を修飾するが属性構文の要件です。  
  
-   添付プロパティのプロパティ要素構文を使用することもできます。 ただし、一般的なプロパティ要素構文について、 *typeName*プロパティ要素が含まれるオブジェクトの要素を指定します。 添付プロパティを参照している場合、 *typeName*オブジェクト要素ではなく、添付プロパティを定義するクラスです。  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>アタッチされるイベント  
 アタッチされるイベントは、イベントは、特定の種類で定義できますが、オブジェクト要素のハンドラーが接続されている XAML で導入されたもう&1; つのプログラミング概念です。 WOF 実装では多くの場合、アタッチされるイベントを定義する型は、サービスを定義する静的な型と、アタッチされるイベントが、ルーティングされたイベントでの別名、サービスを公開する型によって公開される場合があります。 アタッチされるイベントのハンドラーは、属性構文で指定します。 アタッチされるイベントを許可するようにアタッチされるイベントの属性の構文を展開、 *typeName*.*eventName*使用法、場所*typeName*を提供するクラスは、`Add`と`Remove`、アタッチされるイベント インフラストラクチャのためのイベント ハンドラーのアクセサーと*eventName*イベントの名前を指定します。  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>XAML ルート要素の構造  
 次の表は、一般的な XAML ルート要素は、のルート要素の特定の属性の表示を示しています。  
  
|||  
|-|-|  
|`<Page`|ルート要素の開始オブジェクト要素|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|既定値 ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) の XAML 名前空間|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|XAML 言語の XAML 名前空間|  
|`x:Class="ExampleNamespace.ExampleCode"`|部分クラスに対して定義されているマークアップを分離コードに接続する部分クラス宣言|  
|`>`|ルートのオブジェクト要素の終了。 要素には、子要素が含まれているためオブジェクトがまだ閉じていません。|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>オプションであり、非推奨の XAML の使用方法  
 次のセクションでは、技術的には、XAML プロセッサでサポートされているが、詳細度またはその他の美しさ妨げになる問題時期を人間が判読できる残りの XAML ファイルを生成する XAML の使用方法を説明する、XAML ソースを含むアプリケーションを開発します。  
  
### <a name="optional-property-element-usages"></a>省略可能なプロパティ要素の使用方法  
 省略可能なプロパティ要素の使用状況には、XAML プロセッサが暗黙の型が判断した要素のコンテンツ プロパティを明示的に記述が含まれます。 内容を宣言する場合など、 [] メニューの <xref:System.Windows.Controls.Menu>を明示的に宣言することもできます、<xref:System.Windows.Controls.ItemsControl.Items%2A>のコレクション、<xref:System.Windows.Controls.Menu>として、`<Menu.Items>`プロパティ要素のタグおよび配置<xref:System.Windows.Controls.MenuItem>内で`<Menu.Items>`、暗黙的な XAML プロセッサの動作を使用するのではなくのすべての子要素、 [] メニューの <xref:System.Windows.Controls.Menu>する必要があります、 <xref:System.Windows.Controls.MenuItem>に配置し、<xref:System.Windows.Controls.ItemsControl.Items%2A>コレクションです。 省略可能な使用法は視覚的に、マークアップで表されるオブジェクトの構造が明確にできます。 または、明示的なプロパティ要素の使用が技術的には、属性値内での入れ子になったマークアップ拡張機能など、視覚的に混乱しますが、機能するマークアップを回避することがあります。  
  
### <a name="full-typenamemembername-qualified-attributes"></a>完全 typeName.memberName 属性の修飾  
 The *typeName*.*memberName*フォーム ルーティング イベントの場合だけより汎用的な属性が実際に機能します。 他の状況でそのフォーム不要で、マークアップのスタイルや読みやすさの原因のためだけを避ける必要があります。 参照、3 つ以下の例では、<xref:System.Windows.Controls.Control.Background%2A>属性が完全に等価です。  
  
 [!code-xml[XAMLOvwSupport#TypeNameProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`有効でプロパティの修飾参照<xref:System.Windows.Controls.Button>が成功した (<xref:System.Windows.Controls.Control.Background%2A>コントロールから継承された) と<xref:System.Windows.Controls.Button>はオブジェクト要素のクラスまたは基本クラスです。 `Control.Background`ので、<xref:System.Windows.Controls.Control>クラスは実際には、定義<xref:System.Windows.Controls.Control.Background%2A>と<xref:System.Windows.Controls.Control>は、<xref:System.Windows.Controls.Button>基本クラスです。  
  
 ただし、次*typeName*.*memberName* form の例は行われず、コメントがあるため表示されます。  
  
 [!code-xml[XAMLOvwSupport#TypeNameBadProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>の別の派生クラスは、<xref:System.Windows.Controls.Control>、指定した場合と`Label.Background`内で、<xref:System.Windows.Controls.Label>オブジェクト要素の場合は、この使用法が機能します。 ただし、ため<xref:System.Windows.Controls.Label>クラスまたは基本クラスではない<xref:System.Windows.Controls.Button>は、指定した XAML プロセッサの動作を処理し、`Label.Background`添付プロパティとして。 `Label.Background`使用可能な添付プロパティではなく、この使用法が失敗しました。  
  
### <a name="basetypenamemembername-property-elements"></a>baseTypeName.memberName プロパティ要素  
 方法と同様の方法で、 *typeName*.*memberName*属性構文では、フォームの動作、*関連付ける*.*memberName*構文のプロパティ要素構文に動作します。 たとえば、次の構文が動作します。  
  
 [!code-xml[XAMLOvwSupport#GoofyPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 ここでは、property 要素は、として指定された`Control.Background`に property 要素が含まれている場合でも`Button`します。  
  
 同じですが、 *typeName*.*memberName*属性で、フォーム*関連付ける*.*memberName*マークアップでは、スタイルは、これを避ける必要があります。  
  
## <a name="see-also"></a>関連項目  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [XAML Namespace (x:)言語機能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)   
 [WPF XAML 拡張機能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)   
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [TypeConverters および XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)   
 [XAML と WPF のカスタム クラス](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)