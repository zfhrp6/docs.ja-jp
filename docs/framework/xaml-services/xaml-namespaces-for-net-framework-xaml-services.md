---
title: ".NET Framework XAML サービス用の XAML 名前空間"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4e94f116fa820d80e5e23833c20382591c5d479
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>.NET Framework XAML サービス用の XAML 名前空間
XAML 名前空間は、XML 名前空間の定義を拡張する概念です。 XML 名前空間と同様に、定義することを使用して XAML 名前空間、`xmlns`マークアップ内の属性です。 XAML 名前空間も、XAML ノード ストリームとその他の XAML サービス Api で表記します。 このトピックでは、XAML 名前空間の概念を定義し、XAML 名前空間を定義できますおよび XAML スキーマ コンテキストおよびその他の .NET Framework XAML サービスで使用する方法について説明します。  
  
## <a name="xml-namespace-and-xaml-namespace"></a>XML Namespace と XAML Namespace  
 XAML 名前空間は、XAML は、マークアップの基本的な XML 形式を使用して、XML の特殊な形式と同様に特殊化された XML 名前空間です。 マークアップで XAML 名前空間とそのマッピングを宣言する、`xmlns`要素に適用される属性です。 `xmlns`で XAML 名前空間が宣言されている同じ要素宣言を行んだことができます。 要素に対する XAML 名前空間の宣言は、その要素をその要素のすべての属性とその要素の子をすべて有効です。 属性は、属性を格納する要素と同じ属性名自体マークアップでは、その属性名の一部として、プレフィックスを参照する限り、XAML 名前空間を使用できます。  
  
 XML 名前空間と XAML 名前空間の違いは、XML 名前空間は、スキーマの参照に使用される可能性がありますか、単にエンティティを区別するために使用される可能性がありますです。 Xaml をバッキング型、型とメンバーが XAML で使用されているを解決する必要があります最終的にこの機能にも XML スキーマの概念は適用されません。 XAML 名前空間には、XAML スキーマ コンテキストをこの型のマッピングを実行するために使用できる必要がある情報が含まれています。  
  
