---
title: "XAML Namespaces for .NET Framework XAML Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
caps.latest.revision: 3
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 3
---
# XAML Namespaces for .NET Framework XAML Services
XAML 名前空間は、XML 名前空間の定義を拡張する概念です。  XML 名前空間と同様に、マークアップ内で `xmlns` 属性を使用することで XAML 名前空間を定義できます。  XAML 名前空間は XAML ノード ストリームなどの XAML サービス API でも表されます。  このトピックでは、XAML 名前空間の概念について説明し、XAML 名前空間の定義の方法と、XAML スキーマ コンテキストなどの .NET Framework XAML サービスの各要素で XAML 名前空間を使用する方法について説明します。  
  
## XML 名前空間と XAML 名前空間  
 XAML が特殊な形式の XML であるように、XAML 名前空間は特殊な XML 名前空間です。マークアップには XML の基本形式が使用されます。  マークアップ内で、要素に適用される `xmlns` 属性を利用して、XAML 名前空間とそのマッピングを宣言します。  内部で XAML 名前空間が宣言されている同じ要素に対して、`xmlns` 宣言を実行することができます。  要素に対して XAML 名前空間を宣言すると、その要素、その要素のすべての属性、およびその要素のすべての子要素に対してその宣言が有効になります。  属性が含まれている要素と異なる XAML 名前空間をその属性で使用できます。ただし、マークアップ内で、属性名自体からプレフィックスがその属性名の一部として参照されていることが必要です。  
  
 XAML 名前空間と XML 名前空間の違いについて説明します。XML 名前空間は、スキーマの参照やエンティティの単純な判別に使用されます。  XAML の場合、XAML で使用される型とメンバーは最終的にバッキング型として解決される必要がありますが、XML スキーマの概念はこの機能に該当しません。  XAML 名前空間には、XAML スキーマ コンテキストでこのような型の対応付けを実行するために必要となる情報が含まれています。  
  
