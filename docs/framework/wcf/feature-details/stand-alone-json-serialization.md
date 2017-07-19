---
title: "スタンドアロン JSON のシリアル化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
caps.latest.revision: 32
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 32
---
# スタンドアロン JSON のシリアル化
JSON \(JavaScript Object Notation\) は、ブラウザー内の Web ページで実行される JavaScript コードで使用するために特別に設計されたデータ形式です。[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] で作成される ASP.NET AJAX サービスは、既定でこのデータ形式を使用します。  
  
 この形式は、ASP.NET と統合せずに AJAX サービスを作成する場合にも使用できます。この場合、XML が既定のデータ形式になりますが、JSON を選択することもできます。  
  
 JSON をサポートする必要はあっても AJAX サービスを作成する予定はない場合は、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> を使用することで、.NET オブジェクトを JSON データに直接シリアル化したり、このようなデータを .NET 型のインスタンスに逆シリアル化したりできます。この手順の詳細については、「[方法 : JSON データをシリアル化および逆シリアル化する](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md)」を参照してください。  
  
 JSON を使用する場合、一部例外はありますが、<xref:System.Runtime.Serialization.DataContractSerializer> でサポートされているものと同じ .NET 型 がサポートされます。サポートされる型の一覧については、「[データ コントラクト シリアライザーでサポートされる型](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)」を参照してください。これには、ほとんどのプリミティブ型、ほとんどの配列型とコレクション型、<xref:System.Runtime.Serialization.DataContractAttribute> と <xref:System.Runtime.Serialization.DataMemberAttribute> を使用する複合型などがあります。  
  
## .NET 型から JSON 型へのマッピング  
 シリアル化および逆シリアル化の手順でマップされる場合の .NET 型と JSON\/JavaScript 型の対応表を次に示します。  
  
|.NET 型|JSON\/JavaScript|注意|  
|------------|----------------------|--------|  
|すべての数値型 \(<xref:System.Int32>、<xref:System.Decimal>、<xref:System.Double> など\)|数値|`Double.NaN`、`Double.PositiveInfinity`、`Double.NegativeInfinity` などの特殊な値はサポートされていないため、無効な JSON になります。|  
|<xref:System.Enum>|数値|このトピックの「列挙体と JSON」を参照してください。|  
|<xref:System.Boolean>|ブール|\-\-|  
|<xref:System.String>,<xref:System.Char>|文字列|\-\-|  
|<xref:System.Timespan>, <xref:System.Guid>, <xref:System.Uri>|文字列|JSON のこれらの型の形式は、XML の場合と同じです \(基本的には、TimeSpan は ISO 8601 の日付\/時刻形式、GUID は "12345678\-ABCD\-ABCD\-ABCD\-1234567890AB" 形式、URI は "http:\/\/www.example.com" のような自然な文字列形式です\)。正確な情報については、「[データ コントラクト スキーマの参照](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)」を参照してください。|  
|<xref:System.Xml.XmlQualifiedName>|文字列|形式は "name:namespace" です \(最初のコロンの前が名前です\)。名前または名前空間が存在しない場合があります。名前空間がない場合、コロンも省略されることがあります。|  
|<xref:System.Array> 型の<xref:System.Byte>|数値の配列型|各数値は、1 バイトの値を表します。|  
|<xref:System.Datetime>|DateTime 型または文字列型|このトピックの「日付\/時刻と JSON」を参照してください。|  
|<xref:System.DatetimeOffset>|複合型|このトピックの「日付\/時刻と JSON」を参照してください。|  
|XML 型および ADO.NET 型 \(<xref:System.Xml.XmlElement>、<br /><br /> <xref:System.Xml.Linq.XElement>.<xref:System.Xml.XmlNode> の配列、<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>\).|文字列|このトピックの「XML 型と JSON」を参照してください。|  
|<xref:System.DBNull>|空の複合型|\-\-|  
|コレクション、ディクショナリ、および配列|配列|このトピックの「コレクション、ディクショナリ、および配列」を参照してください。|  
|複合型 \(<xref:System.Runtime.Serialization.DataContractAttribute> または <xref:System.SerializableAttribute> が適用された型\)|複合型|データ メンバーは、JavaScript 複合型のメンバーになります。|  
|<xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装する複合型|複合型|他の複合型と同じですが、一部の <xref:System.Runtime.Serialization.ISerializable> 型はサポートされません。このトピックの「高度な情報」の「ISerializable のサポート」を参照してください。|  
|任意の型の `Null` 値|null|null 許容型もサポートされており、null 非許容型と同様に JSON にマップされます。|  
  
