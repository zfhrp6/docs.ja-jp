---
title: "クラスを作成するためのスキーマのインポート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF, スキーマのインポートとエクスポート"
  - "XsdDataContractImporter クラス"
ms.assetid: b9170583-8c34-43bd-97bb-6c0c8dddeee0
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# クラスを作成するためのスキーマのインポート
クラスで使用可能なスキーマを生成する[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]を使用して、 <xref:System.Runtime.Serialization.XsdDataContractImporter>クラスです。 ここでは、生成時に指定できる各種のオプションについて解説します。  
  
## <a name="the-import-process"></a>インポート処理  
 スキーマのインポート処理が始まり、 <xref:System.Xml.Schema.XmlSchemaSet>を生成し、 <xref:System.CodeDom.CodeCompileUnit>します。  
  
 `XmlSchemaSet` は、一連の XML スキーマ定義言語 (XSD) スキーマ ドキュメントを表す [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] のスキーマ オブジェクト モデル (SOM) の一部です。 作成する、`XmlSchemaSet`オブジェクトの一連の XSD ドキュメントから、各ドキュメントに逆シリアル化、 <xref:System.Xml.Schema.XmlSchema>オブジェクト (を使用して、 <xref:System.Xml.Serialization.XmlSerializer>)、新規作成 を追加して`XmlSchemaSet`します。  
  
 `CodeCompileUnit` は、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] コードを抽象化して表す、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] のコード ドキュメント オブジェクト モデル (CodeDOM) の一部です。 実際のコードを生成する、`CodeCompileUnit`のサブクラスを使用して、 <xref:System.CodeDom.Compiler.CodeDomProvider>クラスなど、 <xref:Microsoft.CSharp.CSharpCodeProvider>または<xref:Microsoft.VisualBasic.VBCodeProvider>クラスです。  
  
#### <a name="to-import-a-schema"></a>スキーマをインポートするには  
  
1.  インスタンスを作成、 <xref:System.Runtime.Serialization.XsdDataContractImporter>します。  
  
2.  省略可能です。 `CodeCompileUnit` をコンストラクターに渡します。 スキーマのインポート時に生成された型がこの `CodeCompileUnit` インスタンスに追加されるので、以降の処理は、`CodeCompileUnit` が空でない状態から始まります。  
  
3.  省略可能です。 1 つを呼び出して、 <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A>メソッドです。 指定されたスキーマが有効なデータ コントラクト スキーマであって、インポートしても問題ないかどうかを判断するメソッドです。 `CanImport` メソッドには、次の手順に出てくる `Import` と同様に、オーバーロードがあります。  
  
4.  オーバー ロードされたいずれかを呼び出して`Import`メソッドなど、 <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29>メソッドです。  
  
     これは、指定しなければならない引数が `XmlSchemaSet` だけという最も簡潔なオーバーロードであり、匿名型を含め、一連のスキーマに記述されている型をすべてインポートできます。 他のオーバー ロードでは、インポートするには、XSD 型または型の一覧を指定できます (の形式で、 <xref:System.Xml.XmlQualifiedName>または一連の`XmlQualifiedName`オブジェクト)。 この場合は、指定した型だけがインポートされます。 オーバー ロードは、 <xref:System.Xml.Schema.XmlSchemaElement>のうち特定の要素をインポートする、 `XmlSchemaSet`、(かどうかが匿名か)、関連する種類とします。 このメソッドの戻り値は `XmlQualifiedName` であり、この要素に対応して生成された型のデータ コントラクト名を表します。  
  
     `Import` メソッドを何度も呼び出すと、同じ `CodeCompileUnit` に複数の項目が追加されます。 `CodeCompileUnit` に既に存在する型は生成されません。 したがって、`Import` オブジェクトをいくつも使うのではなく、同じ `XsdDataContractImporter` の `XsdDataContractImporter` を必要な回数呼び出すようにしてください。 同じ型が重複して生成されることがないので、この方法をお勧めします。  
  
    > [!NOTE]
    >  インポート中に障害が発生した場合の `CodeCompileUnit` の状態は不定です。 このような `CodeCompileUnit` を使うと、セキュリティ上の脆弱性につながるおそれがあります。  
  
