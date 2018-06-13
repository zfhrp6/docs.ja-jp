---
title: .NET Framework XAML サービスで使用するためのカスタム型の定義
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: 9edc7baa1a540a71997cf5b1ed010ad5c7960d17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566497"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>.NET Framework XAML サービスで使用するためのカスタム型の定義
ビジネス オブジェクトは、カスタム型の定義または特定のフレームワークに依存関係がない型は、するときに行うことができる XAML の運用方法があります。 これらのプラクティスに従うと場合、.NET Framework XAML サービスおよびその XAML リーダーと XAML ライターを型の XAML の特性を検出し、XAML 型システムを使用して XAML ノード ストリームで適切な形式。 このトピックでは、型定義、メンバーの定義、および CLR 型またはメンバーの属性の設定のベスト プラクティスについて説明します。  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>コンス トラクター パターンと XAML の種類の定義  
 Xaml オブジェクト要素としてインスタンス化されるカスタム クラスは、次の要件を満たす必要があります。  
  
-   カスタムのクラスは、パブリックである必要があり、既定 (パラメーターなし) のコンス トラクターを公開する必要があります。 (次の構造に関する注意事項のセクションを参照してください)。  
  
-   カスタム クラスでは、入れ子になったクラスをすることはできません。 余分な氏名パスで「ドット」名前空間のクラス除算、あいまいになりアタッチされるプロパティなどの他の XAML 機能に干渉します。  
  
 オブジェクトは、オブジェクト要素としてインスタンス化することができます、作成したオブジェクトは、その基になる型としてオブジェクトを使用する任意のプロパティのプロパティ要素の形式を入力できます。  
  
 引き続き、値コンバーターを有効にした場合、オブジェクトの値をこれらの条件を満たしていない種類の指定できます。 詳細については、次を参照してください。[型コンバーターと XAML のマークアップ拡張機能](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)します。  
  
### <a name="structures"></a>構造体  
 CLR の定義によって、XAML で構築する構造体は、常にできます。 CLR コンパイラが暗黙的に構造体の既定のコンス トラクターを作成するためです。 このコンス トラクターでは、すべてのプロパティ値が既定値に初期化します。  
  
 場合によっては、構造体の既定の構築の動作は望ましくありません。 構造体は値と関数を共用体として概念的に入力するためのものがあります。 共用体型として値を含んで、排他的な解釈し、したがって、そのプロパティは設定可能なします。 WPF ボキャブラリで、このような構造の例は<xref:System.Windows.GridLength>します。 このような構造は、値は、さまざまな解釈や構造体の値のモードを作成する文字列の規則を使用して、属性の形式で表すことができるように、型コンバーターを実装する必要があります。 構造体には、既定以外のコンス トラクターを使用してコード構築の同様の動作も公開する必要があります。  
  
### <a name="interfaces"></a>インターフェイス  
 インターフェイスは、基になる型のメンバーとして使用できます。 XAML 型システムでは、割り当て可能な一覧を確認し、値として指定されているオブジェクトをインターフェイスに割り当てできることが必要です。 方法インターフェイスの存在が必要、XAML の型として関連割り当て可能な型は、XAML の作成要件をサポートしている限りの概念はありません。  
  
### <a name="factory-methods"></a>ファクトリ メソッド  
 ファクトリ メソッドは、XAML 2009 の機能です。 これらは、オブジェクトが必要となる既定のコンス トラクター XAML 原則を変更します。 ファクトリ メソッドは、このトピックに記載されていません。 参照してください[X:factorymethod ディレクティブ](../../../docs/framework/xaml-services/x-factorymethod-directive.md)です。  
  
## <a name="enumerations"></a>列挙  
 列挙体では、XAML のネイティブな型変換動作があります。 XAML で指定された列挙定数の名前は、基になる列挙型に対して解決され、XAML オブジェクト ライターに、列挙値を返します。  
  
 XAML の列挙にスタイル フラグの使用状況をサポートしている<xref:System.FlagsAttribute>適用します。 詳細については、次を参照してください。 [XAML 構文の詳細](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)です。 ([XAML 構文の詳細](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)WPF ユーザーを対象に書き込まれますが、そのトピックの情報の大部分は、特定の実装のフレームワークに固有ではない xaml 関連します)。  
  
## <a name="member-definitions"></a>メンバーの定義  
 型は、XAML の使用方法のメンバーを定義できます。 その特定の種類が XAML で使用できない場合でも、XAML の使用可能なメンバーを定義する型のことができます。 これは、CLR の継承によって実現します。 メンバーを継承するいくつかの型の型としての XAML の使用方法をサポートしていると、メンバーの基になる型の XAML の使用方法をサポートまたはネイティブ XAML 構文の使用可能な限り、そのメンバーが XAML で使用します。  
  