## <a name="xaml-namespace-components"></a>XAML Namespace コンポーネント  
 XAML 名前空間の定義が 2 つのコンポーネント: プレフィックス、および識別子。 これらの各コンポーネントは、XAML 名前空間が、マークアップで宣言または XAML 型システムで定義されている場合に存在します。  
  
 プレフィックス、任意の文字列で許可されるよう、 [XML 1.0 仕様の W3C 名前空間](http://go.microsoft.com/fwlink/?LinkID=161735)です。 規則では、プレフィックスは通常、非常に短い文字列のため、プレフィックスが標準的なマークアップ ファイルで何度も繰り返します。 複数の XAML 実装では使用を目的とした、特定の XAML 名前空間は、特定の従来のプレフィックスを使用します。 たとえば、XAML 言語の XAML 名前空間は、通常、マップ、プレフィックスを使用して`x`です。 既定の XAML 名前空間プレフィックスが定義には付与しませんが、定義されているか、脅かさ Framework XAML サービス API のクエリを実行する場合、空の文字列として表されるを定義することができます。 通常、既定の XAML 名前空間は、プレフィックス省略量の最大化を促進するために選択が意図的に、XAML 実装テクノロジおよびシナリオとボキャブラリをマークアップします。  
  
 識別子、任意の文字列で許可されるよう、 [XML 1.0 仕様の W3C 名前空間](http://go.microsoft.com/fwlink/?LinkID=161735)です。 規則では、XML 名前空間または XAML 名前空間のいずれかの識別子は多くの場合、通常与えられる URI 形式でプロトコルで修飾された絶対 URI として。 多くの場合、特定の XAML ボキャブラリを定義するバージョン情報はパス文字列の一部として暗黙的に指定します。 XAML 名前空間は、XML URI 表記を超える、追加の識別子の規則を追加します。 XAML 名前空間には、識別子は、その XAML 名前空間の下の要素として指定されている型を解決するために、またはメンバーに属性を解決するのには、XAML スキーマ コンテキストが必要な情報を通信します。  
  
 XAML スキーマ コンテキストに情報を通信用に、XAML 名前空間の識別子があります URI 形式でします。 ただし、ここでは、URI は宣言も特定のアセンブリまたはアセンブリのリストに一致する識別子として。 これは、アセンブリ内で属性を持つアセンブリ<xref:System.Windows.Markup.XmlnsDefinitionAttribute>です。 XAML 名前空間を特定し、属性付きアセンブリの CLR ベースの型の解決の動作をサポートするには、このメソッドは .NET Framework XAML サービスで既定の XAML スキーマ コンテキストをサポートします。 一般的には、この規則は、場合、XAML スキーマ コンテキストが CLR が組み込まれていますか、既定の XAML スキーマ コンテキスト、CLR アセンブリからの CLR 属性を読み取るために必要なに基づいて使用できます。  
  
 XAML 名前空間は、CLR 名前空間と型を定義するアセンブリを通信する規則によっても識別できます。 この規則でない場合に使用されます<xref:System.Windows.Markup.XmlnsDefinitionAttribute>属性が型を含むアセンブリに存在します。 この規則は、可能性のある URI 規則よりも複雑と、複数のアセンブリを参照する方法があるため重複除去、およびあいまいさが発生する可能性があります。  
  
 CLR 名前空間とアセンブリの規約を使用する識別子の最も基本的な形式は次のとおりです。  
  
 `clr-namespace:`*clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:`および`; assembly=`構文のリテラルのコンポーネントはインストールされています。  
  
 *clrnsName* CLR 名前空間を識別する文字列名を指定します。 この文字列の名前には、CLR 名前空間とその他の CLR 名前空間への関係についてのヒントを提供する内部ドット文字 (.) が含まれています。  
  
 *assemblyShortName* XAML 内で使用される型を定義するアセンブリの名前の文字列を指定します。 アセンブリによって定義されると宣言するのには具体的には指定された CLR 名前空間内で宣言されている XAML 名前空間を介してアクセスするために、型が許可される*clrnsName*です。 通常、この文字列の名前にはによって報告された情報は対応して<xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>です。  
  
 CLR 名前空間とアセンブリの規約のより完全な定義は次のとおりです。  
  
 `clr-namespace:`*clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName*として有効な任意の文字列を表す、<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>入力します。 この文字列は、カルチャ、公開キー、またはバージョン情報を含めることができます (これらの概念の定義のリファレンス トピックの「 <xref:System.Reflection.Assembly>). COFF 形式と証拠 (の他のオーバー ロードで使用される<xref:System.Reflection.Assembly.Load%2A>) 上の目的を読み込み XAML アセンブリでは無関係を文字列としてすべての読み込み情報が表示される必要があります。  
  
 XAML セキュリティのまたはアセンブリの簡易名は、によって読み込まれるまたはキャッシュまたはアプリケーション ドメインにあらかじめ存在場合に存在できるであいまいさを削除するための便利な手法は、アセンブリの公開キーを指定します。 詳細については、次を参照してください。 [XAML セキュリティの考慮事項](../../../docs/framework/xaml-services/xaml-security-considerations.md)です。  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>XAML サービス API で XAML Namespace 宣言  
 XAML サービス API で XAML 名前空間の宣言がによって表される、<xref:System.Xaml.NamespaceDeclaration>オブジェクト。 呼び出したコード内の XAML 名前空間を宣言する場合、<xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29>コンス トラクターです。 `ns`と`prefix`パラメーターは、文字列として指定し、これらのパラメーターを提供する入力は、ようにこのトピックで前述 XAML 名前空間の識別子と XAML 名前空間プレフィックスの定義に対応します。  
  
 または、XAML 型システムへの他のアクセスにより、XAML ノード ストリームの一部としての XAML 名前空間情報が見つかった場合<xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType>XAML 名前空間の識別子をレポートおよび<xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType>XAML 名前空間プレフィックスを報告します。  
  
 XAML ノード ストリームで XAML 名前空間の情報は、それを適用するエンティティの前にある XAML ノードとして表示できます。 XAML 名前空間の情報がよりも前のケースが含まれます、`StartObject`の XAML ルート要素です。 詳細については、「 [Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)」を参照してください。  
  
 シナリオの多くを .NET Framework XAML サービス API を使用して、少なくとも 1 つの XAML 名前空間宣言が存在すると、する必要がおよび、宣言は必要がありますが含まれているか、XAML スキーマ コンテキストが必要な情報を参照してください。 XAML 名前空間では、読み込む、または名前空間と既に読み込まれるか、XAML スキーマ コンテキストによって把握されているアセンブリ内の特定の型を解決するためにアセンブリを指定する必要がありますか。  
  
 XAML ノード ストリームを生成するために、XAML の種類の情報は、XAML スキーマ コンテキストを通じて、利用可能なでなければなりません。 最初に作成するには、各ノードに関連する XAML 名前空間を決定することがなく、XAML の型情報を特定できません。 この時点では、型のインスタンスは作成されません、まだですが、XAML スキーマ コンテキストが、アセンブリを定義してバックアップの種類からの情報を検索する必要があります。 例については、マークアップを処理するために`<Party><PartyFavor/></Party>`、XAML スキーマ コンテキストの種類と名前を決定できる必要があります、`ContentProperty`の`Party`、したがってもがわかっていなければなりませんの XAML 名前空間情報`Party`と`PartyFavor`です。 既定の XAML スキーマ コンテキストの場合は、静的リフレクションは、多くのノード ストリームで XAML の種類のノードを生成するために必要な XAML 型システム情報を報告します。  
  
 XAML ノード ストリームからオブジェクト グラフを生成するために、元のマークアップで使用され、XAML ノード ストリームに記録される各 XAML プレフィックスの XAML 名前空間宣言があります。 この時点では、インスタンスが作成されている、および実際の型マッピングの動作が発生します。  
  
 内の XML 名前空間宣言を宣言することができますを使用する方法の 1 つは、XAML 名前空間については、ここで、XAML スキーマ コンテキストを使用する予定の XAML 名前空間は、マークアップで定義されていない場合に事前に設定する必要がある場合、 <xref:System.Xml.XmlParserContext> の<xref:System.Xml.XmlReader>. 使用して<xref:System.Xml.XmlReader>XAML リーダーのコンス トラクターの入力としてまたは<xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>です。  
  
 XAML 名前空間の .NET Framework XAML サービスの処理に関連するその他の 2 つの API は、属性<xref:System.Windows.Markup.XmlnsDefinitionAttribute>と<xref:System.Windows.Markup.XmlnsPrefixAttribute>です。 これらの属性は、アセンブリに適用されます。 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>URI を含む XAML 名前空間の宣言を解釈する XAML スキーマ コンテキストによって使用されます。 <xref:System.Windows.Markup.XmlnsPrefixAttribute>特定の XAML 名前空間は、予測可能なプレフィックスでシリアル化できるように、XAML を生成するツールによって使用されます。 詳細については、次を参照してください。[カスタム型およびライブラリの CLR 属性を XAML-Related](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)です。  
  
## <a name="see-also"></a>参照  
 [XAML ノード ストリームの構造と概念について](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