## XAML 名前空間の構成要素  
 XAML 名前空間の定義には、プレフィックスと識別子という 2 つの構成要素が含まれます。  マークアップ内で XAML 名前空間を宣言するとき、または XAML 型システムで XAML 名前空間を定義するときに、このような構成要素がそれぞれ表示されます。  
  
 プレフィックスには、[W3C による XML 1.0 名前空間の仕様](http://go.microsoft.com/fwlink/?LinkID=161735)で定められている任意の文字列を使用できます。  一般的なマークアップ ファイルではプレフィックスが頻繁に記述されるため、慣習として非常に短い文字列が使用されます。  複数の XAML 実装で使用するための XAML 名前空間では、慣習的に特定のプレフィックスが使用されます。  たとえば、XAML 言語の XAML 名前空間は一般的にプレフィックス `x` を使用して対応付けされます。  既定の XAML 名前空間を定義することもできます。既定の XAML 名前空間ではプレフィックスが定義で指定されませんが、.NET Framework XAML サービス API から定義または照会された場合は、空の文字列として表されます。  一般的に、XAML を実装するテクノロジとそのシナリオおよびボキャブラリによって、プレフィックスを省略したマークアップを最大限増やすために、意図的に既定の XAML 名前空間が選択されます。  
  
 識別子には、[W3C による XML 1.0 名前空間の仕様](http://go.microsoft.com/fwlink/?LinkID=161735)で定められている任意の文字列を使用できます。  慣習として、XML 名前空間または XAML 名前空間の識別子は URI の形で \(通常はプロトコルで修飾された絶対 URI として\) 指定されるのが一般的です。  多くの場合、特定の XAML ボキャブラリを定義するバージョン情報がパス文字列の中に含まれます。  XAML 名前空間によって、XML URI の規則に加えて新しい識別子規則が追加されます。  XAML 名前空間では、XAML 名前空間で指定された型を解決したり、属性をメンバーとして解決したりするために XAML スキーマ コンテキストで必要となる情報が、識別子によって伝達されます。  
  
 XAML スキーマ コンテキストに情報を伝達するために、XAML 名前空間の識別子が URI の形のままになる場合があります。  ただし、この場合、この URI も特定のアセンブリまたは一連のアセンブリ内の一致する識別子として宣言されます。  アセンブリでこれを行うには、<xref:System.Windows.Markup.XmlnsDefinitionAttribute> を使用してアセンブリに属性を設定します。  属性付きのアセンブリ内で、XAML 名前空間を識別し、CLR ベースの型解決処理をサポートするこの方法は、.NET Framework XAML サービスにおける既定の XAML スキーマ コンテキストでサポートされます。  さらに一般的には、XAML スキーマ コンテキストが CLR を含んでいるか、既定の XAML スキーマ コンテキストに基づいている場合 \(CLR アセンブリから CLR 属性を読み取るために必要です\)、この規則を使用できます。  
  
 XAML 名前空間も、CLR 名前空間を伝達する規則と、型を定義するアセンブリによって識別できます。  この規則は、型が含まれるアセンブリに <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 属性が存在しない場合に使用されます。  この規則は URI 規則よりも複雑化する可能性があります。また、アセンブリの参照方法が複数あるため、あいまいさや重複が発生する可能性があります。  
  
 CLR 名前空間とアセンブリ規則を使用する識別子の、最も基本的な形は、次のようになります。  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` および `; assembly=` は、この構文のリテラル要素です。  
  
 *clrnsName* は、CLR 名前空間を識別する文字列名です。  この文字列名の中に含まれるドット \(.\) は、CLR 名前空間に関するヒントを示し、他の CLR 名前空間との関係を表します。  
  
 *assemblyShortName* は、XAML で有用な型を定義するアセンブリの文字列名です。  宣言される XAML 名前空間を利用してアクセスされる型は、アセンブリによって定義され、*clrnsName* で指定された CLR 名前空間内で特別に宣言されることになります。  この文字列名は、通常、<xref:System.Reflection.AssemblyName.Name%2A?displayProperty=fullName> によって報告される情報と一致します。  
  
 CLR 名前空間とアセンブリ規則の詳細な定義は、次のようになります。  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName* は、<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName> 入力として有効な任意の文字列を表します。  この文字列には、カルチャ、公開キー、またはバージョン情報を含めることができます \(このような概念の定義については <xref:System.Reflection.Assembly> のリファレンス トピックを参照してください\)。  COFF の形式および証拠 \(<xref:System.Reflection.Assembly.Load%2A> の他のオーバーロードで使用する場合\) は、XAML アセンブリの読み込み目的には対応しません。すべての読み込み情報は文字列として表される必要があります。  
  
 アセンブリに公開キーを指定することは、XAML のセキュリティを確保するために有効な手法です。また、アセンブリが簡易名によって読み込まれる場合に生じるあいまいさや、キャッシュまたはアプリケーション ドメインの既存のあいまいさを解消するためにも役立ちます。  詳細については、「[XAML Security Considerations](../../../docs/framework/xaml-services/xaml-security-considerations.md)」を参照してください。  
  
## XAML サービス API における XAML 名前空間宣言  
 XAML サービス API では、XAML 名前空間宣言は <xref:System.Xaml.NamespaceDeclaration> オブジェクトによって表されます。  コード内で XAML 名前空間を宣言する場合、<xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> コンストラクターを呼び出します。  `ns` パラメーターと `prefix` パラメーターは文字列として指定します。この 2 つのパラメーターの入力内容は、このトピックで既に説明した、XAML 名前空間識別子および XAML 名前空間プレフィックスの定義と対応しています。  
  
 XAML ノード ストリームの中で、または XAML 型システムへの他のアクセスを利用して、XAML 名前空間の情報を調べる場合、<xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=fullName> を使用すると XAML 名前空間識別子が返され、<xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=fullName> を使用すると XAML 名前空間プレフィックスが返されます。  
  
 XAML ノード ストリームで、XAML 名前空間の情報は、適用対象のエンティティの前にある XAML ノードとして表示される場合があります。  これは、XAML 名前空間の情報が XAML ルート要素の `StartObject` の前にある場合にも同じです。  詳細については、「[Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)」を参照してください。  
  
 .NET Framework XAML サービス API が使用されるシナリオでは、多くの場合、1 つ以上の XAML 名前空間宣言が存在すると考えられます。その宣言に、XAML スキーマ コンテキストで必要な情報が含まれている、または参照されていることが必要です。  XAML 名前空間には、読み込まれるアセンブリを指定するか、読み込み済みまたは XAML スキーマ コンテキストで認識済みの名前空間とアセンブリの中で特定の型を解決するために役立つアセンブリを指定する必要があります。  
  
 XAML ノード ストリームを生成するためには、XAML スキーマ コンテキストによって XAML 型情報が得られることが必要です。  XAML 型情報を決定するには、作成する各ノードに対応する XAML 名前空間を先に決定する必要があります。  この時点ではまだ型のインスタンスは作成されていませんが、XAML スキーマ コンテキストでは、アセンブリの定義とバッキング型の定義から情報を参照する必要がある場合があります。  たとえば、マークアップ `<Party><PartyFavor/></Party>` を処理するには、XAML スキーマ コンテキストで `Party` の `ContentProperty` の名前と型を決定できる必要があるため、`Party` および `PartyFavor` の XAML 名前空間情報も認識されている必要があります。  既定の XAML スキーマ コンテキストの場合、ノード ストリームに XAML 型ノードを生成するために必要な XAML 型システム情報の多くが、静的リフレクションによって取得されます。  
  
 XAML ノード ストリームのオブジェクト グラフを生成するには、元のマークアップで使用され、XAML ノード ストリームで記録された、それぞれの XAML プレフィックスに対応する XAML 名前空間宣言が存在していることが必要です。  この時点でインスタンスが作成され、実際の型の対応付けが行われます。  
  
 XAML 名前空間の情報を事前に入力する必要がある場合 \(たとえば、XAML スキーマ コンテキストで使用する予定の XAML 名前空間がマークアップで定義されていない場合など\)、<xref:System.Xml.XmlReader> の <xref:System.Xml.XmlParserContext> で XML 名前空間宣言を宣言する手法を使用できます。  次に、その <xref:System.Xml.XmlReader> を XAML リーダー コンストラクター \(<xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=fullName>\) の入力として使用します。  
  
 .NET Framework XAML サービスで XAML 名前空間の処理に対応する、他の 2 つの API は、<xref:System.Windows.Markup.XmlnsDefinitionAttribute> 属性および <xref:System.Windows.Markup.XmlnsPrefixAttribute> 属性です。  これらの属性はアセンブリに適用されます。  <xref:System.Windows.Markup.XmlnsDefinitionAttribute> は、XAML スキーマ コンテキストで、URI を含む XAML 名前空間宣言を解釈するために使用されます。  <xref:System.Windows.Markup.XmlnsPrefixAttribute> は、XAML を出力するツールで使用されます。これによって、特定の XAML 名前空間を予測可能なプレフィックスでシリアル化することができます。  詳細については、「[XAML\-Related CLR Attributes for Custom Types and Libraries](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)」を参照してください。  
  
## 参照  
 [Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)