### <a name="properties"></a>プロパティ  
 一般的な CLR を使用して、パブリックの CLR プロパティとしてプロパティを定義するかどうかは`get`と`set`アクセサー パターンと言語に応じた keywording、XAML 型システムが指定されたプロパティを適切な情報を持つメンバーとしてをレポートすることができます<xref:System.Xaml.XamlMember>プロパティなど<xref:System.Xaml.XamlMember.IsReadPublic%2A>と<xref:System.Xaml.XamlMember.IsWritePublic%2A>です。  
  
 特定のプロパティは、適用することで、テキスト構文を有効にできます<xref:System.ComponentModel.TypeConverterAttribute>です。 詳細については、次を参照してください。[型コンバーターと XAML のマークアップ拡張機能](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)します。  
  
 テキストの構文またはネイティブの XAML の変換がない場合、さらに、間接参照、マークアップ拡張機能の使用状況など、プロパティの型がない場合 (<xref:System.Xaml.XamlMember.TargetType%2A> xaml 型システム) を t を扱うことにより、XAML オブジェクト ライターにインスタンスを返すことがありますCLR 型とターゲット型です。  
  
 XAML 2009 を使用して場合[X:reference マークアップ拡張機能](../../../docs/framework/xaml-services/x-reference-markup-extension.md)値を指定する、前の考慮事項が満たされない場合も使用できます。 ただし、型定義の問題よりも使用状況に関する問題の詳細はします。  
  
### <a name="events"></a>イベント  
 XAML 型システムできますを持つメンバーとして、イベントを報告する場合は、パブリックの CLR イベントとイベントを定義する<xref:System.Xaml.XamlMember.IsEvent%2A>として`true`です。 .NET Framework XAML サービス機能のスコープ内にないため、イベント ハンドラーを配線これは、特定のフレームワークと実装に任されてです。  
  
### <a name="methods"></a>メソッド  
 メソッドのインライン コードは、既定の XAML 機能ではありません。 ほとんどの場合で直接参照しないメソッドのメンバー、XAML からして、XAML でのメソッドの役割は、特定の XAML パターンのサポートを提供するだけです。 [X:factorymethod ディレクティブ](../../../docs/framework/xaml-services/x-factorymethod-directive.md)は例外です。  
  
### <a name="fields"></a>フィールド  
 CLR のデザイン ガイドラインは、非静的フィールドを防止します。 静的フィールドは、静的フィールドの値にアクセスできますを通してのみ[X:static マークアップ拡張機能](../../../docs/framework/xaml-services/x-static-markup-extension.md); ここでは、何もありません用のフィールドを公開する CLR の定義の特別な[X:static](../../../docs/framework/xaml-services/x-static-markup-extension.md)の使用法。  
  
## <a name="attachable-members"></a>アタッチ可能なメンバー  
 アタッチ可能なメンバーは、XAML を定義する型のアクセサー メソッド パターンを通じて公開されます。 定義の型自体は、オブジェクトとして、XAML で使用する必要はありません。 実際には、一般的なパターンでは、ロールがあるサービス クラスを宣言する添付可能なメンバーを所有して、関連する動作を実装するだけ UI 表現などの他の関数は使用されません。 次のセクションでは、プレース ホルダーの*PropertyName*アタッチ可能なメンバーの名前を表します。 その名前を無効にする必要があります、 [XamlName の文法](../../../docs/framework/xaml-services/xamlname-grammar.md)です。  
  
 これらのパターンと型の他のメソッド間で名前の衝突の注意する必要があります。 いずれのパターンに一致するメンバーが存在する場合、として解釈できるアタッチ可能なメンバーの使用の経路、XAML プロセッサによって場合でもに設定することはありませんでした。  
  
#### <a name="the-getpropertyname-accessor"></a>GetPropertyName アクセサー  
 `Get`*PropertyName* アクセサーのシグネチャは次の形式にする必要があります。  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   `target` オブジェクトは、実装のより具体的な型として指定することができます。 これを使用するには、アタッチ可能なメンバーの使用状況のスコープを指定する意図したスコープ外の使用方法、XAML の解析エラーによって、表示された無効なキャスト例外がスローされます。 パラメーター名`target`、必須ではありませんが、名前は`target`ほとんどの実装では規約によってです。  
  
-   戻り値は、実装のより具体的な型として指定することができます。  
  
 サポートするために、<xref:System.ComponentModel.TypeConverter>添付可能なメンバーの属性の使用方法を有効になっているテキストの構文を適用<xref:System.ComponentModel.TypeConverterAttribute>を`Get` *PropertyName*アクセサー。 適用する、`get`の代わりに、`set`かもしれませんが直感; ただし、この規則は、概念をサポートできます読み取り専用添付可能なメンバーのシリアル化可能なこれはデザイナーのシナリオで役立ちます。  
  
#### <a name="the-setpropertyname-accessor"></a>SetPropertyName アクセサー  
 セットの署名*PropertyName*アクセサーを指定する必要があります。  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   `target`オブジェクトは、前のセクションで説明したのと同じロジックの結果、実装でより具体的な種類として指定できます。  
  
-   `value` オブジェクトは、実装のより具体的な型として指定することができます。  
  
 このメソッドの値は、XAML の使用方法、属性の形式で通常からの入力であることに注意してください。 属性の形式から必要があります、テキスト構文の値コンバーターのサポートと属性を`Get` *PropertyName*アクセサー。  
  
