---
title: "カスタム型およびライブラリの XAML 関連の CLR 属性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 9a445d7e730ecb743d5e4086ec682b12a7bf3ff9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>カスタム型およびライブラリの XAML 関連の CLR 属性
このトピックでは、.NET Framework XAML サービスによって定義されている共通言語ランタイム (CLR) の属性について説明します。 その他の CLR 属性、.NET Framework で定義されているアセンブリまたは型へのアプリケーションの XAML 関連のシナリオがあることについても説明します。 これらの CLR 属性を持つアセンブリ、型、またはメンバーの属性の型に関連する XAML 型システム情報を提供します。 情報は、直接、XAML ノード ストリームを処理するため、または専用の XAML リーダーと XAML ライターで、.NET Framework XAML サービスを使用する任意の XAML コンシューマーに提供されます。  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>XAML 関連のカスタム型とカスタム メンバーの CLR 属性  
 CLR 属性を使用するには、全体的な CLR を使用して、型を定義することは、それ以外の場合などの属性がご利用いただけません必要があります。 CLR を使用してバックアップの種類を定義する場合、.NET Framework XAML サービスの XAML ライターによって使用される既定の XAML スキーマ コンテキストはアセンブリのバックアップに対するリフレクションの CLR 属性を読み取ることができます。  
  
 次のセクションでは、カスタムの型またはカスタムのメンバーに適用可能な XAML 関連の属性について説明します。 XAML 型システムに関連する情報を CLR 属性ごとに通信します。 読み込みパスでは属性付きの情報は有効な XAML ノード ストリームでは、XAML リーダーに役立ちますか、または有効なオブジェクト グラフを生成する XAML ライターと役に立ちます。 ファイルのパス、XAML リーダーが XAML 型システム情報を再構成する有効な XAML ノード ストリームは、いずれかの属性情報または、シリアル化のヒントや XAML ライターは、またはその他の XAML コンシューマーの要件を宣言します。  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **適用されます:**クラス、プロパティ、または`get`アクセサー メンバー アタッチ可能なプロパティをサポートします。  
  
 **引数:**なし  
  
 <xref:System.Windows.Markup.AmbientAttribute>XAML でのアンビエント プロパティという概念に基づいて解釈する必要があります、プロパティ、または属性付きの型を受け取るすべてのプロパティを示します。 アンビエントの概念は XAML プロセッサがメンバーの型の所有者を確認する方法と関連します。 アンビエント プロパティは、イミディ エイトの XAML ノードが作成されている設定の一般的な型メンバーの参照が中断されているが、オブジェクト グラフを作成するときにパーサー コンテキストで使用できる値が予期されるときのプロパティです。  
  
 アンビエントの概念は、アタッチ可能なメンバーは、CLR 属性の定義の観点からのプロパティとしては表されないに適用できる<xref:System.AttributeTargets>です。 のみの場合、メソッドの属性の使用を適用する必要があります、 `get` XAML のアタッチの使用をサポートするアクセサー。  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **適用されます:**クラス  
  
 **引数:**コンス トラクターの 1 つの引数に一致するプロパティの名前を指定する文字列。  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute>既定以外のコンス トラクター構文を使用してオブジェクトを初期化できることと、指定した名前のプロパティが構造情報を提供することを指定します。 この情報は主に XAML シリアル化用です。 詳細については、「<xref:System.Windows.Markup.ConstructorArgumentAttribute>」を参照してください。  
  