### 列挙体と JSON  
 列挙メンバー値は、JSON では数値として処理されるため、列挙メンバー値がメンバー名として含まれているデータ コントラクトでの処理方法とは異なります。データ コントラクトでの処理[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[データ コントラクトの列挙型](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)」を参照してください。  
  
-   たとえば、`public enum Color {red, green, blue, yellow, pink}` の場合、`yellow` をシリアル化すると、文字列の "yellow" ではなく、数字の 3 が生成されます。  
  
-   `enum` のメンバーはすべて、シリアル化できます。<xref:System.Runtime.Serialization.EnumMemberAttribute> 属性と <xref:System.NonSerializedAttribute> 属性は、使用しても無視されます。  
  
-   存在しない `enum` 値を逆シリアル化できます。たとえば、値 87 に対応する色の名前が定義されていなくても、この値を上記の Color 列挙値に逆シリアル化できます。  
  
-   フラグ `enum` は特殊ではなく、他の `enum` と同様に処理されます。  
  
### 日付時刻 とJSON  
 JSON 形式では、日付と時刻を直接サポートしていません。ただし、日付と時刻は使用されることが非常に多いため、ASP.NET AJAX ではこれらの型を特別にサポートしています。ASP.NET AJAX プロキシを使用する場合、.NET の <xref:System.DateTime> 型は JavaScript の `DateTime` 型に完全に対応します。  
  
-   ASP.NET を使用しない場合、JSON では、<xref:System.DateTime> 型はこのトピックの「高度な情報」で説明する特殊な形式の文字列として表されます。  
  
-   JSON では、<xref:System.DateTimeOffset> が複合型 {"DateTime":dateTime,"OffsetMinutes":offsetMinutes} として表現されます。`offsetMinutes` メンバーは、当該イベントの場所に関連付けられたグリニッジ標準時 \(GMT\) \(協定世界時 \(UTC\) とも呼ばれます\) からの現地時刻のオフセットです。`dateTime` メンバーは、当該イベントが発生した時点のインスタンスを表します \(この場合も、ASP.NET AJAX を使用しているときは JavaScript の `DateTime` になり、使用していないときは文字列になります\)。シリアル化時には、`dateTime` メンバーは常に GMT でシリアル化されます。したがって、ニューヨーク時間の午前 3 時を示す場合、`dateTime` の時刻コンポーネントは 8:00 AM であり、`offsetMinutes` は 300 \(GMT マイナス 300 分 \(5 時間\)\) です。  
  
    > [!NOTE]
    >  <xref:System.DateTime> オブジェクトと <xref:System.DateTimeOffset> オブジェクトを JSON にシリアル化した場合、ミリ秒の精度までしか情報は保持されません。1 ミリ秒未満の値 \(マイクロ秒\/ナノ秒\) は、シリアル化時に失われます。  
  
### XML 型と JSON  
 XML 型は JSON 文字列になります。  
  
-   たとえば、XElement 型のデータ メンバー "q" が \<abc\/\> を含む場合、JSON は {"q":"\<abc\/\>"} になります。  
  
-   XML のラップ方法を指定する特別なルールがいくつかあります。詳細については、このトピックで後述する「高度な情報」を参照してください。  
  
-   ASP.NET AJAX を使用している場合に、JavaScript で文字列ではなく XML DOM を使用するときは、<xref:System.ServiceModel.Web.WebGetAttribute> で <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> プロパティを XML に設定するか、<xref:System.ServiceModel.Web.WebInvokeAttribute> で <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> プロパティを XML に設定します。  
  
### コレクション、ディクショナリ、および配列  
 コレクション、ディクショナリ、および配列は、JSON ではすべて配列として表されます。  
  
-   <xref:System.Runtime.Serialization.CollectionDataContractAttribute> を使用するカスタマイズは、JSON 表現では無視されます。  
  
-   ディクショナリは、直接 JSON を操作する手段ではありません。ディクショナリの \<string,object\> は、他の JSON テクノロジの使用方法から予想されるように [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でサポートされていない場合があります。たとえば、ディクショナリで "abc" が "xyz" にマップされ、"def" が 42 にマップされている場合、JSON 表現では {"abc":"xyz","def":42} ではなく、\[{"Key":"abc","Value":"xyz"},{"Key":"def","Value":42}\] になります。  
  
-   JSON を直接使用する \(厳密なコントラクトをあらかじめ定義せずに、キーと値に動的にアクセスする\) 場合、いくつかのオプションがあります。  
  
    -   「[弱い型指定の JSON のシリアル化 \(AJAX\)](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md)」のサンプルを使用することを検討します。  
  
    -   <xref:System.Runtime.Serialization.ISerializable> インターフェイスと逆シリアル化コンストラクターを使用することを検討します。この 2 つの機構を使用すると、シリアル化と逆シリアル化の実行時にそれぞれ JSON のキーと値のペアにアクセスできます。ただし、これらの機構は、部分信頼シナリオでは機能しません。  
  
    -   シリアライザーを使用するのではなく、[JSON と XML 間のマッピング](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md)を使用することを検討します。  
  
    -   シリアル化のコンテキストにおける *"ポリモーフィズム"* は、基本型が必要な場合に派生型をシリアル化できることを指します。コレクションをポリモーフィックに使用する場合は \(コレクションを <xref:System.Object> に割り当てる場合など\)、JSON 固有の特別なルールがあります。この問題については、後の「高度な情報」で詳しく説明します。  
  
## 追加の詳細情報  
  
### データ メンバーの順序  
 JSON を使用する際、データ メンバーの順序は重要ではありません。具体的には、<xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> が設定されていても、JSON データを任意の順序で逆シリアル化できます。  
  
### JSON の型  
 JSON の型は、逆シリアル化時には前述の表と一致する必要はありません。たとえば、`Int` は通常 JSON の数値にマップされますが、JSON 文字列に有効な数値が含まれていれば、その文字列から正常に逆シリアル化することもできます。つまり、"q" という `Int` データ メンバーが存在する場合は、{"q":42} も {"q":"42"} も有効です。  
  
### ポリモーフィズム  
 ポリモーフィックなシリアル化は、基本型が必要な場合に派生型をシリアル化できることで成り立ちます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] による JSON シリアル化でこれがサポートされているのは、XML シリアル化がサポートされている方法と互換性がある場合です。たとえば、`MyBaseType` が必要な場合に `MyDerivedType` をシリアル化したり、`Object` が必要な場合に `Int` をシリアル化したりできます。  
  
 複合型を逆シリアル化する場合を除き、基本型が必要な場合に派生型を逆シリアル化すると、型情報が失われることがあります。たとえば、<xref:System.Object> が必要な場合に <xref:System.Uri> をシリアル化すると、JSON 文字列になります。この文字列を <xref:System.Object> に逆シリアル化した場合、.NET の <xref:System.String> が返されます。デシリアライザーは、この文字列が最初は <xref:System.Uri> 型であったことを認識していません。通常、<xref:System.Object> を必要とするときに、すべての JSON 文字列が .NET 文字列として逆シリアル化されます。また、.NET のコレクション、ディクショナリ、および配列のシリアル化に使用するすべての JSON 配列は、実際の元の型に関係なく、<xref:System.Object> 型の .NET <xref:System.Array> として逆シリアル化されます。JSON のブール型は .NET の <xref:System.Boolean> にマップされます。ただし、<xref:System.Object> が必要な場合、JSON の数値型は .NET の <xref:System.Int32>、<xref:System.Decimal>、または <xref:System.Double> の型として逆シリアル化されます。この場合、最も適切な型が自動的に選択されます。  
  
 インターフェイス型に逆シリアル化する場合、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、宣言された型がオブジェクトである場合と同様に逆シリアル化します。  
  
 独自の基本型と派生型を使用している場合は、通常、<xref:System.Runtime.Serialization.KnownTypeAttribute>、<xref:System.ServiceModel.ServiceKnownTypeAttribute>、または同等の機構を使用する必要があります。たとえば、戻り値が `Animal` である操作があり、実際には \(`Animal` から派生した\) `Cat` のインスタンスを返す場合、<xref:System.Runtime.Serialization.KnownTypeAttribute> を `Animal` 型に適用するか、<xref:System.ServiceModel.ServiceKnownTypeAttribute> を操作に適用し、これらの属性で `Cat` 型を指定する必要があります。詳細については、「[既知のデータ コントラクト型](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)」を参照してください。  
  
 ポリモーフィックなシリアル化のしくみの詳細、およびポリモーフィックなシリアル化を使用するときに留意する必要のある制限事項については、このトピックで後述する「高度な情報」を参照してください。  
  
### バージョン管理  
 <xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスをはじめとするデータ コントラクトのバージョン管理機能は、JSON で完全にサポートされています。また、ほとんどの場合、ある形式 \(XML など\) で型を逆シリアル化した後、その型を別の形式 \(JSON など\) にシリアル化しても、<xref:System.Runtime.Serialization.IExtensibleDataObject> にデータを保持できます。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][上位互換性のあるデータ コントラクト](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).JSON は順序なしであるため、順序情報は失われることに注意してください。また、JSON では、同じキー名を持つ複数のキーと値のペアをサポートしていません。<xref:System.Runtime.Serialization.IExtensibleDataObject> でのすべての操作は、本質的にポリモーフィックです。つまり、派生型はすべての型の基本型である <xref:System.Object> に割り当てられます。  
  
