---
title: "XAML-Related CLR Attributes for Custom Types and Libraries | Microsoft Docs"
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
  - "CLR attributes for custom types [XAML Services]"
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
caps.latest.revision: 8
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 8
---
# XAML-Related CLR Attributes for Custom Types and Libraries
このトピックでは、.NET Framework XAML サービスによって定義される共通言語ランタイム \(CLR: Common Language Runtime\) 属性について説明します。  また、アセンブリまたは型に適用される XAML 関連のシナリオを持つ、.NET Framework で定義されるその他の CLR 属性についても説明します。  アセンブリ、型、およびメンバーに対して、このような CLR 属性を設定すると、型に関連する XAML 型システム情報が提供されます。  情報は、XAML ノード ストリームの直接処理または専用の XAML リーダーおよび XAML ライターによる処理を目的として .NET Framework XAML サービスを使用する、すべての XAML コンシューマーに提供されます。  
  
## カスタム型とカスタム メンバー用の XAML 関連の CLR 属性  
 CLR 属性を使用すると、CLR 全般を使用して型を定義することになります。それ以外の場合は、CLR 属性は使用できません。  CLR を使用して型バッキングを定義した場合、.NET Framework XAML サービスの XAML ライターによって使用される既定の XAML スキーマ コンテキストは、バッキング アセンブリに対するリフレクションを介して CLR 属性を読み取ることができるようになります。  
  
 以降では、カスタム型およびカスタム メンバーに適用できる XAML 関連の属性について説明します。  各 CLR 属性は、XAML 型システムに関連する情報をやり取りします。  読み込みパスでは、属性付きの情報に基づいて、XAML リーダーが有効な XAML ノード ストリームを形成する場合と、XAML ライターが有効なオブジェクト グラフを生成する場合があります。  保存パスでは、属性付きの情報に基づいて、XAML リーダーが有効な XAML ノード ストリームを形成して XAML 型システム情報を再構築する場合と、XAML ライターやその他の XAML コンシューマーに対するシリアル化のヒントおよび要件が宣言される場合があります。  
  
### AmbientAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **対象:** クラス、プロパティ、またはアタッチ可能なプロパティをサポートする `get` アクセサー メンバー。  
  
 **引数:** なし  
  
 <xref:System.Windows.Markup.AmbientAttribute> は、プロパティ \(属性付き型を受け取るすべてのプロパティ\) は XAML のアンビエント プロパティの概念に基づいて解釈する必要があることを示します。  アンビエントの概念は XAML プロセッサがメンバーの型の所有者を確認する方法と関連します。  アンビエント プロパティは、オブジェクト グラフの作成時にパーサー コンテキストで値を使用できるという想定のプロパティです。ただし、XAML ノード セットを迅速に作成するために、通常の型メンバーの検索は中断されます。  
  
 アンビエントの概念は、CLR 属性で <xref:System.AttributeTargets> を定義する方法に関してプロパティとして表現されない、アタッチ可能なメンバーに適用できます。  メソッド属性の使用は、`get` アクセサーが XAML のアタッチ可能な使用方法をサポートするケースのみに限定する必要があります。  
  
### ConstructorArgumentAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **対象:** クラス  
  
 **引数:** 単一のコンストラクター引数と照合されるプロパティ名を指定する文字列。  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute> は、既定以外のコンストラクター構文を使用してオブジェクトを初期化できることと、指定された名前のプロパティが構造情報を提供することを指定します。  この情報は、主に XAML のシリアル化に使用されます。  詳細については、「<xref:System.Windows.Markup.ConstructorArgumentAttribute>」を参照してください。  
  
### ContentPropertyAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **対象:** クラス  
  
 **引数:** 属性付き型のメンバー名を指定する文字列。  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute> は、引数によって名前が指定されたプロパティはその型の XAML コンテンツ プロパティとして機能する必要があることを示します。  XAML コンテンツ プロパティ定義は、定義元の型に割り当て可能なすべての派生型に継承されます。  特定の派生型の定義を無視するには、<xref:System.Windows.Markup.ContentPropertyAttribute> を特定の派生型に適用します。  
  
 XAML コンテンツ プロパティとして機能するプロパティの場合、そのプロパティのプロパティ要素に対するタグ付けは XAML の使用方法では省略できます。  通常は、XAML コンテンツ プロパティを指定して、コンテンツおよびコンテインメント モデルの XAML マークアップを簡略化します。  XAML コンテンツ プロパティとして指定できるのは単一のメンバーのみに限定されるので、場合によっては、XAML コンテンツ プロパティとして指定する必要がある、型のいくつかのコンテナー プロパティの種類に関して、デザインを選択することになります。  その他のコンテナー プロパティは、明示的なプロパティ要素と共に使用する必要があります。  
  
 XAML ノード ストリームでは、XAML コンテンツ プロパティは <xref:System.Xaml.XamlMember> のプロパティ名に基づいて `StartMember` ノードと `EndMember` ノードを生成します。  メンバーが XAML コンテンツ プロパティであるかどうか判断するには、`StartObject` の位置から <xref:System.Xaml.XamlType> 値を調べ、<xref:System.Xaml.XamlType.ContentProperty%2A> の値を取得します。  
  
### ContentWrapperAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **対象:** クラス \(特にコレクション型\)。  
  
 **引数:** 外部コンテンツ用のコンテンツ ラッパー型として使用する型を指定する <xref:System.Type>。  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute> は、外部コンテンツをラップするために使用される関連するコレクション型に対して 1 つ以上の型を指定します。  外部コンテンツは、コンテンツ プロパティの型に対する型システムの制約で、所有する型の XAML 使用方法でサポートされるコンテンツ ケースの一部がキャプチャされないケースを指します。  たとえば、XAML は、厳密に型指定されたジェネリック <xref:System.Collections.ObjectModel.Collection%601> で文字列をサポートする可能性がある、特定の型のコンテンツをサポートします。  コンテンツ ラッパーは、テキスト関連のコンテンツ モデルの移行など、既存のマークアップ規則を、コレクションの割り当て可能な値に関する XAML の概念に移行する場合に役立ちます。  
  
 複数のコンテンツ ラッパー型を指定するには、属性を複数回適用します。  
  
### DependsOnAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **対象:** プロパティ  
  
 **引数:** 属性付き型の別のメンバー名を指定する文字列。  
  
 <xref:System.Windows.Markup.DependsOnAttribute> は、属性付きプロパティが別のプロパティの値に依存することを示します。  この属性をプロパティ定義に適用すると、依存プロパティは XAML オブジェクトの記述で最初に処理されます。  <xref:System.Windows.Markup.DependsOnAttribute> の使用により、例外的なケースを指定して、有効なオブジェクトを作成するために特定の順序で解析を行う必要がある型のプロパティに対応します。  
  
 プロパティ定義に対して複数の <xref:System.Windows.Markup.DependsOnAttribute> ケースを適用できます。  
  
### MarkupExtensionReturnTypeAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **対象:** <xref:System.Windows.Markup.MarkupExtension> 派生型であると想定されるクラス。  
  
 **引数:** 属性付きの <xref:System.Windows.Markup.MarkupExtension> の `ProvideValue` の結果として想定される最も精密な型を指定する <xref:System.Type>。  
  
 詳細については、「[Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)」を参照してください。  
  
### NameScopePropertyAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **対象:** クラス  
  
 **引数:** 次の 2 つの形式の属性をサポートします。  
  
-   属性付き型のプロパティ名を指定する文字列  
  
-   プロパティ名を指定する文字列、および名前付きプロパティを定義する型の <xref:System.Type> この形式では、XAML 名前スコープ プロパティとしてアタッチ可能なメンバーを指定します。  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute> は、属性付きクラスに XAML 名前スコープの値を提供するプロパティを指定します。  XAML 名前スコープのプロパティは、<xref:System.Windows.Markup.INameScope> を実装し、実際の XAML 名前スコープ、そのストア、およびその動作を保持するオブジェクトを参照すると想定されます。  
  
### RuntimeNamePropertyAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **対象:** クラス  
  
 **引数:** 属性付き型のランタイム名のプロパティ名を指定する文字列。  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> は、XAML の [x:Name Directive](../../../docs/framework/xaml-services/x-name-directive.md) にマップされる属性付き型のプロパティを報告します。  このプロパティは <xref:System.String> 型であると同時に、読み書き可能である必要があります。  
  
 この定義は、定義元の型に割り当て可能なすべての派生型に継承されます。  特定の派生型の定義を無視するには、<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> を特定の派生型に適用します。  
  
### TrimSurroundingWhitespaceAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **対象:** 型  
  
 **引数:** なし。  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> は、空白が意味を持つコンテンツ \(<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> を含むコレクションによって保持されるコンテンツ\) 内で子要素として表される可能性がある特定の型に適用されます。  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> は主に保存パスに関連しますが、<xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=fullName> を調べることで、読み込みパスの XAML 型システムでも使用できます。  詳細については、「[Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)」を参照してください。  
  
### TypeConverterAttribute  
 **リファレンス ドキュメント:**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **対象:** クラス、プロパティ、メソッド \(XAML 対応の唯一のメソッド ケースは、アタッチ可能なメンバーをサポートする `get` アクセサー\)。  
  
 **引数:** <xref:System.ComponentModel.TypeConverter> の <xref:System.Type>。  
  
 XAML コンテキストの <xref:System.ComponentModel.TypeConverterAttribute> は、カスタム <xref:System.ComponentModel.TypeConverter> を参照します。  この <xref:System.ComponentModel.TypeConverter> は、カスタム型 \(その型のメンバー\) の型変換動作を提供します。  
  
 型コンバーターの実装を参照し、<xref:System.ComponentModel.TypeConverterAttribute> 属性を型に適用します。  クラス、構造体、およびインターフェイスに対して、XAML の型コンバーターを定義できます。  列挙体に対しては、型変換がネイティブで有効になっているため、型変換を提供する必要はありません。  
  
 型コンバーターは、マークアップで属性または初期化テキストに使用される文字列を目的の型に変換できる必要があります。  詳細については、「[TypeConverters および XAML](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)」を参照してください。  
  
 XAML の型コンバーターの動作は、型のすべての値を適用する代わりに、特定のプロパティを対象にすることもできます。  このケースでは、<xref:System.ComponentModel.TypeConverterAttribute> をプロパティ定義 \(特定の `get` および `set` 定義以外の定義\) に適用します。  
  
 アタッチ可能なカスタム メンバーの XAML の使用に対応する型コンバーターの動作を割り当てるには、XAML の使用をサポートする `get` メソッド アクセサーに <xref:System.ComponentModel.TypeConverterAttribute> を割り当てます。  
  
 <xref:System.ComponentModel.TypeConverter> と同様に、<xref:System.ComponentModel.TypeConverterAttribute> は XAML よりも前に .NET Framework に存在しており、型コンバーター モデルはその他の目的に対応していました。  <xref:System.ComponentModel.TypeConverterAttribute> を参照して使用するには、完全修飾するか、<xref:System.ComponentModel> に `using` ステートメントを指定します。  システム アセンブリをプロジェクトに含める必要もあります。  
  
### UidPropertyAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **対象:** クラス  
  
 **引数:** 関連プロパティを名前で参照する文字列。  
  
 [x:Uid Directive](../../../docs/framework/xaml-services/x-uid-directive.md) をエイリアス化するクラスの CLR プロパティを示します。  
  
### UsableDuringInitializationAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **対象:** クラス  
  
 **引数:** ブール値。  属性の用途で使用する場合、常に `true` として指定する必要があります。  
  
 XAML のオブジェクト グラフの作成中にこの型がトップダウンで構築されるかどうかを示します。  これは高度な概念であり、実際のプログラミング モデルの定義に密接に関連していると考えられます。  詳細については、「<xref:System.Windows.Markup.UsableDuringInitializationAttribute>」を参照してください。  
  
### ValueSerializerAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **対象:** クラス、プロパティ、メソッド \(XAML 対応の唯一のメソッド ケースは、アタッチ可能なメンバーをサポートする `get` アクセサー\)。  
  
 **引数:** 属性付き型のプロパティ \(特定の属性付きプロパティ\) をすべてシリアル化する場合に使用する値のシリアライザーのサポート クラスを指定する <xref:System.Type>。  
  
 <xref:System.Windows.Markup.ValueSerializer> は、<xref:System.ComponentModel.TypeConverter> よりも状態とコンテキストを必要とする値のシリアル化クラスを指定します。  アタッチ可能なメンバーの静的な `get` アクセサー メソッド上で <xref:System.Windows.Markup.ValueSerializerAttribute> 属性を適用することにより、アタッチ可能なメンバーに <xref:System.Windows.Markup.ValueSerializer> を関連付けることができます。  値のシリアル化は、列挙体、インターフェイス、および構造体に対しても適用できますが、デリゲートには適用できません。  
  
### WhitespaceSignificantCollectionAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **対象:** クラス \(特に、オブジェクト要素周辺の空白が UI 表現で意味を持つ、混合コンテンツをホストする想定のコレクション型\)  
  
 **引数:** なし。  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> は、コレクション内で XAML ノード ストリームの値ノードの作成に影響を及ぼすため、XAML プロセッサで空白が意味を持つものとしてコレクション型を処理する必要があることを示します。  詳細については、「[Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)」を参照してください。  
  
### XamlDeferLoadAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **対象:** クラス、プロパティ。  
  
 **引数:** 文字列として 2 つの属性フォーム型、または <xref:System.Type> の型をサポートします。  「<xref:System.Windows.Markup.XamlDeferLoadAttribute>」を参照してください。  
  
 クラスまたはプロパティに XAML の遅延読み込みの使用 \(テンプレート動作など\) が含まれていることを示し、遅延動作を有効にするクラスと、その宛先\/コンテンツ タイプを報告します。  
  
### XamlSetMarkupExtensionAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **対象:** クラス  
  
 **引数:** コールバックの名前を指定します。  
  
 クラスでマークアップ拡張機能を使用して 1 つ以上のプロパティの値を指定できることを示すと同時に、クラスの任意のプロパティに対してマークアップ拡張機能のセット操作を実行する前に XAML ライターから呼び出す必要のあるハンドラーを参照します。  
  
### XamlSetTypeConverterAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **対象:** クラス  
  
 **引数:** コールバックの名前を指定します。  
  
 クラスで型コンバーターを使用して 1 つ以上のプロパティの値を指定できることを示すと同時に、クラスの任意のプロパティに対して型コンバーターのセット操作を実行する前に XAML ライターから呼び出す必要のあるハンドラーを参照します。  
  
### XmlLangPropertyAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **対象:** クラス  
  
 **引数:** 属性付き型の `xml:lang` にエイリアス化するプロパティ名を指定する文字列。  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute> は、XML の `lang` ディレクティブにマッピングされる属性付き型のプロパティを報告します。  このプロパティは必ずしも <xref:System.String> 型である必要はありませんが、文字列からの割り当て \(具体的には、プロパティの型または特定のプロパティと型コンバーターの関連付け\) に対応する必要があります。  このプロパティは読み取り\/書き込み可能である必要があります。  
  
 `xml:lang` のマッピングに対応するシナリオでは、特に XMLDOM による処理を必要とせずに、ランタイム オブジェクト モデルが XML 固有の言語情報にアクセスできます。  
  
 この定義は、定義元の型に割り当て可能なすべての派生型に継承されます。  特定の派生型の定義を無視するには、<xref:System.Windows.Markup.XmlLangPropertyAttribute> を特定の派生型に適用します。ただし、これは一般的なシナリオではありません。  
  
## アセンブリ レベルでの XAML 関連の CLR 属性  
 以降では、型やメンバー定義に適用されずにアセンブリに適用される XAML 関連の属性について説明します。  各属性の全体としての目的は、XAML で使用するカスタム型を含むライブラリを定義することです。  一部の属性は XAML ノード ストリームに直接影響を及ぼすわけではありませんが、使用するその他のコンシューマー用にノード ストリームで受け渡されます。  情報のコンシューマーとしては、XAML 名前空間の情報および関連付けられたプレフィックス情報を必要とする、デザイン環境やシリアル化処理が挙げられます。  XAML スキーマ コンテキスト \(既定の .NET Framework XAML サービスを含む\) も、この情報を使用します。  
  
### XmlnsCompatibleWithAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **引数:**  
  
-   包含する XAML 名前空間の識別子を指定する文字列。  
  