### <a name="contentpropertyattribute"></a>Contentpropertyattribute があります。  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **適用されます:**クラス  
  
 **引数:**属性付く型のメンバーの名前を指定する文字列。  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute>引数で指定された名前のプロパティがその型の XAML コンテンツ プロパティとして使用する必要があることを示します。 XAML コンテンツ プロパティ定義を定義する型に割り当てることができるすべての派生型を継承します。 適用することで特定の派生型の定義をオーバーライドできます<xref:System.Windows.Markup.ContentPropertyAttribute>特定の型を派生します。  
  
 XAML コンテンツ プロパティとして機能するプロパティに、XAML の使用方法のプロパティ要素のプロパティのタグ付けを省略できます。 通常、モデルのコンテンツや含有関係の簡素化された XAML マークアップを促進する XAML のコンテンツ プロパティを指定します。 1 つのメンバーは、XAML コンテンツ プロパティとして指定することができます、ために、いくつかのコンテナーのに関しては、XAML コンテンツ プロパティとして型のプロパティを指定するようにする設計の選択肢がある場合があります。 その他のコンテナーのプロパティは、明示的なプロパティ要素で使用する必要があります。  
  
 XAML ノード ストリームで XAML コンテンツ プロパティでも発生する可能性`StartMember`と`EndMember`のプロパティの名前を使用して、ノード、<xref:System.Xaml.XamlMember>です。 メンバーが XAML コンテンツ プロパティであるかどうかを確認するのには、確認、<xref:System.Xaml.XamlType>値から、`StartObject`を配置し、値を取得する<xref:System.Xaml.XamlType.ContentProperty%2A>です。  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **適用されます:**クラス、具体的にはコレクション型。  
  
 **引数:** A<xref:System.Type>外部コンテンツのコンテンツ ラッパー型として使用する型を指定します。  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute>外部コンテンツをラップするために使用される関連するコレクション型の 1 つまたは複数の種類を指定します。 外部コンテンツをコンテンツのプロパティの型の型システムの制約をキャプチャしません所有している型の XAML の使用方法をサポートするコンテンツ ケースのすべてのケースを指します。 XAML での特定の種類のコンテンツは厳密に型指定されたジェネリック型の文字列をサポートする場合がありますのサポートなど、<xref:System.Collections.ObjectModel.Collection%601>です。 コンテンツ ラッパーは、移行するテキストに関連するコンテンツのモデルなどのコレクションの値を割り当てることができるの XAML の概念に既存のマークアップ規則を移行するのに役立ちます。  
  
 1 つ以上のコンテンツ ラッパー型を指定するには、複数回、属性を適用します。  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **適用されます:**プロパティ  
  
 **引数:**属性付く型の別のメンバーの名前を指定する文字列。  
  
 <xref:System.Windows.Markup.DependsOnAttribute>属性付きのプロパティが別のプロパティの値に依存することを示します。 この属性をプロパティ定義に適用する XAML オブジェクトの記述に依存するプロパティが最初に処理されることを確認します。 使用状況<xref:System.Windows.Markup.DependsOnAttribute>解析の特定の順序を有効なオブジェクトの作成に従う必要がありますの種類のプロパティの例外的なケースを指定します。  
  
 複数を適用する<xref:System.Windows.Markup.DependsOnAttribute>プロパティが定義する場合。  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **適用されます:**できると予想される、クラス、<xref:System.Windows.Markup.MarkupExtension>派生型です。  
  
 **引数:** A<xref:System.Type>として期待する最も正確な型を指定する、`ProvideValue`属性の結果<xref:System.Windows.Markup.MarkupExtension>です。  
  
 詳細については、次を参照してください。 [XAML の概要のマークアップ拡張機能](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)します。  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **適用されます:**クラス  
  
 **引数:**属性の 2 つの形式をサポートしています。  
  
-   属性付く型のプロパティの名前を指定する文字列。  
  
