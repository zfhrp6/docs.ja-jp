---
title: "JSON と XML 間のマッピング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 770be9ea5327b32286de64207a3cf07bca7449c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mapping-between-json-and-xml"></a>JSON と XML 間のマッピング
<xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> によって作成されるリーダーとライターには、JSON (JavaScript Object Notation) コンテンツでの XML API が備わっています。 JSON は、JavaScript のオブジェクト リテラルのサブセットを使用してデータをエンコードします。 このファクトリによって作成されるリーダーおよびライターは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションが <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> または <xref:System.ServiceModel.WebHttpBinding> を使用して JSON コンテンツを送信または受信するときにも使用されます。  
  
 JSON リーダーは JSON コンテンツで初期化されると、XML インスタンスで動作するテキストの XML リーダーと同じ方法で動作します。 テキストの XML リーダーでの一連の呼び出しによって特定の XML インスタンスが生成されると、JSON ライターは JSON コンテンツを書き出します。 このトピックでは、高度なシナリオで使用するために、この XML のインスタンスと JSON コンテンツ間のマッピングについて説明します。  
  
 内部的には、JSON は [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって処理される際に XML 情報セットとして表されます。 マッピングは論理上の処理であるため、通常はこのような内部表現を考慮する必要はありません。JSON は通常、メモリで物理的に XML に変換されたり、XML から JSON に変換されたりすることはありません。 マッピングとは、XML API を使用して JSON コンテンツにアクセスすることを意味します。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で JSON を使用する場合、通常のシナリオでは <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 動作、または該当する場合は <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> 動作により、<xref:System.ServiceModel.Description.WebHttpBehavior> が自動的にプラグインされます。 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、JSON と XML 情報セット間のマッピングを認識し、直接 JSON を処理しているかのように動作します。 XML が次のマッピングに従うという了解の下に、任意の XML リーダーまたはライターで <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> を使用できます。  
  
 高度なシナリオでは、次のマッピングへの直接アクセスが必要になることがあります。 このようなシナリオが生じるのは、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> に依存することなく、独自の方法で JSON のシリアル化および逆シリアル化を行うとき、または JSON を含むメッセージに対して直接 <xref:System.ServiceModel.Channels.Message> 型を処理するときです。 JSON と XML 間のマッピングは、メッセージ ログにも使用されます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のメッセージ ログ機能を使用する場合、次のセクションで説明するマッピングに従って、JSON メッセージが XML としてログに記録されます。  
  
 マッピングの概念を明確にするために、次に JSON ドキュメントの例を示します。  
  
```json  
{"product":"pencil","price":12}  
```  
  
 前述のリーダーのいずれか 1 つを使用してこの JSON ドキュメントを読み取るには、次の XML ドキュメントの読み取りに使用するシーケンスと同一の、<xref:System.Xml.XmlDictionaryReader> 呼び出しのシーケンスを使用します。  
  
```xml  
<root type="object">  
    <product type="string">pencil</product>  
    <price type="number">12</price>  
</root>  
```  
  
 また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によってこの例の JSON メッセージが取得されてログに記録される場合は、先行ログの XML フラグメントを参照します。  
  
## <a name="mapping-between-json-and-the-xml-infoset"></a>JSON と XML 情報セット間のマッピング  
 正式には、マッピングは JSON の間で説明した[RFC 4627](http://go.microsoft.com/fwlink/?LinkId=98808) (を除く厳密でないと特定の特定の制限を追加するその他の制限) XML 情報セット (およびいないテキスト形式の XML) として記載[XML について設定](http://go.microsoft.com/fwlink/?LinkId=98809)です。 このトピックの定義を参照して*情報項目*および [角かっこで囲んで] フィールドです。  
  
 空白の JSON ドキュメントは空白の XML ドキュメントにマップされ、空白の XML ドキュメントは空白の JSON ドキュメントにマップされます。 XML から JSON へのマッピングで、先行する空白およびドキュメント後続の空白は許可されません。  
  
 マッピングは、ドキュメント情報項目 (DII: Document Information Item) または要素情報項目 (EII: Element Information Item) のいずれか一方と JSON の間に定義されます。 EII、または DII の [document element] プロパティは、Root JSON Element と呼ばれます。 また、ドキュメント フラグメント (ルート要素を複数持つ XML) は、このマッピングではサポートされません。  
  
 例 : 次のドキュメントがあるとします。  
  
 `<?xml version="1.0"?>`  
  
 `<root type="number">42</root>`  
  
 また、次の要素があるとします。  
  
 `<root type="number">42</root>`  
  
 どちらにも JSON へのマッピングが存在します。 <`root`> 要素は、どちらの場合も、Root JSON Element です。  
  
 また、DII の場合は次の点を考慮する必要があります。  
  
-   [children] 一覧には、除外する必要のある項目が含まれています。 JSON からマッピングされた XML を読み取るときは、この事実に依存しないでください。  
  
-   [children] 一覧には、注釈情報項目が保持されません。  
  
-   [children] 一覧には、DTD 情報項目が保持されません。  
  
-   [Children] 一覧に個人情報 (PI) の情報項目が保持していない (、 \<? xml… > 宣言は PI 情報項目と見なされません)  
  
-   [notations] セットは空です。  
  
-   [unparsed entities] セットは空です。  
  
 例 : 次のドキュメントでは [children] が PI とコメントを保持するため、JSON へのマッピングが存在しません。  
  
 `<?xml version="1.0"?>`  
  
 `<!--comment--><?pi?>`  
  
 `<root type="number">42</root>`  
  
 Root JSON Element としての EII には次の特性があります。  
  
-   [local name] は値 "root" を持ちます。  
  
-   [namespace name] は値を持ちません。  
  
-   [prefix] は値を持ちません。  
  
-   [children] には、後述するように内部要素である EII、または文字情報項目 (CII: Character Information Item) のいずれか一方が含まれる場合と、どちらも含まれない場合がありますが、両方とも含まれることはありません。  
  
-   [attributes] には、次のオプションの属性情報項目 (AII: Attribute Information Item) が含まれる場合があります。  
  
-   後述の JSON Type Attribute ("type")。 この属性は、マップされた XML で JSON 型 (文字列、数値、ブール値、オブジェクト、配列、または null) を保持するのに使用します。  
  
-   後述の Data Contract Name Attribute ("__type")。 この属性は、JSON Type Attribute が存在し、その [normalized value] が "object" であるときにのみ存在します。 この属性は、派生型がシリアル化されたり、基本型が要求されたりするポリモーフィックな場合などに、`DataContractJsonSerializer` によりデータ コントラクトの型情報を保持するために使用されます。 `DataContractJsonSerializer` を使用していなければ、この属性はほとんどの場合に無視されます。  
  
-   XML 情報セットの仕様に規定されるように、[in-scope namespaces] には、"xml" から "http://www.w3.org/XML/1998/namespace" へのバインディングが含まれます。  
  
-   [children]、[attributes]、および[in-scope namespaces] は、あらかじめ指定した項目以外の項目を持つことができず、[namespace attributes] はメンバーを持つことができませんが、JSON からマップされた XML を読み取るときには、この事実に依存しないでください。  
  
 例 : 次のドキュメントでは [namespace attributes] が空ではないため、JSON へのマッピングが存在しません。  
  
 `<?xml version="1.0"?>`  
  
 `<root  xmlns:a="myattributevalue">42</root>`  
  
 JSON Type Attribute としての AII には次の特性があります。  
  
-   [namespace name] は値を持ちません。  
  
-   [prefix] は値を持ちません。  
  
-   [local name] は "type" です。  
  
-   [normalized value] は、次のセクションで説明する型の値のいずれかになります。  
  
-   [specified] は `true` です。  
  
-   [attribute type] は値を持ちません。  
  
-   [references] は値を持ちません。  
  
 Data Contract Name Attribute としての AII には次の特性があります。  
  
-   [namespace name] は値を持ちません。  
  
-   [prefix] は値を持ちません。  
  
-   [local name] は "__type" (2 連続のアンダースコアの直後に "type") です。  
  
-   [normalized value] は、任意の有効な Unicode 文字列です。この文字列から JSON へのマッピングは、次のセクションで説明します。  
  
-   [specified] は `true` です。  
  
-   [attribute type] は値を持ちません。  
  
-   [references] は値を持ちません。  
  
 Root JSON Element に含まれる内部要素、またはその他の内部要素には、次の特性があります。  
  
-   後述するように、[local name] は任意の値を持つことができます。  
  
-   [namespace name]、[prefix]、[children]、[attributes]、[namespace attributes]、および [in-scope namespaces] は、Root JSON Element と同じ規則に従います。  
  
 Root JSON Element および内部要素では、JSON Type Attribute により JSON へのマッピングと、[children] およびその解釈が定義されます。 この属性の [normalized value] では大文字と小文字が区別され、小文字を使用する必要があります。また、ここに空白を含めることはできません。  
  
|`JSON Type Attribute` としての AII の [normalized value]|対応する EII の許可された [children]|JSON へのマッピング|  
|---------------------------------------------------------|---------------------------------------------------|---------------------|  
|`string` (または JSON 型 AII なし)<br /><br /> `string` および JSON 型 AII なしは同じです。`string` を既定値にします。<br /><br /> その結果、`<root> string1</root>` が JSON `string` "string1" にマップされます。|0 または複数の Cii|JSON `string` (JSON RFC section 2.5)。 `char` はそれぞれ、CII の [character code] に対応する文字です。 CII が存在しない場合は、空の JSON `string` にマップされます。<br /><br /> 例 : 次の要素は JSON フラグメントにマップされます。<br /><br /> `<root type="string">42</root>`<br /><br /> JSON フラグメントは "42" です。<br /><br /> XML から JSON へのマッピングでは、エスケープする必要がある文字はエスケープ文字にマップされ、その他はすべて、エスケープされない文字にマップされます。 「/」文字が特別な – エスケープする必要はない場合でも (として書き出さ"\\/") です。<br /><br /> 例 : 次の要素は JSON フラグメントにマップされます。<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> JSON フラグメントは"、 \\"da\\/ta\\""です。<br /><br /> JSON から XML へのマッピングでは、エスケープ文字およびエスケープされない文字が、対応する [character code] に正しくマップされます。<br /><br /> 例 : JSON フラグメント "\u0041BC" が次の XML 要素にマップされます。<br /><br /> `<root type="string">ABC</root>`<br /><br /> 文字列は、XML にマップされない空白 (JSON RFC section 2 の 'ws') で囲むことができます。<br /><br /> 例 : JSON フラグメント           "ABC" (最初の二重引用符の前に空白があります) が次の XML 要素にマップされます。<br /><br /> `<root type="string">ABC</root>`<br /><br /> XML の空白が、JSON の空白にマップされます。<br /><br /> 例 : 次の XML 要素は JSON フラグメントにマップされます。<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> JSON フラグメントは " A BC " です。|  
|`number`|1 個以上の CII|JSON `number` (JSON RFC section 2.4)。空白で囲まれている場合があります。 数値と空白の組み合わせに含まれる文字はそれぞれ、CII の [character code] に対応する文字です。<br /><br /> 例 : 次の要素は JSON フラグメントにマップされます。<br /><br /> `<root type="number">    42</root>`<br /><br /> JSON フラグメントは    42 です <br /><br /> (空白が保持されます)。|  
|`boolean`|4 個または 5 個の CII (`true` または `false` に対応)。追加の空白の CII で囲まれている場合があります。|文字列 "true" に対応する CII シーケンスは、リテラルの `true` にマップされ、文字列 "false" に対応する CII シーケンスは、リテラルの `false` にマップされます。 囲んでいる空白は保持されます。<br /><br /> 例 : 次の要素は JSON フラグメントにマップされます。<br /><br /> `<root type="boolean"> false</root>`<br /><br /> JSON フラグメントは `false` です。|  
|`null`|いずれも許可されません。|リテラルの `null`。 JSON から XML へのマッピングでは、`null` は、XML にマップされない空白 (section 2 の 'ws') で囲まれる場合があります。<br /><br /> 例 : 次の要素は JSON フラグメントにマップされます。<br /><br /> `<root type="null"/>`<br /><br /> または<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> いずれの場合も、JSON フラグメントは `Null` です。|  
|`object`|0 個以上の EII|JSON RFC section 2.2 にあるように、`begin-object` (左中かっこ) の直後に、後述するように各 EII のメンバー レコードが続きます。 EII が複数個存在する場合、メンバー レコードの間に値区切り記号 (コンマ) が配置されます。 最後尾には、end-object (右中かっこ) が置かれます。<br /><br /> 例 : 次の要素は JSON フラグメントにマップされます。<br /><br /> \<ルート型 ="object"><br /><br /> \<type1 型 ="string"> aaa\</type1 ><br /><br /> \<type2 型 ="string"> bbb\</type2 ><br /><br /> \</root ><br /><br /> JSON フラグメントは {"type1":"aaa","type2":"bbb"} です。<br /><br /> XML から JSON へのマッピングに Data Contract Type Attribute が存在する場合は、最初に追加のメンバー レコードが挿入されます。 その名前は Data Contract Type Attribute ("__type") の [local name] であり、その値はこの属性の [normalized value] です。 逆に、JSON から XML へのマッピングで、最初のメンバー レコードの名前は Data Contract Type Attribute の [local name] で (つまり、"\_ください (_t)")、対応する Data Contract Type Attribute が、マップされた XML 内に存在が対応する EII はありません存在します。 また、このような特定のマッピングが適用されるには、このメンバー レコードが最初に JSON オブジェクトに存在している必要があります。 これは、メンバー レコードの順序が重要ではない通常の JSON 処理とは異なっています。<br /><br /> 例:<br /><br /> 次の JSON フラグメントは XML にマップされます。<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> XML は次のコードです。<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> 注意して、 \_AII ください (_t) が存在する場合があるない\_EII ください (_t)。<br /><br /> ただし、次の例に示すように、JSON での順序が逆になる場合があります。<br /><br /> {"name":"John「,」\_ください (_t)":"Person"}<br /><br /> このとき、対応する XML は次のとおりです。<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> つまり、 \_EII に対応して特別な意味を通常どおりがください (_t) 停止 AII ではありません。<br /><br /> JSON 値にマップされるときの、AII の [normalized value] に対するエスケープ/エスケープ解除ルールは、このテーブルの "string" 行で指定された JSON 文字列に対するルールと同じです。<br /><br /> 例:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> これを前の例に適用すると、次の JSON にマップされます。<br /><br /> `{"__type":"\\abc"}`<br /><br /> XML JSON へのマッピングからで、最初の EII の [ローカル名] することはできません"\_ください (_t)"です。<br /><br /> オブジェクト用の XML から JSON へのマッピングでは空白 (`ws`) が生成されることはなく、JSON から XML のマッピングでは空白が無視されます。<br /><br /> 例 : 次の JSON フラグメントは XML 要素にマップされます。<br /><br /> {   "ccc"   :  "aaa",   "ddd"    :"bbb"}<br /><br /> XML 要素を、次のコードで示します。<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|  
光線 '|0 個以上の EII|JSON RFC section 2.3 にあるように、begin-array (左角かっこ) の直後に、後述する各 EII の配列レコードが続きます。 EII が複数個存在する場合、配列レコードの間に値区切り記号 (コンマ) が配置されます。 最後尾には、end-array が置かれます。<br /><br /> 例 : 次の XML 要素は JSON フラグメントにマップされます。<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> JSON フラグメントは ["aaa","bbb"] です。<br /><br /> 配列用の XML から JSON へのマッピングでは空白 (`ws`) が生成されることはなく、JSON から XML のマッピングでは空白が無視されます。<br /><br /> 例 : JSON フラグメント<br /><br /> [     "aaa",     "bbb"]<br /><br /> マップされる XML 要素は、次のとおりです。<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|  
  
 メンバー レコードの動作は次のとおりです。  
  
-   JSON RFC section 2.2 で規定されるように、内部要素の [local name] は `string` の `member` 部分にマップされます。  
  
 例 : 次の要素は JSON フラグメントにマップされます。  
  
 `<root type="object"/>`  
  
 `<myLocalName type="string">aaa</myLocalName>`  
  
 `</root >`  
  
 次の JSON フラグメントが示されます。  
  
 `{"myLocalName":"aaa"}`  
  
-   XML から JSON へのマッピングでは、JSON でエスケープする必要がある文字はエスケープされ、それ以外はエスケープされません。 "/" 文字は、エスケープする必要のない文字ですが、エスケープされます (JSON から XML へのマッピングではエスケープする必要はありません)。 これは、JSON の `DateTime` データに対する ASP.NET AJAX 形式をサポートするために必要な処理です。  
  
-   JSON から XML へのマッピングでは、すべての文字が (必要に応じて非エスケープ文字も含む) [local name] を生成する `string` を形成するために使用されます。  
  
-   内部要素 [children] は `JSON Type Attribute` の場合と同じように、`Root JSON Element` に従って section 2.2 の値にマップされます。 EII の複数レベルの入れ子 (配列内の入れ子も含む) が許可されます。  
  
 例 : 次の要素は JSON フラグメントにマップされます。  
  
 `<root type="object">`  
  
 `<myLocalName1 type="string">myValue1</myLocalName1>`  
  
 `<myLocalName2 type="number">2</myLocalName2>`  
  
 `<myLocalName3 type="object">`  
  
 `<myNestedName1 type="boolean">true</myNestedName1>`  
  
 `<myNestedName2 type="null"/>`  
  
 `</myLocalName3>`  
  
 `</root >`  
  
 マップされる JSON フラグメントは次のとおりです。  
  
 `{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}`  
  
> [!NOTE]
>  上記のマッピングには、XML エンコーディングの手順がありません。 したがって、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、キー名のすべての文字が XML 要素名の有効な文字である JSON ドキュメントのみをサポートします。 たとえば、JSON ドキュメント {"<":"a"} は、< が XML 要素の有効な名前ではないため、サポートされません。  
  
 逆に、XML では有効であり、JSON では有効でない文字は、上記のマッピングに JSON のエスケープ/エスケープ解除の手順が含まれるため、問題が生じません。  
  
 Array Record の動作は次のとおりです。  
  
-   内部要素の [local name] は "item" です。  
  
-   内部要素の [children] は、Root JSON Element の場合と同じように、JSON Type Attribute に従って section 2.3 の値にマップされます。 EII の複数の入れ子 (オブジェクト内の入れ子も含む) が許可されます。  
  
 例 : 次の要素は JSON フラグメントにマップされます。  
  
 `<root type="array"/>`  
  
 `<item type="string">myValue1</item>`  
  
 `<item type="number">2</item>`  
  
 `<item type="array">`  
  
 `<item type="boolean">true</item>`  
  
 `<item type="null"/>`  
  
 `</item>`  
  
 `</root >`  
  
 JSON フラグメントは次のとおりです。  
  
 `["myValue1",2,[true,null]]`  
  
## <a name="see-also"></a>参照  
 <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
 [スタンドアロン JSON のシリアル化](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