## URL 内の JSON  
 \(<xref:System.ServiceModel.Web.WebGetAttribute> 属性を使用して\) HTTP GET 動詞と共に ASP.NET AJAX エンドポイントを使用する場合、受信パラメーターは、メッセージ本文ではなく要求 URL に配置されます。JSON は、要求 URL 内でもサポートされます。そのため、"number" という `Int` 型と "p" という `Person` 複合型を取得する操作がある場合、次のような URL になります。  
  
```  
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}  
```  
  
 ASP.NET AJAX Script Manager コントロールとプロキシを使用してサービスを呼び出すと、この URL はプロキシによって自動的に生成されるため、確認することはできません。JSON は、ASP.NET AJAX エンドポイントを使用しない URL では使用できません。  
  
## 高度な情報  
  
### ISerializable のサポート  
  
#### サポートされる ISerializable 型とサポートされない ISerializable 型  
 通常、JSON をシリアル化または逆シリアル化するときに、<xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装する型は完全にサポートされています。ただし、これらの型の一部 \(一部の .NET Framework 型を含みます\) は、次のような JSON 固有のシリアル化の側面が原因で正しく逆シリアル化されない方法で実装されています。  
  
-   <xref:System.Runtime.Serialization.ISerializable> では、個々のデータ メンバーの型は事前にはわかりません。このため、型をオブジェクトに逆シリアル化する場合と同様のポリモーフィックな状況になります。前述のように、これは JSON で型情報が失われる原因となる場合があります。たとえば、<xref:System.Runtime.Serialization.ISerializable> 実装で `enum` をシリアル化した型を \(適切にキャストせずに\) `enum` に直接逆シリアル化しようとした場合、逆シリアル化は失敗します。これは、`enum` は JSON の数値型を使用してシリアル化されますが、JSON の数値型は .NET の組み込みの数値型 \(Int32、Decimal、または Double\) に逆シリアル化されるためです。そのため、この数値が `enum` 値を表すために使用されているという情報が失われます。  
  