-   前の引数から XAML 名前空間を包含できる XAML 名前空間の識別子を指定する文字列。  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> は、XAML 名前空間を別の XAML 名前空間で包含できることを指定します。  通常、XAML 名前空間の包含は、あらかじめ定義した <xref:System.Windows.Markup.XmlnsDefinitionAttribute> で示されます。  この方法は、ライブラリ内の XAML の語彙のバージョン管理を目的として使用され、以前のバージョンの語彙に対してあらかじめ定義したマークアップとの互換性を確保します。  
  
### XmlnsDefinitionAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **引数:**  
  
-   定義する XAML 名前空間の識別子を指定する文字列。  
  
-   CLR 名前空間の名前を付ける文字列。  CLR 名前空間がアセンブリのパブリック型を定義し、CLR 名前空間の型のうち少なくとも 1 つが XAML の使用方法で対象になる必要があります。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> は、XAML 名前空間と CLR 名前空間の間のアセンブリごとのマッピングを指定します。これは、XAML オブジェクト ライターまたは XAML スキーマ コンテキストによる型解決に使用されます。  
  
 アセンブリに対して、複数の <xref:System.Windows.Markup.XmlnsDefinitionAttribute> を適用できます。  この方法は、次の理由のいずれか、または組み合わせに基づいて使用されます。  
  
-   ランタイム API アクセスの論理構成に対応する複数の CLR 名前空間がライブラリ デザインに含まれるが、同じ XAML 名前空間を参照して各名前空間のすべての型を XAML で使用可能にする必要がある。  このケースでは、<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> 値は同じで <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> 値は異なる複数の <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 属性を適用します。  XAML 名前空間のマッピングを定義するときに、一般的な使用方法でフレームワークまたはアプリケーションが既定の XAML 名前空間になる想定である場合、この方法が役立ちます。  
  
-   複数の CLR 名前空間がライブラリ デザインに含まれ、各 CLR 名前空間での型の使用方法に応じて意図的に XAML 名前空間を分離する必要がある。  
  
-   アセンブリで CLR 名前空間を定義して、複数の XAML 名前空間からのアクセスを可能にする必要がある。  同じコードベースで複数の語彙をサポートしている場合に、このような必要性が生じます。  
  
-   1 つ以上の CLR 名前空間で XAML 言語サポートを定義する。  これらについては、<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> 値に `http://schemas.microsoft.com/winfx/2006/xaml` を指定する必要があります。  
  
### XmlnsPrefixAttribute  
 **リファレンス ドキュメント:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **引数:**  
  
-   XAML 名前空間の識別子を指定する文字列。  
  
-   推奨プレフィックスを指定する文字列。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> は、XAML 名前空間に使用する推奨プレフィックスを指定します。  .NET Framework XAML サービスの <xref:System.Xaml.XamlXmlWriter> によってシリアル化される XAML ファイルに要素および属性を書き込む場合や、XAML 実装ライブラリが XAML の編集機能を備えたデザイン環境とやり取りする場合に、このプレフィックスが役立ちます。  
  
 アセンブリに対して、複数の <xref:System.Windows.Markup.XmlnsPrefixAttribute> を適用できます。  この方法は、次の理由のいずれか、または組み合わせに基づいて使用されます。  
  
-   アセンブリで複数の XAML 名前空間の型を定義する。  このケースでは、XAML 名前空間ごとに異なるプレフィックス値を定義する必要があります。  
  
-   複数の語彙をサポートしている状況で、語彙および XAML 名前空間ごとに異なるプレフィックスを使用する。  
  
-   アセンブリで XAML 言語サポートを定義し、<xref:System.Windows.Markup.XmlnsDefinitionAttribute> に `http://schemas.microsoft.com/winfx/2006/xaml` を指定する。  このケースでは通常、プレフィックス `x` を昇格させる必要があります。  
  
> [!NOTE]
>  .NET Framework XAML サービスでは、XAML 関連の属性 <xref:System.Windows.Markup.RootNamespaceAttribute> も定義します。  これは、プロジェクト システム サポート用のアセンブリ レベルの属性であり、XAML のカスタム型には関連しません。  
  
## 参照  
 <xref:System.Attribute>   
 [Defining Custom Types for Use with .NET Framework XAML Services](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)