5.  アクセス、`CodeCompileUnit`を通じて、 <xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A>プロパティです。  
  
### <a name="import-options-customizing-the-generated-types"></a>インポート オプション : 生成された型のカスタマイズ  
 設定することができます、<xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A>のプロパティ、 <xref:System.Runtime.Serialization.XsdDataContractImporter>のインスタンスに、 <xref:System.Runtime.Serialization.ImportOptions>クラスをインポート処理のさまざまな側面を制御します。 生成される型に直接影響するオプションが多数あります。  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>アクセス レベルの制御 (GenerateInternal または /internal スイッチ)  
 これに対応して、 **/内部**スイッチ、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)します。  
  
 通常、スキーマから生成されるのはパブリック型です。ここにプライベート フィールドや対応するパブリック データ メンバー プロパティが定義されます。 代わりに、内部型を生成するには、設定、 <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A>プロパティを`true`します。  
  
 次の例では、内部に変換するスキーマ クラスの場合、 <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A>にプロパティが設定されています。`true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>名前空間の制御 (Namespaces または /namespace スイッチ)  
 これに対応して、 **/namespace**スイッチ、`Svcutil.exe`ツールです。  
  
 通常、スキーマから生成された型が生成される[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]名前空間の特定に対応する各 XSD 名前空間を持つ、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]で説明するマッピングに従って名前空間[データ コントラクト スキーマの参照](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)します。 このマッピングをカスタマイズすることができます、<xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A>プロパティを<xref:System.Collections.Generic.Dictionary%602>\</TKey, TValue>。 指定した XSD 名前空間がディクショナリに存在する場合、その XSD 名前空間に対応する [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 名前空間も、ディクショナリから取得されます。  
  
 たとえば、次のスキーマを考えます。  
  
 [!code[c_SchemaImportExport#10](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 
          `Namespaces` プロパティを使って、"http://schemas.contoso.com/carSchema" という名前空間を "Contoso.Cars" に対応付ける例を示します。  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>SerializableAttribute の追加 (GenerateSerializable または /serializable スイッチ)  
 これに対応して、 **/serializable**スイッチ、`Svcutil.exe`ツールです。  
  
 使用できるようにするために、スキーマから生成された型に対して重要な場合があります[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]ランタイム シリアル化エンジン (たとえば、 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName>と<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>クラス)。 たとえば、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] リモート処理に使うような場合がこれに当たります。 これを有効にする必要がありますを適用する、 <xref:System.SerializableAttribute>属性だけでなく、通常、生成された型を<xref:System.Runtime.Serialization.DataContractAttribute>属性です。 `GenerateSerializable` オプションを `true` に設定すると、この属性が自動的に生成されます。  
  
 
          `Vehicle` オプションを `GenerateSerializable` に設定して `true` クラスを生成する例を示します。  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>データ バインディング機能の追加 (EnableDataBinding または /enableDataBinding スイッチ)  
 これに対応して、 **/enableDataBinding** Svcutil.exe ツールをオンにします。  
  
 スキーマから生成された型を GUI コンポーネントにバインドして、この型のインスタンスを更新したとき、自動的に UI にも反映されるようにする場合があります。 `XsdDataContractImporter`を実装する型を生成することができます、 <xref:System.ComponentModel.INotifyPropertyChanged>インターフェイス、プロパティが変更にイベントがトリガーされるようにします。 このインターフェイスをサポートするクライアント UI プログラミング環境で使用するための型を生成している場合 (など[!INCLUDE[avalon1](../../../../includes/avalon1-md.md)])、設定、 <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A>プロパティを`true`この機能を有効にします。  
  
 例を次に、`Vehicle`で生成されたクラス、 <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A>設定`true`します。  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>インポート オプション: コレクション型の選択  
 XML でアイテムのコレクションを表すパターンには、アイテムのリストと、アイテム間の関連付けの&2; 種類があります。 文字列のリストの例を次に示します。  
  
 [!code[C_SchemaImportExport#11](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 文字列と整数 (`city name` と `population`) を関連付ける例を次に示します。  
  
 [!code[C_SchemaImportExport#12](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
>  関連付けもリストと見なすことができます。 たとえば、上記の関連付けは、文字列と整数の&2; つのフィールドから成る複雑な `city` オブジェクトのリストと考えることも可能です。 どちらの方法であっても、XSD スキーマで表現できます。 この&2; つを区別する手段はないので、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に特有の特別な注釈がスキーマ内になければ、このようなパターンは常にリストとして扱われます。 注釈がある場合は、関連付けを表すものとして扱われます。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][データ コントラクト スキーマ リファレンス](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)します。  
  
 リストは通常、ジェネリック リストから派生したコレクション データ コントラクト、または [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の配列としてインポートされます。スキーマがコレクションの標準的な名前付けパターンに従っているかどうかによって切り分けます。 これについては説明について詳しく[データ コントラクトのコレクション型](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)します。 関連付けは通常、いずれかとしてインポート、<xref:System.Collections.Generic.Dictionary%602>または辞書オブジェクトから派生したコレクション データ コントラクト\</TKey, TValue>。 たとえば、次のスキーマを考えます。  
  
 [!code[c_SchemaImportExport#13](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 これをインポートすると次のようになります (読みやすいようプロパティの代わりにフィールドを記載)。  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 このようなスキーマ パターンに対し、生成されるコレクション型をカスタマイズすることも可能です。 などからコレクションを生成する場合、 <xref:System.ComponentModel.BindingList%601>の代わりに、<xref:System.Collections.Generic.List%601>コレクションの内容が変わるクラス型をリスト ボックスにバインドして、それをするために自動的に更新します。 これを行うには、設定、 <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>のプロパティ、 <xref:System.Runtime.Serialization.ImportOptions> (以下参照先の型として知られている) で使用されるコレクション型の一覧にクラスをします。 コレクションのインポート時には、参照されるコレクション型のリストが順に調べられ、最も適したコレクションがあれば、それが使用されます。 アソシエーションはジェネリックか否かにかかわらずを実装する型とのみ一致<xref:System.Collections.IDictionary>インターフェイスのリストは、すべてのサポートされるコレクション型を照合されます。  
  
 たとえば場合、 <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>プロパティに設定されて、 <xref:System.ComponentModel.BindingList%601>、`people`前の例での種類は、次のように生成します。  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 クローズ ジェネリック型 (型パラメーターすべてに具体的な型が指定されているジェネリック型) は、合致度が最も高いと見なされます。 たとえば場合、種類`BindingList(Of Integer)`と<xref:System.Collections.ArrayList>渡されるとして参照される型のコレクションにスキーマ内に整数のリストをインポート、`BindingList(Of Integer)`です。 一方、それ以外のリスト (`List(Of String)` など) は、`ArrayList` としてインポートされます。  
  
 ジェネリック `IDictionary` インターフェイスを実装する型を "参照される" 型のコレクションに追加した場合、型パラメーターは、完全にオープンであるか完全にクローズであるかのどちらかです。  
  
 複製は使用できません。 たとえば `List(Of Integer)` と `Collection(Of Integer)` の両方を "参照される" 型に追加することはできません。 仮に追加したとしても、整数のリストがスキーマ中に表れたとき、どちらを使うか決められないからです。 もっとも、このような重複が検出されるのは、それが問題になるような型がスキーマ中にある場合だけです。 インポートするスキーマ中に、たとえば整数のリストがないのであれば、`List(Of Integer)` と `Collection(Of Integer)` の両方が "参照される" 型のコレクションにあっても問題はなく、単に何にも使われなかったというだけのことです。  
  
 参照されるコレクション型のしくみは、プリミティブ型のコレクションばかりでなく、複合型のコレクション (他のコレクションから成るコレクションを含む) にも同様に働きます。  
  
 `ReferencedCollectionTypes`プロパティに対応して、 **/collectionType** SvcUtil.exe ツールをオンにします。 複数のコレクション型を参照することに注意してください、 **/collectionType**スイッチを複数回指定する必要があります。 型が MsCorLib.dll にない場合は、そのアセンブリも参照する必要を使用して、 **/reference**切り替えます。  
  
#### <a name="import-options-referencing-existing-types"></a>インポート オプション : 既存の型の参照  
 スキーマ内の型が既存の [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型に対応する場合は、その型を一から作成する必要はありません  (以下の説明は、非コレクション型にのみ当てはまります。 コレクション型については、前のセクションを参照してください)。  
  
 たとえば、企業全体で共通に、"Person" というデータ コントラクト型を使っており、人を表す場合には常にこれを使いたいとします。 いくつかのサービスでこの型を利用し、そのスキーマがサービス メタデータに表示される場合は、このスキーマをインポートするときに既存の `Person` 型を再利用でき、サービスごとに新たに生成する必要がありません。  
  
 これを行うには、一覧を渡す[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]コレクションに再利用する型、 <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A>プロパティ上を返します、 <xref:System.Runtime.Serialization.ImportOptions>クラスです。 これらの型のいずれかが、スキーマ型の名前および名前空間と一致すれば、その構造が比較されます。 名前も構造も合致した場合は、型は新たに生成されず、既存の [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型が再利用されます。 名前だけが一致して構造が一致しない場合は、例外が発生します。 型の参照時に、バージョンによる (オプションのデータ メンバーの追加などの) 差異は許容されません。 構造は厳密に合致しなければなりません。  
  
 "参照される" 型のコレクションに、データ コントラクト名と名前空間が同一である型を重複して追加しても、その名前と名前空間でスキーマ型をインポートしない限り問題ありません。 したがって、実際にはスキーマに現れることのない型については重複を気にすることなく、アセンブリ内の型をすべてコレクションに追加してしまうことができます。  
  
 `ReferencedTypes`プロパティに対応して、 **/reference** Svcutil.exe ツールの特定のモードに切り替えます。  
  
> [!NOTE]
>  Svcutil.exe を使用する場合または (で[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)])、**サービス参照の追加**MsCorLib.dll に型のすべてのツールが自動的に参照します。  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>インポート オプション : 非データ コントラクト スキーマを IXmlSerializable 型としてインポート  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>スキーマの限られたサブセットをサポートします。 未対応のスキーマ構造 (たとえば XML 属性) をインポートしようとすると例外が発生します。 ただし、設定、 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>プロパティを`true`がサポートするスキーマの範囲が広がります。 設定すると`true`、 <xref:System.Runtime.Serialization.XsdDataContractImporter>を実装する型を生成、 <xref:System.Xml.Serialization.IXmlSerializable>インターフェイスです。 そのため、これらの型の XML 表現に直接アクセスできるようになります。  
  
##### <a name="design-considerations"></a>設計上の考慮事項  
  
-   弱く型指定された XML 表現を直接扱うのは困難です。 など、別のシリアル化エンジンとしての使用を検討、 <xref:System.Xml.Serialization.XmlSerializer>厳密に型指定のデータと互換性のないスキーマ コントラクトと操作する。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][XmlSerializer クラスを使用して](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)します。  
  
-   スキーマ構造をインポートできない、 <xref:System.Runtime.Serialization.XsdDataContractImporter>場合でも、 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>にプロパティが設定されている`true`します。 ここでも、使用を検討して、 <xref:System.Xml.Serialization.XmlSerializer>このような場合です。  
  
-   詳細なスキーマ構造には、両方がサポートされているときに<xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>は`true`または`false`は「[データ コントラクト スキーマの参照](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)します。  
  
-   スキーマの生成<xref:System.Xml.Serialization.IXmlSerializable>型では、インポートし、エクスポートの忠実性は保持されないためです。 つまり、生成された型を基にスキーマをエクスポートし、再びこれをクラスとしてインポートした場合、元どおりのスキーマにはなりません。  
  
 結合するには、 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>オプションを指定する、 <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A>前に説明したオプション。 型として生成する必要がある<xref:System.Xml.Serialization.IXmlSerializable>実装では、構造的なチェックをスキップして、使用して、 <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A>機能します。  
  
 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>オプションに対応して、 **/importXmlTypes** Svcutil.exe ツールをオンにします。  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>生成された IXmlSerializable 型の使い方  
 生成された`IXmlSerializable`種類には、"nodesField"というプライベート フィールドが含まれているの配列を返す<xref:System.Xml.XmlNode>オブジェクトです。 このような型のインスタンスを逆シリアル化すると、XML ドキュメント オブジェクト モデルに基づき、このフィールドを介して XML データに直接アクセスできるようになります。 この型のインスタンスをシリアル化する際、"nodesField" フィールドに XML データを設定しておくと、これもシリアル化の対象になります。  
  
 以上の処理は `IXmlSerializable` インターフェイスで実装されます。 生成された`IXmlSerializable`の種類、 <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>実装の呼び出し、 <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A>のメソッド、 <xref:System.Runtime.Serialization.XmlSerializableServices>クラスです。 メソッドがを通じて提供される XML に変換するヘルパー メソッド、 <xref:System.Xml.XmlReader>型の配列を<xref:System.Xml.XmlNode>オブジェクトです。 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>実装では、その逆の配列に変換する`XmlNode`オブジェクトのシーケンスを<xref:System.Xml.XmlWriter>呼び出しです。 これは、 <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A>メソッドです。  
  
 スキーマのエクスポート処理は、生成された `IXmlSerializable` クラスに対して実行できます。 ただし、先に述べたように、元どおりのスキーマは再現されません。 任意の XSD 型を表す、"anyType" という標準型になります。  
  
 これを行うに適用することで、 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute>属性を生成された`IXmlSerializable`クラスとメソッドを指定することを呼び出す、 <xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A> "anyType"型を生成するメソッドです。  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.XmlSerializableServices>型がこの特定の機能をサポートするためにのみ存在します。 他の目的で使用することはお勧めできません。  
  
#### <a name="import-options-advanced-options"></a>インポート オプション : 高度なオプション  
 他にも、次のようなオプションがあります。  
  
-   <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A>プロパティです。 指定の<xref:System.CodeDom.Compiler.CodeDomProvider>を使用して生成されたクラスのコードを生成します。 機能が回避インポート メカニズムされます、 <xref:System.CodeDom.Compiler.CodeDomProvider>はサポートしていません。 たとえば J# にはジェネリック型の機能がありません。 このプロパティに j# コード プロバイダーを指定する場合のジェネリック型は生成されません、インポート側の<xref:System.CodeDom.CodeCompileUnit>します。 場合、 <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A>の完全なセットを設定しない[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]機能が制限なしで使用されます。  
  
-   <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A>プロパティです。 <xref:System.Runtime.Serialization.IDataContractSurrogate>実装は、このプロパティを指定します。 <xref:System.Runtime.Serialization.IDataContractSurrogate>インポート処理をカスタマイズします。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][データ コントラクト サロゲート](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)します。 既定では、サロゲートは使用されません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.Runtime.Serialization.XsdDataContractImporter>   
 <xref:System.Runtime.Serialization.XsdDataContractExporter>   
 <xref:System.Runtime.Serialization.ImportOptions>   
 [データ コントラクト スキーマの参照](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)   
 [データ コントラクト サロゲート](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)   
 [スキーマのインポートとエクスポート](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)   
 [クラスからのスキーマのエクスポート](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)   
 [データ コントラクト スキーマの参照](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)