-   <xref:System.Runtime.Serialization.ISerializable> 型が逆シリアル化コンストラクターで特定の順序の逆シリアル化に依存する場合も、一部の JSON データの逆シリアル化に失敗する場合があります。これは、ほとんどの JSON シリアライザーが特定の順序を保証しないためです。  
  
#### ファクトリ型  
 <xref:System.Runtime.Serialization.IObjectReference> インターフェイスは JSON で一般にサポートされますが、"ファクトリ型" 機能 \(<xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> から、このインターフェイスを実装する型とは異なる型のインスタンスを返す機能\) を必要とする型はサポートされません。  
  
### DateTime ワイヤ形式  
 <xref:System.DateTime> 値は、"\/Date\(700000\+0500\)\/" 形式の JSON 文字列として表されます。ここで、最初の数値 \(この例では 700000\) は GMT タイム ゾーンのミリ秒数であり、1970 年 1 月 1 日午前 0 時以降の \(夏時間ではなく\) 通常時間です。これより前の時間を表すために、この数値が負の値になる場合があります。この例の "\+0500" で構成される部分は省略可能であり、<xref:System.DateTimeKind> の時刻を示します。つまり、逆シリアル化時にローカル タイム ゾーンに変換される必要があります。この部分が指定されていない場合、時刻は <xref:System.DateTimeKind> として逆シリアル化されます。実際の数値 \(この例では "0500"\) と記号 \(\+ または \-\) は無視されます。  
  
 <xref:System.DateTime> をシリアル化すると、<xref:System.DateTimeKind> と <xref:System.DateTimeKind> の時刻はオフセットして書き込まれ、<xref:System.DateTimeKind> はオフセットせずに書き込まれます。  
  
 ASP.NET AJAX クライアントの JavaScript コードにより、このような文字列は JavaScript の `DateTime` インスタンスに自動的に変換されます。類似する形式で .NET の <xref:System.DateTime> 型ではない他の文字列が存在する場合、これらの文字列も変換されます。  
  
 変換は、文字 "\/" をエスケープする場合 \(つまり、JSON が "\\\/Date\(700000\+0500\)\\\/" のような場合\) にのみ実行されます。このため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の JSON エンコーダー \(<xref:System.ServiceModel.WebHttpBinding> によって有効になります\) は、文字 "\/" を常にエスケープします。  
  