-   プロパティの名前を指定する文字列と<xref:System.Type>名前付きのプロパティを定義する型。 フォームは、XAML 名前スコープのプロパティとしてアタッチ可能なメンバーを指定するためです。  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute>属性付きクラスの XAML 名前スコープの値を提供するプロパティを指定します。 XAML 名前スコープのプロパティを実装するオブジェクトを参照する必要は<xref:System.Windows.Markup.INameScope>実際の XAML 名前スコープ、そのストア、およびその動作を保持します。  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **適用されます:**クラス  
  
 **引数:**属性付く型を実行時の name プロパティの名前を指定する文字列。  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>XAML にマップされる属性付く型のプロパティをレポート[X:name ディレクティブ](../../../docs/framework/xaml-services/x-name-directive.md)です。 プロパティは、型でなければなりません<xref:System.String>読み取り/書き込みをする必要があります。  
  
 定義を定義する型に割り当てることができるすべての派生型を継承します。 適用することで特定の派生型の定義をオーバーライドできます<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>特定の型を派生します。  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **適用されます:**型  
  
 **引数:**なし。  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>空白の重要なコンテンツ内の子要素として表示される特定の種類に適用される (を持つコレクションで保持されているコンテンツ<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>)。 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>主に、保存パスが利用できる、読み込みパスで XAML 型システムで確認するには<xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>します。 詳細については、次を参照してください。 [XAML での空白の処理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)です。  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **リファレンス ドキュメント。**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **適用されます:**クラス、プロパティ、メソッド (だけ有効では XAML のメソッドの場合は、`get`アタッチ可能なメンバーをサポートするアクセサー)。  
  
 **引数:** 、<xref:System.Type>の<xref:System.ComponentModel.TypeConverter>です。  
  
 <xref:System.ComponentModel.TypeConverterAttribute>XAML でコンテキストを参照して、カスタム<xref:System.ComponentModel.TypeConverter>です。 これは、<xref:System.ComponentModel.TypeConverter>カスタム型、またはその型のメンバーの型変換動作を提供します。  
  
 適用する、<xref:System.ComponentModel.TypeConverterAttribute>属性を型、型コンバーターの実装を参照します。 クラス、構造体、またはインターフェイスに、XAML の型コンバーターを定義できます。 変換がネイティブで有効になっている、列挙体の型の変換を提供する必要はありません。  
  
 型コンバーターを目的の型に属性またはマークアップでは、初期化のテキストに使用される文字列に変換することがあります。 詳細については、次を参照してください。 [TypeConverters と XAML](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)です。  
  
 型のすべての値に適用するではなくに、特定のプロパティで XAML の型コンバーターの動作を確立することもできます。 この場合は、適用<xref:System.ComponentModel.TypeConverterAttribute>プロパティ定義 (外側の定義、固有ではない`get`と`set`定義) です。  
  
 型コンバーターの XAML 使用量は、カスタムのアタッチ可能なメンバーの動作を適用することで割り当てることができる<xref:System.ComponentModel.TypeConverterAttribute>を`get`XAML の使用方法をサポートするメソッドのアクセサー。  
  
 ような<xref:System.ComponentModel.TypeConverter>、 <xref:System.ComponentModel.TypeConverterAttribute> XAML が存在する前に .NET Framework が存在し、型コンバーターのモデルは、他の目的を提供します。 参照および使用するために<xref:System.ComponentModel.TypeConverterAttribute>、するには、完全に修飾するか、`using`の声明<xref:System.ComponentModel>です。 システム アセンブリは、プロジェクトにも含める必要があります。  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **適用されます:**クラス  
  
 **引数:**名前によって、関連するプロパティを参照する文字列。  
  
 エイリアスを表すクラスの CLR プロパティを示す、 [X:uid Directive](../../../docs/framework/xaml-services/x-uid-directive.md)です。  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **適用されます:**クラス  
  
 **引数:**ブール値。 属性の使用目的に使用される場合この常に指定してください`true`です。  
  
 この型が XAML オブジェクト グラフの作成中に上から下に組み込まれるかどうかを示します。 これは、プログラミング モデルの定義に関連性が高い可能性があります、高度な概念です。 詳細については、「<xref:System.Windows.Markup.UsableDuringInitializationAttribute>」を参照してください。  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **適用されます:**クラス、プロパティ、メソッド (だけ有効では XAML のメソッドの場合は、`get`アタッチ可能なメンバーをサポートするアクセサー)。  
  
 **引数:** A<xref:System.Type>属性付きの型のすべてのプロパティをシリアル化するときに使用するには、値シリアライザー サポート クラスを指定するか、属性付きプロパティを特定します。  
  
 <xref:System.Windows.Markup.ValueSerializer>詳細の状態とよりコンテキストが必要な値のシリアル化クラスを指定、<xref:System.ComponentModel.TypeConverter>はします。 <xref:System.Windows.Markup.ValueSerializer>適用することで、アタッチ可能なメンバーを関連付けることができます、<xref:System.Windows.Markup.ValueSerializerAttribute>属性、静的に`get`アタッチ可能なメンバーのアクセサー メソッドです。 値のシリアル化は適用も列挙体、インターフェイス、および構造体、のではなくデリゲート。  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **適用されます:**クラス、具体的にはオブジェクト要素の周囲の空白文字を表す UI での大幅なあります混合のコンテンツをホストするとして予想されるコレクション型。  
  
 **引数:**なし。  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>コレクション型を有意な空白として、コレクション内の XAML ノード ストリームの値ノードの構築に影響する、XAML プロセッサで処理する必要があることを示します。 詳細については、次を参照してください。 [XAML での空白の処理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)です。  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **適用されます:**クラス、プロパティです。  
  
 **引数:**型を文字列としてのフォームまたはとして型をサポートする 2 つの属性<xref:System.Type>です。 「<xref:System.Windows.Markup.XamlDeferLoadAttribute>」を参照してください。  
  
 示しますクラスやプロパティ (など、テンプレートの動作)、XAML の遅延読み込みの使用状況がレポートを遅延の動作とその宛先/コンテンツ タイプを有効にするクラス。  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **適用されます:**クラス  
  
 **引数:**コールバックの名前します。  
  
 クラスが、マークアップ拡張機能を使用して、そのプロパティの 1 つ以上の値を指定することができます、XAML ライターが、クラスの任意のプロパティでマークアップ拡張機能のセットの操作を実行する前に呼び出す必要がありますハンドラーを参照ことを示します。  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **適用されます:**クラス  
  
 **引数:**コールバックの名前します。  
  
 クラスが、そのプロパティの 1 つ以上の値を指定する型コンバーターを使用できる XAML ライターが、クラスの任意のプロパティの型コンバーター設定操作を実行する前に呼び出す必要がありますハンドラーを参照ことを示します。  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **適用されます:**クラス  
  
 **引数:**エイリアスを使用するプロパティの名前を指定する文字列`xml:lang`属性付く型にします。  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute>XML にマップされる属性付く型のプロパティをレポート`lang`ディレクティブです。 プロパティが必ずしも型の<xref:System.String>、する必要があります (これを実現する、プロパティの型、または特定のプロパティを使用して実行する型コンバーターを関連付けることによって) 文字列から割り当てることができます。 プロパティには、読み取り/書き込みをする必要があります。  
  
 マッピングのシナリオは`xml:lang`は具体的には、XMLDOM を処理することがなく、ランタイム オブジェクト モデルに XML が指定した言語情報へのアクセスを持つようにします。  
  
 定義を定義する型に割り当てることができるすべての派生型を継承します。 適用することで特定の派生型の定義をオーバーライドできます<xref:System.Windows.Markup.XmlLangPropertyAttribute>特定の派生型、れていますが、一般的ではないシナリオです。  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>アセンブリ レベルで XAML 関連の CLR 属性  
 次のセクションでは、型またはメンバーの定義には適用されませんが、代わりに、アセンブリに適用されている XAML 関連の属性について説明します。 これらの属性は、XAML で使用するカスタムの型を含むライブラリを定義する全体的なゴールに当てはまります。 一部の属性には影響を与える、XAML ノード ストリームを直接が、他のコンシューマーを使用する、ノード ストリームで受け渡されます。 情報のコンシューマーには、デザイン環境や XAML 名前空間情報を必要としてプレフィックス情報が関連付けられているシリアル化プロセスが含まれます。 XAML スキーマ コンテキスト (.NET Framework XAML サービスの既定値を含む) もには、この情報が使用されます。  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **引数:**  
  