### <a name="attachable-member-stores"></a>アタッチ可能メンバー ストア  
 アクセサー メソッドは通常ありませんアタッチ可能なメンバーの値をオブジェクト グラフに配置するか、オブジェクト グラフの外部に値を取得し、シリアル化して、正しくする手段を提供するのに十分なです。 この機能を提供する、`target`上のアクセサーのシグネチャ内のオブジェクトの値を格納できる必要があります。 記憶域メカニズムは、メンバーは、アタッチ可能なメンバーがないメンバー リスト内のターゲットにアタッチ可能なアタッチ可能なメンバーの原則と一致する必要があります。 .NET framework XAML サービスは、実装手法で、アタッチ可能なメンバーを格納、Api を介して<xref:System.Xaml.IAttachedPropertyStore>と<xref:System.Xaml.AttachablePropertyServices>です。 <xref:System.Xaml.IAttachedPropertyStore> ストアの実装を検出する XAML ライターによって使用され、ある型に実装する必要があります、`target`アクセサー。 静的な<xref:System.Xaml.AttachablePropertyServices>Api は、アクセサーの本文内で使用され、アタッチ可能なメンバーを参照してください、<xref:System.Xaml.AttachableMemberIdentifier>です。  
  
## <a name="xaml-related-clr-attributes"></a>XAML 関連の CLR 属性  
 型、メンバー、およびアセンブリを正しく属性は、レポートには、.NET Framework XAML サービスの XAML 型システム情報を順に重要です。 これは、型に直接基づく .NET Framework XAML サービスの XAML リーダーと XAML ライターでは、XAML システムを使用する場合、または定義またはそれらの XAML リーダーと XAML ライターに基づいている XAML を使用してフレームワークを使用する場合。  
  
 カスタムの型の XAML サポート対象の各 XAML 関連の属性の一覧については、次を参照してください。[カスタム型およびライブラリの CLR 属性を XAML-Related](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)です。  
  
## <a name="usage"></a>使用法  
 カスタム型の使用方法は、マークアップの作成者がカスタム型を含むアセンブリと CLR 名前空間のプレフィックスをマップする必要がある必要があります。 このトピックでは、この手順が記載されていません。  
  
## <a name="access-level"></a>アクセス レベル  
 XAML をロードおよびを持つ型をインスタンス化する手段を提供する、`internal`アクセス レベル。 この機能を提供するは、ユーザー コードが独自の型を定義しても、同じユーザー コードのスコープの一部であるマークアップからこれらのクラスのインスタンスを作成できるようにします。  
  
 WPF の例は、ユーザー コードを定義するたびに、<xref:System.Windows.Controls.UserControl>はものでは、UI の動作をリファクターする方法としてをサポートするクラスを宣言することで暗黙的な可能性がある任意の拡張メカニズムの一部としてではなく`public`アクセス レベル。 このような<xref:System.Windows.Controls.UserControl>で宣言できる`internal`バッキング コードは、XAML の型として参照されている元の同じアセンブリにコンパイルされる場合にアクセスします。  
  
 完全な信頼で XAML をロードを使用してアプリケーションの<xref:System.Xaml.XamlObjectWriter>を持つクラスを読み込む`internal`アクセス レベルが常に有効にします。  
  
 アプリケーションで部分信頼で XAML をロードする場合を使用してアクセスのレベルの特性を制御できます、 <xref:System.Xaml.Permissions.XamlAccessLevel> API です。 また、(、WPF テンプレート システムなど) の遅延メカニズムできる必要がありますを任意のアクセス レベルのアクセス許可を反映してそれらを保持する最終的な実行時の評価です。これは処理内部的に渡すことによって、<xref:System.Xaml.Permissions.XamlAccessLevel>情報。  
  
### <a name="wpf-implementation"></a>WPF の実装  
 XAML の WPF モデルを使用して、部分信頼のアクセス、BAML が部分信頼で読み込まれると、アクセスに制限されます<xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A>BAML ソースであるアセンブリ。 WPF を使用して遅延、<xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType>アクセス レベルの情報を渡すためのメカニズムとして。  
  
 WPF XAML 用語では、*内部型*は、同じアセンブリも含まれており、参照元の XAML で定義されている型です。 アセンブリを意図的に省略された XAML 名前空間を介してこのような型をマップすることができます、マッピングの一部を =`xmlns:local="clr-namespace:WPFApplication1"`です。  BAML が内部の型を参照するかどうか、型がある`internal`アクセス レベル、これが生成されます、`GeneratedInternalTypeHelper`アセンブリのクラスです。 避けたい場合`GeneratedInternalTypeHelper`、いずれかを使用する必要がある`public`アクセス レベル、または必要があります別のアセンブリに関連するクラスを要素し、そのアセンブリが依存するようにします。  
  
## <a name="see-also"></a>関連項目  
 [カスタム型およびライブラリの XAML 関連の CLR 属性](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)  
 [XAML サービス](../../../docs/framework/xaml-services/index.md)