### JSON 文字列内の XML  
  
#### XmlElement  
 <xref:System.Xml.XmlElement> は、ラップされずにそのままの状態でシリアル化されます。たとえば、\<abc\/\> を含む <xref:System.Xml.XmlElement> 型のデータ メンバー "x" は、次のように表されます。  
  
```  
{"x":"<abc/>"}  
```  
  
#### XmlNode の配列  
 <xref:System.Xml.XmlNode> 型の <xref:System.Array> オブジェクトは、この型の標準のデータ コントラクト名前空間にある ArrayOfXmlNode という要素にラップされます。"x" が、"value" と空の要素ノード "M" を含む名前空間 "ns" にある、属性ノード "N" を含む配列である場合、次のように表されます。  
  
```  
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}  
```  
  
 XmlNode 配列の先頭 \(他の要素の前\) にある空の名前空間の属性はサポートされません。  
  
#### XElement と DataSet を含む IXmlSerializable 型  
 <xref:System.Runtime.Serialization.ISerializable> 型は、"コンテンツ型"、"DataSet 型"、および "要素型" に細分化されます。これらの型の定義については、「[データ コントラクトの XML および ADO.NET の種類](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)」を参照してください。  
  
 "コンテンツ" 型と "DataSet" 型は、前のセクションで説明した <xref:System.Xml.XmlNode> の <xref:System.Array> オブジェクトと同様にシリアル化されます。これらの型は、その型のデータ コントラクトの名前と名前空間に対応する名前と名前空間を持つ要素にラップされます。  
  
 <xref:System.Xml.Linq.XElement> などの "要素" 型は、このトピックで既に説明した <xref:System.Xml.XmlElement> と同様に、そのままの状態でシリアル化されます。  
  
### ポリモーフィズム  
  
#### 型情報の保持  
 前述のように、ポリモーフィズムは JSON でサポートされていますが、いくつかの制限があります。JavaScript は厳密に型指定されていない言語であるため、通常、型 ID は問題ではありません。ただし、JSON を使用して厳密に型指定されたシステム \(.NET\) と厳密に型指定されていないシステム \(JavaScript\) 間で通信する場合、型 ID を保持していると役立ちます。たとえば、"Square" と "Circle" というデータ コントラクト名を持つ型が "Shape" というデータ コントラクト名を持つ型から派生したとします。"Circle" が .NET から JavaScript に送信され、後で "Shape" を必要とする .NET メソッドに返された場合、該当のオブジェクトが本来は "Circle" であったことが .NET 側でわかれば役立ちます。そうでない場合、派生型に固有の情報 \("Circle" のデータ メンバー "radius" など\) が失われることがあります。  
  
 型 ID を保持するために、複合型を JSON にシリアル化するときに "型ヒント" を追加できます。デシリアライザーはこのヒントを認識し、適切に動作します。"型ヒント" は、JSON のキーと値のペアです。キー名は "\_\_type" です \(2 つのアンダースコアの後に "type" という語が続きます\)。値は、"DataContractName:DataContractNamespace" 形式の JSON 文字列です \(最初のコロンまでが名前です\)。前述の例の "Circle" は、次のようにシリアル化できます。  
  
```  
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}  
```  
  
 型ヒントは、XML スキーマ インスタンス標準で定義された `xsi:type` 属性によく似ており、XML をシリアル化または逆シリアル化するときに使用されます。  
  
 "\_\_type" というデータ メンバーは、型ヒントと競合する可能性があるため、禁止されています。  
  