-   包含する XAML 名前空間の識別子を指定する文字列。  
  
-   XAML 名前空間を前の引数から包含できる XAML 名前空間の識別子を指定する文字列。  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>XAML 名前空間を別の XAML 名前空間によって包括できることを指定します。 通常は、包含の XAML 名前空間が示されている、あらかじめ定義したで<xref:System.Windows.Markup.XmlnsDefinitionAttribute>です。 この方法は、以前のバージョン管理されたボキャブラリに対して以前に定義されたマークアップとの互換性には、ライブラリ内の XAML ボキャブラリをバージョン管理に使用します。  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **引数:**  
  
-   定義する XAML 名前空間の識別子を指定する文字列。  
  
-   CLR 名前空間の名前を示す文字列。 CLR 名前空間は、アセンブリ内のパブリック型を定義する必要がありますあり、少なくとも 1 つの CLR 名前空間の種類は XAML の使用方法に使用する必要があります。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>XAML 名前空間と CLR 名前空間は、型の解決で使用した XAML オブジェクト ライターまたは XAML スキーマ コンテキストの間でアセンブリごとの単位でのマッピングを指定します。  
  
 1 つ以上<xref:System.Windows.Markup.XmlnsDefinitionAttribute>アセンブリに適用できます。 これは、次の理由の任意の組み合わせに対して実行する可能性があります。  
  
-   ライブラリ デザインには、ランタイム API アクセス; の論理組織用の複数の CLR 名前空間が含まれています。ただし、XAML で使用できるように、同じ XAML 名前空間を参照することでそれらの名前空間内のすべての型が必要です。 この場合は、いくつか適用<xref:System.Windows.Markup.XmlnsDefinitionAttribute>属性を使用して同じ<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>値しますが、異なる<xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A>値。 これは、フレームワークまたはアプリケーションは、一般的な使用方法の既定の XAML 名前空間を意図している XAML 名前空間のマッピングを定義している場合に特に便利です。  
  
-   ライブラリ デザインには、複数の CLR 名前空間が含まれ、その CLR 名前空間の型の使用状況の間で意図的な XAML 名前空間の分離をたいとします。  
  
-   アセンブリの CLR 名前空間を定義して 1 つ以上の XAML 名前空間を介してアクセスできるようにします。 このシナリオでは、同じコードベースで複数のボキャブラリをサポートしているときに発生します。  
  
-   1 つまたは複数の CLR 名前空間では、XAML 言語サポートを定義します。 これらの場合、<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>値でなければなりません`http://schemas.microsoft.com/winfx/2006/xaml`です。  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **引数:**  
  
-   XAML 名前空間の識別子を指定する文字列。  
  
-   推奨されるプレフィックスを指定する文字列。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>XAML 名前空間を使用する推奨されるプレフィックスを指定します。 プレフィックスは、.NET Framework XAML サービスによってシリアル化される XAML ファイルで要素と属性を記述するときに便利です<xref:System.Xaml.XamlXmlWriter>、または XAML 実装のライブラリが XAML を持つデザイン環境とやり取りするときに編集機能。  
  
 1 つ以上<xref:System.Windows.Markup.XmlnsPrefixAttribute>アセンブリに適用できます。 これは、次の理由の任意の組み合わせに対して実行する可能性があります。  
  
-   アセンブリでは、1 つ以上の XAML 名前空間の型を定義します。 ここでは XAML 名前空間ごとに値を別のプレフィックスを定義する必要があります。  
  
-   複数のボキャブラリをサポートしているし、ボキャブラリおよび XAML 名前空間ごとに異なるプレフィックスを使用します。  
  
-   アセンブリの XAML 言語サポートを定義している、<xref:System.Windows.Markup.XmlnsDefinitionAttribute>の`http://schemas.microsoft.com/winfx/2006/xaml`します。 ここでは、通常は昇格するプレフィックス`x`です。  
  
> [!NOTE]
>  .NET framework XAML サービスは、XAML 関連の属性も定義<xref:System.Windows.Markup.RootNamespaceAttribute>です。 この属性は、プロジェクト システムのサポートのアセンブリ レベル属性と、XAML のカスタム型には無効です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Attribute>  
 [.NET Framework XAML サービスで使用するためのカスタム型の定義](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