#### 型ヒントのサイズの削減  
 JSON メッセージのサイズを縮小するために、既定のデータ コントラクト名前空間プレフィックス \(http:\/\/schemas.datacontract.org\/2004\/07\/\) は文字 "\#" に置き換えられます \(この置換を元に戻すことを可能にするために、エスケープ ルールが使用されます。名前空間が "\#" または "\\" で始まる場合、これらの文字に "\\" が追加されます\)。したがって、"Circle" が .NET の "MyApp.Shapes" 名前空間の型である場合、既定のデータ コントラクト名前空間は http:\/\/schemas.datacontract.org\/2004\/07\/MyApp になります。形状と JSON 表現は次のようになります。  
  
```  
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}  
```  
  
 逆シリアル化時には、切り捨てられた名前 \(\#MyApp.Shapes\) と完全名 \(http:\/\/schemas.datacontract.org\/2004\/07\/MyApp.Shapes\) の両方が認識されます。  
  
#### JSON オブジェクト内での型ヒントの位置  
 JSON 表現では、型ヒントは最初に出現する必要があります。JSON の処理でキーと値のペアの順序が重要となるのはこの場合だけです。たとえば、型ヒントの次の指定方法は無効です。  
  
```  
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}  
```  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が使用する <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> と ASP.NET AJAX クライアント ページでは、いずれも型ヒントが常に最初に出力されます。  
  
#### 複合型にのみ適用される型ヒント  
 複合型以外の型の型ヒントを出力する方法はありません。たとえば、戻り値の型が <xref:System.Object> である操作で Circle を返す場合、前に示したような JSON 表現が可能であり、型情報は保持されます。ただし、Uri が返される場合、JSON 表現は文字列であり、この文字列が Uri を表すために使用されているという情報は失われます。これは、プリミティブ型だけでなく、コレクションと配列にも適用されます。  
  
#### 型ヒントが出力される状況  
 型ヒントにより、メッセージ サイズが大幅に増加することがあります \(これを軽減する 1 つの方法として、可能であれば短いデータ コントラクト名前空間を使用します\)。そのため、次のルールによって型ヒントを出力するかどうかが制御されます。  
  
-   ASP.NET AJAX を使用する場合、基本型と派生型の割り当てが存在しない場合でも \(Circle を Circle に割り当てる場合など\)、型ヒントは可能である限り常に出力されます \(これは、厳密に型指定されていない JSON 環境から厳密に型指定された .NET 環境への呼び出しプロセスにおいて、情報が予想外に失われることのないプロセスを完全に実現するために必要です\)。  
  
-   ASP.NET と統合せずに AJAX サービスを使用する場合、基本型と派生型の割り当てが存在する場合にのみ、型ヒントが出力されます。つまり、Circle を Shape または <xref:System.Object> に割り当てるときは出力されますが、Circle に割り当てるときには出力されません。この場合、JavaScript クライアントを適切に実装するために必要な最小限の情報しか提供されないため、パフォーマンスは向上しますが、適切に設計されていないクライアントでの型情報の損失を防ぐことはできません。クライアントでこの問題に対処することを避ける必要がある場合は、サーバーで基本型と派生型の割り当てを一切行わないようにします。  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> 型を使用する場合、`alwaysEmitTypeInformation` コンストラクター パラメーターを使用すると、上記の 2 つのモードのいずれかを選択できます。既定値は "`false`" \(必要な場合にのみ型情報を出力\) です。  
  
#### 重複するデータ メンバー名  
 派生型情報は、基本型情報と共に同じ JSON オブジェクト内に存在しますが、任意の順序で出現する場合があります。たとえば、`Shape` は次のように表されることがあります。  
  
```  
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}  
```  
  
 Circle は、次のように表されることがあります。  
  
```  
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}  
```  
  
 基本型 `Shape` にも "`radius`" というデータ メンバーが含まれている場合、シリアル化と逆シリアル化の両方で競合が発生することになります。これは、シリアル化では JSON オブジェクトは反復するキー名を持つことができないためであり、逆シリアル化では "radius" が `Shape.radius` と `Circle.radius` のどちらを参照しているかが不明確であるためです。そのため、データ コントラクト クラスでは、"プロパティの隠ぺい" \(基本クラスと派生クラスに同じ名前のデータ メンバーが存在する\) という概念は一般に推奨されていませんが、JSON では実際には禁止されています。  
  
#### ポリモーフィズムと IXmlSerializable 型  
 <xref:System.Xml.Serialization.IXmlSerializable> 型は、既知の型の要件を満たしている限り、通常のデータ コントラクト規則に従って、通常どおり相互にポリモーフィックな割り当てを行うことができます。ただし、<xref:System.Object> の代わりに <xref:System.Xml.Serialization.IXmlSerializable> 型をシリアル化すると、結果が JSON 文字列になるため、型情報が失われることになります。  
  
#### ポリモーフィズムと一部のインターフェイス型  
 <xref:System.Xml.Serialization.IXmlSerializable> ではないコレクション型以外の型 \(<xref:System.Object> を除きます\) が必要な場合、コレクション型または <xref:System.Xml.Serialization.IXmlSerializable> を実装する型をシリアル化することは禁止されています。たとえば、`IMyInterface` というカスタム インターフェイスと、`int` 型の <xref:System.Collections.Generic.IEnumerable%601> と `IMyInterface` の両方を実装する `MyType` 型があるとします。この場合、戻り値の型が `IMyInterface` である操作から、`MyType` を返すことは禁止されています。これは、`MyType` は JSON 配列としてシリアル化する必要があり、型ヒントを必要としますが、前述のように型ヒントを配列と共に含めることはできないためです。型ヒントを含めることができるのは、複合型を使用する場合だけです。  
  
#### 既知の型と構成  
 <xref:System.Runtime.Serialization.DataContractSerializer> が使用する既知の型機構は、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> の場合と同様にすべてサポートされます。両方のシリアライザーが同じ構成要素 \([\<system.runtime.serialization\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md) の [\<dataContractSerializer\>](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)\) を読み取って、構成ファイルを通じて追加された既知の型を検出します。  
  
#### Object に割り当てられたコレクション  
 Object に割り当てられたコレクションは、<xref:System.Collections.Generic.IEnumerable%601> を実装するコレクションと同様にシリアル化されます。複合型の場合は、各エントリに型ヒントが含まれた JSON 配列になります。たとえば、<xref:System.Object> に割り当てられた `Shape` 型の <xref:System.Collections.Generic.List%601> は、次のようになります。  
  
```  
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},  
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},  
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]  
```  
  
 <xref:System.Object> に逆シリアル化するときは、次の点に注意してください。  
  
-   `Shape` は、既知の型リストに含まれている必要があります。既知の型に含まれている `Shape` 型の <xref:System.Collections.Generic.List%601> があっても効果はありません。この場合、シリアル化時に `Shape` を既知の型に追加する必要はありません。これは、自動的に実行されます。  
  
-   コレクションは、`Shape` インスタンスを格納する <xref:System.Object> 型の <xref:System.Array> として逆シリアル化されます。  
  
#### 基本コレクションに割り当てられた派生コレクション  
 派生コレクションを基本コレクションに割り当てると、通常、そのコレクションは基本型のコレクションと同様にシリアル化されます。ただし、派生コレクションの項目の型を基本コレクションの項目の型に割り当てることができない場合は、例外がスローされます。  
  
#### 型ヒントとディクショナリ  
 ディクショナリを <xref:System.Object> に割り当てると、ディクショナリに含まれる Key および Value の各エントリは、<xref:System.Object> に割り当てられている場合と同様に処理され、型ヒントを取得します。  
  
 ディクショナリ型をシリアル化した場合、"Key" メンバーと "Value" メンバーを含む JSON オブジェクトは、`alwaysEmitTypeInformation` 設定の影響を受けません。オブジェクトに型ヒントが含まれるのは、前述のコレクション ルールで必要とされる場合だけです。  
  
### JSON の有効なキー名  
 シリアライザーは、有効な XML 名ではないキー名を XML エンコードします。たとえば、"123" という名前のデータ メンバーの場合、"123" は無効な XML 要素名 \(数字で始まる要素名\) であるため、"\_x0031\_\_x0032\_\_x0033\_" のような名前にエンコードされます。XML 名が有効ではない一部の国際文字セットでも、同様の状況が発生する場合があります。JSON 処理に対する XML のこの影響については、「[JSON と XML 間のマッピング](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md)」を参照してください。  
  
## 参照  
 [JSON などのデータ転送形式のサポート](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)