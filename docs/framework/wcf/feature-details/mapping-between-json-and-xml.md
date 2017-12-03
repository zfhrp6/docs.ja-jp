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
ms.openlocfilehash: 9bf104af8c88413298412d3ec3a29cd934558e2d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="mapping-between-json-and-xml"></a><span data-ttu-id="eeb60-102">JSON と XML 間のマッピング</span><span class="sxs-lookup"><span data-stu-id="eeb60-102">Mapping Between JSON and XML</span></span>
<span data-ttu-id="eeb60-103"><xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> によって作成されるリーダーとライターには、JSON (JavaScript Object Notation) コンテンツでの XML API が備わっています。</span><span class="sxs-lookup"><span data-stu-id="eeb60-103">The readers and writers produced by the <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> provide an XML API over JavaScript Object Notation (JSON) content.</span></span> <span data-ttu-id="eeb60-104">JSON は、JavaScript のオブジェクト リテラルのサブセットを使用してデータをエンコードします。</span><span class="sxs-lookup"><span data-stu-id="eeb60-104">JSON encodes data using a subset of the object literals of JavaScript.</span></span> <span data-ttu-id="eeb60-105">このファクトリによって作成されるリーダーおよびライターは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションが <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> または <xref:System.ServiceModel.WebHttpBinding> を使用して JSON コンテンツを送信または受信するときにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-105">The readers and writers produced by this factory are also used when JSON content is being sent or received by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications using the <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> or the <xref:System.ServiceModel.WebHttpBinding>.</span></span>  
  
 <span data-ttu-id="eeb60-106">JSON リーダーは JSON コンテンツで初期化されると、XML インスタンスで動作するテキストの XML リーダーと同じ方法で動作します。</span><span class="sxs-lookup"><span data-stu-id="eeb60-106">When initialized with JSON content, the JSON reader behaves in the same way that a textual XML reader does over an instance of XML.</span></span> <span data-ttu-id="eeb60-107">テキストの XML リーダーでの一連の呼び出しによって特定の XML インスタンスが生成されると、JSON ライターは JSON コンテンツを書き出します。</span><span class="sxs-lookup"><span data-stu-id="eeb60-107">The JSON writer, when given a sequence of calls that on a textual XML reader produces a certain XML instance, writes out JSON content.</span></span> <span data-ttu-id="eeb60-108">このトピックでは、高度なシナリオで使用するために、この XML のインスタンスと JSON コンテンツ間のマッピングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="eeb60-108">The mapping between this instance of XML and the JSON content is described in this topic for use in advanced scenarios.</span></span>  
  
 <span data-ttu-id="eeb60-109">内部的には、JSON は [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって処理される際に XML 情報セットとして表されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-109">Internally, JSON is represented as an XML infoset when processed by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="eeb60-110">マッピングは論理上の処理であるため、通常はこのような内部表現を考慮する必要はありません。JSON は通常、メモリで物理的に XML に変換されたり、XML から JSON に変換されたりすることはありません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-110">Normally you do not have to be concerned with this internal representation as the mapping is only a logical one: JSON is normally not physically converted to XML in memory or converted to JSON from XML.</span></span> <span data-ttu-id="eeb60-111">マッピングとは、XML API を使用して JSON コンテンツにアクセスすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="eeb60-111">The mapping means that XML APIs are used to access JSON content.</span></span>  
  
 <span data-ttu-id="eeb60-112">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で JSON を使用する場合、通常のシナリオでは <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 動作、または該当する場合は <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> 動作により、<xref:System.ServiceModel.Description.WebHttpBehavior> が自動的にプラグインされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-112">When [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses JSON, the usual scenario is that the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is automatically plugged in by the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior, or by the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior when appropriate.</span></span> <span data-ttu-id="eeb60-113"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、JSON と XML 情報セット間のマッピングを認識し、直接 JSON を処理しているかのように動作します。</span><span class="sxs-lookup"><span data-stu-id="eeb60-113">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> understands the mapping between JSON and the XML infoset and acts as if it is dealing with JSON directly.</span></span> <span data-ttu-id="eeb60-114">XML が次のマッピングに従うという了解の下に、任意の XML リーダーまたはライターで <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-114">(It is possible to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> with any XML reader or writer, with the understanding that the XML conforms to the following mapping.)</span></span>  
  
 <span data-ttu-id="eeb60-115">高度なシナリオでは、次のマッピングへの直接アクセスが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="eeb60-115">In advanced scenarios, it may become necessary to directly access the following mapping.</span></span> <span data-ttu-id="eeb60-116">このようなシナリオが生じるのは、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> に依存することなく、独自の方法で JSON のシリアル化および逆シリアル化を行うとき、または JSON を含むメッセージに対して直接 <xref:System.ServiceModel.Channels.Message> 型を処理するときです。</span><span class="sxs-lookup"><span data-stu-id="eeb60-116">These scenarios occur when you want to serialize and deserialize JSON in custom ways, without relying on the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, or when dealing with the <xref:System.ServiceModel.Channels.Message> type directly for messages containing JSON.</span></span> <span data-ttu-id="eeb60-117">JSON と XML 間のマッピングは、メッセージ ログにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-117">The JSON-XML mapping is also used for message logging.</span></span> <span data-ttu-id="eeb60-118">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のメッセージ ログ機能を使用する場合、次のセクションで説明するマッピングに従って、JSON メッセージが XML としてログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-118">When using the message logging feature in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], JSON messages is logged as XML according to the mapping described in the next section.</span></span>  
  
 <span data-ttu-id="eeb60-119">マッピングの概念を明確にするために、次に JSON ドキュメントの例を示します。</span><span class="sxs-lookup"><span data-stu-id="eeb60-119">To clarify the concept of a mapping, the following example is of a JSON document.</span></span>  
  
```json  
{"product":"pencil","price":12}  
```  
  
 <span data-ttu-id="eeb60-120">前述のリーダーのいずれか 1 つを使用してこの JSON ドキュメントを読み取るには、次の XML ドキュメントの読み取りに使用するシーケンスと同一の、<xref:System.Xml.XmlDictionaryReader> 呼び出しのシーケンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="eeb60-120">To read this JSON document using one of the readers previously mentioned, use the same sequence of <xref:System.Xml.XmlDictionaryReader> calls as you would to read the following XML document.</span></span>  
  
```xml  
<root type="object">  
    <product type="string">pencil</product>  
    <price type="number">12</price>  
</root>  
```  
  
 <span data-ttu-id="eeb60-121">また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によってこの例の JSON メッセージが取得されてログに記録される場合は、先行ログの XML フラグメントを参照します。</span><span class="sxs-lookup"><span data-stu-id="eeb60-121">Furthermore, if the JSON message in the example is received by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and logged, you would see the XML fragment in the preceding log.</span></span>  
  
## <a name="mapping-between-json-and-the-xml-infoset"></a><span data-ttu-id="eeb60-122">JSON と XML 情報セット間のマッピング</span><span class="sxs-lookup"><span data-stu-id="eeb60-122">Mapping Between JSON and the XML Infoset</span></span>  
 <span data-ttu-id="eeb60-123">正式には、マッピングは JSON の間で説明した[RFC 4627](http://go.microsoft.com/fwlink/?LinkId=98808) (を除く厳密でないと特定の特定の制限を追加するその他の制限) XML 情報セット (およびいないテキスト形式の XML) として記載[XML について設定](http://go.microsoft.com/fwlink/?LinkId=98809)です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-123">Formally, the mapping is between JSON as described in [RFC 4627](http://go.microsoft.com/fwlink/?LinkId=98808) (except with certain restrictions relaxed and certain other restrictions added) and the XML infoset (and not textual XML) as described in [XML Information Set](http://go.microsoft.com/fwlink/?LinkId=98809) .</span></span> <span data-ttu-id="eeb60-124">このトピックの定義を参照して*情報項目*および [角かっこで囲んで] フィールドです。</span><span class="sxs-lookup"><span data-stu-id="eeb60-124">See this topic for the definitions of *information items* and fields in [square brackets].</span></span>  
  
 <span data-ttu-id="eeb60-125">空白の JSON ドキュメントは空白の XML ドキュメントにマップされ、空白の XML ドキュメントは空白の JSON ドキュメントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-125">A blank JSON document maps to blank XML document, and a blank XML document maps to a blank JSON document.</span></span> <span data-ttu-id="eeb60-126">XML から JSON へのマッピングで、先行する空白およびドキュメント後続の空白は許可されません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-126">On the XML to JSON mapping, preceding whitespace and trailing whitespace after the document are not allowed.</span></span>  
  
 <span data-ttu-id="eeb60-127">マッピングは、ドキュメント情報項目 (DII: Document Information Item) または要素情報項目 (EII: Element Information Item) のいずれか一方と JSON の間に定義されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-127">The mapping is defined between either a Document Information Item (DII) or an Element Information Item (EII) and JSON.</span></span> <span data-ttu-id="eeb60-128">EII、または DII の [document element] プロパティは、Root JSON Element と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-128">The EII, or the DII’s [document element] property, is referred to as the Root JSON Element.</span></span> <span data-ttu-id="eeb60-129">また、ドキュメント フラグメント (ルート要素を複数持つ XML) は、このマッピングではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-129">Note that document fragments (XML with multiple root elements) are not supported in this mapping.</span></span>  
  
 <span data-ttu-id="eeb60-130">例 : 次のドキュメントがあるとします。</span><span class="sxs-lookup"><span data-stu-id="eeb60-130">Example: The following document:</span></span>  
  
 `<?xml version="1.0"?>`  
  
 `<root type="number">42</root>`  
  
 <span data-ttu-id="eeb60-131">また、次の要素があるとします。</span><span class="sxs-lookup"><span data-stu-id="eeb60-131">And the following element:</span></span>  
  
 `<root type="number">42</root>`  
  
 <span data-ttu-id="eeb60-132">どちらにも JSON へのマッピングが存在します。</span><span class="sxs-lookup"><span data-stu-id="eeb60-132">Both have a mapping to JSON.</span></span> <span data-ttu-id="eeb60-133"><`root`> 要素は、どちらの場合も、Root JSON Element です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-133">The <`root`> element is the Root JSON Element in both cases.</span></span>  
  
 <span data-ttu-id="eeb60-134">また、DII の場合は次の点を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eeb60-134">Furthermore, in the case of a DII, the following should be considered:</span></span>  
  
-   <span data-ttu-id="eeb60-135">[children] 一覧には、除外する必要のある項目が含まれています。</span><span class="sxs-lookup"><span data-stu-id="eeb60-135">Some items in the [children] list must not be present.</span></span> <span data-ttu-id="eeb60-136">JSON からマッピングされた XML を読み取るときは、この事実に依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="eeb60-136">Do not rely on this fact when reading XML mapped from JSON.</span></span>  
  
-   <span data-ttu-id="eeb60-137">[children] 一覧には、注釈情報項目が保持されません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-137">The [children] list holds no comment information items.</span></span>  
  
-   <span data-ttu-id="eeb60-138">[children] 一覧には、DTD 情報項目が保持されません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-138">The [children] list holds no DTD information items.</span></span>  
  
-   <span data-ttu-id="eeb60-139">[Children] 一覧に個人情報 (PI) の情報項目が保持していない (、 \<? xml… > 宣言は PI 情報項目と見なされません)</span><span class="sxs-lookup"><span data-stu-id="eeb60-139">The [children] list holds no personal Information (PI) information items (the \<?xml…> declaration is not considered a PI information item)</span></span>  
  
-   <span data-ttu-id="eeb60-140">[notations] セットは空です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-140">The [notations] set is empty.</span></span>  
  
-   <span data-ttu-id="eeb60-141">[unparsed entities] セットは空です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-141">The [unparsed entities] set is empty.</span></span>  
  
 <span data-ttu-id="eeb60-142">例 : 次のドキュメントでは [children] が PI とコメントを保持するため、JSON へのマッピングが存在しません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-142">Example: The following document has no mapping to JSON because [children] holds a PI and a comment.</span></span>  
  
 `<?xml version="1.0"?>`  
  
 `<!--comment--><?pi?>`  
  
 `<root type="number">42</root>`  
  
 <span data-ttu-id="eeb60-143">Root JSON Element としての EII には次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="eeb60-143">The EII for the Root JSON Element has the following characteristics:</span></span>  
  
-   <span data-ttu-id="eeb60-144">[local name] は値 "root" を持ちます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-144">[local name] has the value "root".</span></span>  
  
-   <span data-ttu-id="eeb60-145">[namespace name] は値を持ちません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-145">[namespace name] has no value.</span></span>  
  
-   <span data-ttu-id="eeb60-146">[prefix] は値を持ちません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-146">[prefix] has no value.</span></span>  
  
-   <span data-ttu-id="eeb60-147">[children] には、後述するように内部要素である EII、または文字情報項目 (CII: Character Information Item) のいずれか一方が含まれる場合と、どちらも含まれない場合がありますが、両方とも含まれることはありません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-147">[children] may either contain EIIs (which represent Inner Elements as described further) or CIIs (Character Information Items as described further) or none of these, but not both.</span></span>  
  
-   <span data-ttu-id="eeb60-148">[attributes] には、次のオプションの属性情報項目 (AII: Attribute Information Item) が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="eeb60-148">[attributes] may contain the following optional attribute information items (AIIs)</span></span>  
  
-   <span data-ttu-id="eeb60-149">後述の JSON Type Attribute ("type")。</span><span class="sxs-lookup"><span data-stu-id="eeb60-149">The JSON Type Attribute ("type") as described further.</span></span> <span data-ttu-id="eeb60-150">この属性は、マップされた XML で JSON 型 (文字列、数値、ブール値、オブジェクト、配列、または null) を保持するのに使用します。</span><span class="sxs-lookup"><span data-stu-id="eeb60-150">This attribute is used to preserve the JSON type (string, number, boolean, object, array or null) in the mapped XML.</span></span>  
  
-   <span data-ttu-id="eeb60-151">後述の Data Contract Name Attribute ("__type")。</span><span class="sxs-lookup"><span data-stu-id="eeb60-151">The Data Contract Name Attribute ("__type") as described further.</span></span> <span data-ttu-id="eeb60-152">この属性は、JSON Type Attribute が存在し、その [normalized value] が "object" であるときにのみ存在します。</span><span class="sxs-lookup"><span data-stu-id="eeb60-152">This attribute is can only be present if the JSON type attribute is also present and its [normalized value] is "object".</span></span> <span data-ttu-id="eeb60-153">この属性は、派生型がシリアル化されたり、基本型が要求されたりするポリモーフィックな場合などに、`DataContractJsonSerializer` によりデータ コントラクトの型情報を保持するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-153">This attribute is used by the `DataContractJsonSerializer` to preserve data contract type information - for example, in polymorphic cases where a derived type is serialized and where a base type is expected.</span></span> <span data-ttu-id="eeb60-154">`DataContractJsonSerializer` を使用していなければ、この属性はほとんどの場合に無視されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-154">If you are not working with the `DataContractJsonSerializer`, in most cases, this attribute is ignored.</span></span>  
  
-   <span data-ttu-id="eeb60-155">XML 情報セットの仕様に規定されるように、[in-scope namespaces] には、"xml" から "http://www.w3.org/XML/1998/namespace" へのバインディングが含まれます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-155">[in-scope namespaces] contains the binding of "xml" to "http://www.w3.org/XML/1998/namespace" as mandated by the infoset specification.</span></span>  
  
-   <span data-ttu-id="eeb60-156">[children]、[attributes]、および[in-scope namespaces] は、あらかじめ指定した項目以外の項目を持つことができず、[namespace attributes] はメンバーを持つことができませんが、JSON からマップされた XML を読み取るときには、この事実に依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="eeb60-156">[children], [attributes] and [in-scope namespaces] must not have any items other than as specified previously and [namespace attributes] must have no members, but do not rely on these facts when reading XML mapped from JSON.</span></span>  
  
 <span data-ttu-id="eeb60-157">例 : 次のドキュメントでは [namespace attributes] が空ではないため、JSON へのマッピングが存在しません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-157">Example: The following document has no mapping to JSON because [namespace attributes] is not empty.</span></span>  
  
 `<?xml version="1.0"?>`  
  
 `<root  xmlns:a="myattributevalue">42</root>`  
  
 <span data-ttu-id="eeb60-158">JSON Type Attribute としての AII には次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="eeb60-158">The AII for the JSON Type Attribute has the following characteristics:</span></span>  
  
-   <span data-ttu-id="eeb60-159">[namespace name] は値を持ちません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-159">[namespace name] has no value.</span></span>  
  
-   <span data-ttu-id="eeb60-160">[prefix] は値を持ちません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-160">[prefix] has no value.</span></span>  
  
-   <span data-ttu-id="eeb60-161">[local name] は "type" です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-161">[local name] is "type".</span></span>  
  
-   <span data-ttu-id="eeb60-162">[normalized value] は、次のセクションで説明する型の値のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="eeb60-162">[normalized value] is one of the possible type values described in the following section.</span></span>  
  
-   <span data-ttu-id="eeb60-163">[specified] は `true` です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-163">[specified] is `true`.</span></span>  
  
-   <span data-ttu-id="eeb60-164">[attribute type] は値を持ちません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-164">[attribute type] has no value.</span></span>  
  
-   <span data-ttu-id="eeb60-165">[references] は値を持ちません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-165">[references] has no value.</span></span>  
  
 <span data-ttu-id="eeb60-166">Data Contract Name Attribute としての AII には次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="eeb60-166">The AII for the Data Contract Name Attribute has the following characteristics:</span></span>  
  
-   <span data-ttu-id="eeb60-167">[namespace name] は値を持ちません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-167">[namespace name] has no value.</span></span>  
  
-   <span data-ttu-id="eeb60-168">[prefix] は値を持ちません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-168">[prefix] has no value.</span></span>  
  
-   <span data-ttu-id="eeb60-169">[local name] は "__type" (2 連続のアンダースコアの直後に "type") です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-169">[local name] is "__type" (two underscores and then "type").</span></span>  
  
-   <span data-ttu-id="eeb60-170">[normalized value] は、任意の有効な Unicode 文字列です。この文字列から JSON へのマッピングは、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="eeb60-170">[normalized value] is any valid Unicode string – the mapping of this string to JSON is described in the following section.</span></span>  
  
-   <span data-ttu-id="eeb60-171">[specified] は `true` です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-171">[specified] is `true`.</span></span>  
  
-   <span data-ttu-id="eeb60-172">[attribute type] は値を持ちません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-172">[attribute type] has no value.</span></span>  
  
-   <span data-ttu-id="eeb60-173">[references] は値を持ちません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-173">[references] has no value.</span></span>  
  
 <span data-ttu-id="eeb60-174">Root JSON Element に含まれる内部要素、またはその他の内部要素には、次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="eeb60-174">Inner elements contained within the Root JSON Element or other inner elements have the following characteristics:</span></span>  
  
-   <span data-ttu-id="eeb60-175">後述するように、[local name] は任意の値を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-175">[local name] may have any value as described further</span></span>  
  
-   <span data-ttu-id="eeb60-176">[namespace name]、[prefix]、[children]、[attributes]、[namespace attributes]、および [in-scope namespaces] は、Root JSON Element と同じ規則に従います。</span><span class="sxs-lookup"><span data-stu-id="eeb60-176">[namespace name], [prefix], [children], [attributes], [namespace attributes], and [in-scope namespaces] are subject to the same rules as the Root JSON Element.</span></span>  
  
 <span data-ttu-id="eeb60-177">Root JSON Element および内部要素では、JSON Type Attribute により JSON へのマッピングと、[children] およびその解釈が定義されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-177">In both the Root JSON Element and the inner elements, the JSON Type Attribute defines the mapping to JSON and the possible [children] and their interpretation.</span></span> <span data-ttu-id="eeb60-178">この属性の [normalized value] では大文字と小文字が区別され、小文字を使用する必要があります。また、ここに空白を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-178">The attribute’s [normalized value] is case-sensitive and must be lowercase, and cannot contain whitespace.</span></span>  
  
|<span data-ttu-id="eeb60-179">`JSON Type Attribute` としての AII の [normalized value]</span><span class="sxs-lookup"><span data-stu-id="eeb60-179">[normalized value] of `JSON Type Attribute`’s AII</span></span>|<span data-ttu-id="eeb60-180">対応する EII の許可された [children]</span><span class="sxs-lookup"><span data-stu-id="eeb60-180">Allowed [children] of the corresponding EII</span></span>|<span data-ttu-id="eeb60-181">JSON へのマッピング</span><span class="sxs-lookup"><span data-stu-id="eeb60-181">Mapping to JSON</span></span>|  
|---------------------------------------------------------|---------------------------------------------------|---------------------|  
|<span data-ttu-id="eeb60-182">`string` (または JSON 型 AII なし)</span><span class="sxs-lookup"><span data-stu-id="eeb60-182">`string` (or absence of the JSON type AII)</span></span><br /><br /> <span data-ttu-id="eeb60-183">`string` および JSON 型 AII なしは同じです。`string` を既定値にします。</span><span class="sxs-lookup"><span data-stu-id="eeb60-183">A `string` and the absence of the JSON type AII are the same makes `string` the default.</span></span><br /><br /> <span data-ttu-id="eeb60-184">その結果、`<root> string1</root>` が JSON `string` "string1" にマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-184">So, `<root> string1</root>` maps to the JSON `string` "string1".</span></span>|<span data-ttu-id="eeb60-185">0 または複数の Cii</span><span class="sxs-lookup"><span data-stu-id="eeb60-185">0 or more CIIs</span></span>|<span data-ttu-id="eeb60-186">JSON `string` (JSON RFC section 2.5)。</span><span class="sxs-lookup"><span data-stu-id="eeb60-186">A JSON `string` (JSON RFC, section 2.5).</span></span> <span data-ttu-id="eeb60-187">`char` はそれぞれ、CII の [character code] に対応する文字です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-187">Each `char` is a character that corresponds to the [character code] from the CII.</span></span> <span data-ttu-id="eeb60-188">CII が存在しない場合は、空の JSON `string` にマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-188">If there are no CIIs, it maps to an empty JSON `string`.</span></span><br /><br /> <span data-ttu-id="eeb60-189">例 : 次の要素は JSON フラグメントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-189">Example: The following element maps to a JSON fragment:</span></span><br /><br /> `<root type="string">42</root>`<br /><br /> <span data-ttu-id="eeb60-190">JSON フラグメントは "42" です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-190">The JSON fragment is "42".</span></span><br /><br /> <span data-ttu-id="eeb60-191">XML から JSON へのマッピングでは、エスケープする必要がある文字はエスケープ文字にマップされ、その他はすべて、エスケープされない文字にマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-191">On XML to JSON mapping, characters that must be escaped map to escaped characters, all others map to characters that are not escaped.</span></span> <span data-ttu-id="eeb60-192">「/」文字が特別な – エスケープする必要はない場合でも (として書き出さ"\\/") です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-192">The "/" character is special – it is escaped even though it does not have to be (written out as "\\/").</span></span><br /><br /> <span data-ttu-id="eeb60-193">例 : 次の要素は JSON フラグメントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-193">Example: The following element maps to a JSON fragment.</span></span><br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> <span data-ttu-id="eeb60-194">JSON フラグメントは"、 \\"da\\/ta\\""です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-194">The JSON fragment is "the \\"da\\/ta\\"".</span></span><br /><br /> <span data-ttu-id="eeb60-195">JSON から XML へのマッピングでは、エスケープ文字およびエスケープされない文字が、対応する [character code] に正しくマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-195">On JSON to XML mapping, any escaped characters and characters that are not escaped map correctly to the corresponding [character code].</span></span><br /><br /> <span data-ttu-id="eeb60-196">例 : JSON フラグメント "\u0041BC" が次の XML 要素にマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-196">Example: The JSON fragment "\u0041BC", maps to the following XML element.</span></span><br /><br /> `<root type="string">ABC</root>`<br /><br /> <span data-ttu-id="eeb60-197">文字列は、XML にマップされない空白 (JSON RFC section 2 の 'ws') で囲むことができます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-197">The string can be surrounded by whitespace ('ws' in section 2 of the JSON RFC) that does not get mapped to XML.</span></span><br /><br /> <span data-ttu-id="eeb60-198">例 : JSON フラグメント           "ABC" (最初の二重引用符の前に空白があります) が次の XML 要素にマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-198">Example: The JSON fragment           "ABC", (there are spaces before the first double quote), maps to the following XML element.</span></span><br /><br /> `<root type="string">ABC</root>`<br /><br /> <span data-ttu-id="eeb60-199">XML の空白が、JSON の空白にマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-199">Any whitespace in XML maps to whitespace in JSON.</span></span><br /><br /> <span data-ttu-id="eeb60-200">例 : 次の XML 要素は JSON フラグメントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-200">Example: The following XML element maps to a JSON fragment.</span></span><br /><br /> `<root type="string">  A BC      </root>`<br /><br /> <span data-ttu-id="eeb60-201">JSON フラグメントは " A BC " です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-201">The JSON fragment is " A BC ".</span></span>|  
|`number`|<span data-ttu-id="eeb60-202">1 個以上の CII</span><span class="sxs-lookup"><span data-stu-id="eeb60-202">1 or more CIIs</span></span>|<span data-ttu-id="eeb60-203">JSON `number` (JSON RFC section 2.4)。空白で囲まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="eeb60-203">A JSON `number` (JSON RFC, section 2.4), possibly surrounded by whitespace.</span></span> <span data-ttu-id="eeb60-204">数値と空白の組み合わせに含まれる文字はそれぞれ、CII の [character code] に対応する文字です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-204">Each character in the number/whitespace combination is a character that corresponds to the [character code] from the CII.</span></span><br /><br /> <span data-ttu-id="eeb60-205">例 : 次の要素は JSON フラグメントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-205">Example: The following element maps to a JSON fragment.</span></span><br /><br /> `<root type="number">    42</root>`<br /><br /> <span data-ttu-id="eeb60-206">JSON フラグメントは    42 です </span><span class="sxs-lookup"><span data-stu-id="eeb60-206">The JSON fragment is    42</span></span><br /><br /> <span data-ttu-id="eeb60-207">(空白が保持されます)。</span><span class="sxs-lookup"><span data-stu-id="eeb60-207">(Whitespace is preserved).</span></span>|  
|`boolean`|<span data-ttu-id="eeb60-208">4 個または 5 個の CII (`true` または `false` に対応)。追加の空白の CII で囲まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="eeb60-208">4 or 5 CIIs (which corresponds to `true` or `false`), possibly surrounded by additional whitespace CIIs.</span></span>|<span data-ttu-id="eeb60-209">文字列 "true" に対応する CII シーケンスは、リテラルの `true` にマップされ、文字列 "false" に対応する CII シーケンスは、リテラルの `false` にマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-209">A CII sequence that corresponds to the string "true" is mapped to the literal `true`, and a CII sequence that corresponds to the string "false" is mapped to the literal `false`.</span></span> <span data-ttu-id="eeb60-210">囲んでいる空白は保持されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-210">Surrounding whitespace is preserved.</span></span><br /><br /> <span data-ttu-id="eeb60-211">例 : 次の要素は JSON フラグメントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-211">Example: The following element maps to a JSON fragment.</span></span><br /><br /> `<root type="boolean"> false</root>`<br /><br /> <span data-ttu-id="eeb60-212">JSON フラグメントは `false` です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-212">The JSON fragment is `false`.</span></span>|  
|`null`|<span data-ttu-id="eeb60-213">いずれも許可されません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-213">None allowed.</span></span>|<span data-ttu-id="eeb60-214">リテラルの `null`。</span><span class="sxs-lookup"><span data-stu-id="eeb60-214">The literal `null`.</span></span> <span data-ttu-id="eeb60-215">JSON から XML へのマッピングでは、`null` は、XML にマップされない空白 (section 2 の 'ws') で囲まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="eeb60-215">On JSON to XML mapping, the `null` may be surrounded by whitespace (‘ws’ in section 2) that does not get mapped to XML.</span></span><br /><br /> <span data-ttu-id="eeb60-216">例 : 次の要素は JSON フラグメントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-216">Example: The following element maps to a JSON fragment.</span></span><br /><br /> `<root type="null"/>`<br /><br /> <span data-ttu-id="eeb60-217">または</span><span class="sxs-lookup"><span data-stu-id="eeb60-217">or</span></span><br /><br /> `<root type="null"></root>`<br /><br /> <span data-ttu-id="eeb60-218">:</span><span class="sxs-lookup"><span data-stu-id="eeb60-218">:</span></span><br /><br /> <span data-ttu-id="eeb60-219">いずれの場合も、JSON フラグメントは `Null` です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-219">The JSON fragment in both cases is `Null`.</span></span>|  
|`object`|<span data-ttu-id="eeb60-220">0 個以上の EII</span><span class="sxs-lookup"><span data-stu-id="eeb60-220">0 or more EIIs.</span></span>|<span data-ttu-id="eeb60-221">JSON RFC section 2.2 にあるように、`begin-object` (左中かっこ) の直後に、後述するように各 EII のメンバー レコードが続きます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-221">A `begin-object` (left curly brace) as in section 2.2 of the JSON RFC, followed by a member record for each EII as described further.</span></span> <span data-ttu-id="eeb60-222">EII が複数個存在する場合、メンバー レコードの間に値区切り記号 (コンマ) が配置されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-222">If there is more than one EII, there are value-separators (commas) between the member records.</span></span> <span data-ttu-id="eeb60-223">最後尾には、end-object (右中かっこ) が置かれます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-223">All this is followed by an end-object (right curly brace).</span></span><br /><br /> <span data-ttu-id="eeb60-224">例 : 次の要素は JSON フラグメントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-224">Example: The following element maps to the JSON fragment.</span></span><br /><br /> <span data-ttu-id="eeb60-225">\<ルート型 ="object"></span><span class="sxs-lookup"><span data-stu-id="eeb60-225">\<root type="object"></span></span><br /><br /> <span data-ttu-id="eeb60-226">\<type1 型 ="string"> aaa\</type1 ></span><span class="sxs-lookup"><span data-stu-id="eeb60-226">\<type1 type="string">aaa\</type1></span></span><br /><br /> <span data-ttu-id="eeb60-227">\<type2 型 ="string"> bbb\</type2 ></span><span class="sxs-lookup"><span data-stu-id="eeb60-227">\<type2 type="string">bbb\</type2></span></span><br /><br /> <span data-ttu-id="eeb60-228">\</root ></span><span class="sxs-lookup"><span data-stu-id="eeb60-228">\</root ></span></span><br /><br /> <span data-ttu-id="eeb60-229">JSON フラグメントは {"type1":"aaa","type2":"bbb"} です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-229">The JSON fragment is {"type1":"aaa","type2":"bbb"}.</span></span><br /><br /> <span data-ttu-id="eeb60-230">XML から JSON へのマッピングに Data Contract Type Attribute が存在する場合は、最初に追加のメンバー レコードが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-230">If the Data Contract Type Attribute is present on XML to JSON mapping, then an additional Member Record is inserted at the beginning.</span></span> <span data-ttu-id="eeb60-231">その名前は Data Contract Type Attribute ("__type") の [local name] であり、その値はこの属性の [normalized value] です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-231">Its name is the [local name] of the Data Contract Type Attribute ("__type"), and its value is the attribute's [normalized value].</span></span> <span data-ttu-id="eeb60-232">逆に、JSON から XML へのマッピングで、最初のメンバー レコードの名前は Data Contract Type Attribute の [local name] で (つまり、"\_ください (_t)")、対応する Data Contract Type Attribute が、マップされた XML 内に存在が対応する EII はありません存在します。</span><span class="sxs-lookup"><span data-stu-id="eeb60-232">Conversely, on JSON to XML mapping, if the first member-record’s name is the [local name] of the Data Contract Type Attribute (that is, "\__type"), a corresponding Data Contract Type Attribute is present in the mapped XML, but a corresponding EII is not present.</span></span> <span data-ttu-id="eeb60-233">また、このような特定のマッピングが適用されるには、このメンバー レコードが最初に JSON オブジェクトに存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="eeb60-233">Note that this member record must occur first in the JSON object for this special mapping to apply.</span></span> <span data-ttu-id="eeb60-234">これは、メンバー レコードの順序が重要ではない通常の JSON 処理とは異なっています。</span><span class="sxs-lookup"><span data-stu-id="eeb60-234">This represents a departure from usual JSON processing, where the order of member records is not significant.</span></span><br /><br /> <span data-ttu-id="eeb60-235">例:</span><span class="sxs-lookup"><span data-stu-id="eeb60-235">Example:</span></span><br /><br /> <span data-ttu-id="eeb60-236">次の JSON フラグメントは XML にマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-236">The following JSON fragment maps to XML.</span></span><br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> <span data-ttu-id="eeb60-237">XML は次のコードです。</span><span class="sxs-lookup"><span data-stu-id="eeb60-237">The XML is the following code.</span></span><br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> <span data-ttu-id="eeb60-238">注意して、 \_AII ください (_t) が存在する場合があるない\_EII ください (_t)。</span><span class="sxs-lookup"><span data-stu-id="eeb60-238">Notice that the \__type AII is present, but there is no \__type EII.</span></span><br /><br /> <span data-ttu-id="eeb60-239">ただし、次の例に示すように、JSON での順序が逆になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="eeb60-239">However, if the order in the JSON is reversed as shown in the following example.</span></span><br /><br /> <span data-ttu-id="eeb60-240">{"name":"John「,」\_ください (_t)":"Person"}</span><span class="sxs-lookup"><span data-stu-id="eeb60-240">{"name":"John","\__type":"Person"}</span></span><br /><br /> <span data-ttu-id="eeb60-241">このとき、対応する XML は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eeb60-241">The corresponding XML is shown.</span></span><br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> <span data-ttu-id="eeb60-242">つまり、 \_EII に対応して特別な意味を通常どおりがください (_t) 停止 AII ではありません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-242">That is, \__type ceases to have special meaning and maps to an EII as usual, not AII.</span></span><br /><br /> <span data-ttu-id="eeb60-243">JSON 値にマップされるときの、AII の [normalized value] に対するエスケープ/エスケープ解除ルールは、このテーブルの "string" 行で指定された JSON 文字列に対するルールと同じです。</span><span class="sxs-lookup"><span data-stu-id="eeb60-243">Escaping/unescaping rules for the AII’s [normalized value] when mapped to a JSON value are the same as for JSON strings, specified in the "string" row of this table.</span></span><br /><br /> <span data-ttu-id="eeb60-244">例:</span><span class="sxs-lookup"><span data-stu-id="eeb60-244">Example:</span></span><br /><br /> `<root type="object" __type="\abc" />`<br /><br /> <span data-ttu-id="eeb60-245">これを前の例に適用すると、次の JSON にマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-245">to the previous example can be mapped to the following JSON.</span></span><br /><br /> `{"__type":"\\abc"}`<br /><br /> <span data-ttu-id="eeb60-246">XML JSON へのマッピングからで、最初の EII の [ローカル名] することはできません"\_ください (_t)"です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-246">On an XML to JSON mapping, the first EII’s [local name] must not be "\__type".</span></span><br /><br /> <span data-ttu-id="eeb60-247">オブジェクト用の XML から JSON へのマッピングでは空白 (`ws`) が生成されることはなく、JSON から XML のマッピングでは空白が無視されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-247">Whitespace (`ws`) is never generated on XML to JSON mapping for objects and is ignored on JSON to XML mapping.</span></span><br /><br /> <span data-ttu-id="eeb60-248">例 : 次の JSON フラグメントは XML 要素にマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-248">Example: The following JSON fragment maps to an XML element.</span></span><br /><br /> <span data-ttu-id="eeb60-249">{   "ccc"   :  "aaa",   "ddd"    :"bbb"}</span><span class="sxs-lookup"><span data-stu-id="eeb60-249">{   "ccc"   :  "aaa",   "ddd"    :"bbb"}</span></span><br /><br /> <span data-ttu-id="eeb60-250">XML 要素を、次のコードで示します。</span><span class="sxs-lookup"><span data-stu-id="eeb60-250">The XML element is shown in the following code.</span></span><br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|  
<span data-ttu-id="eeb60-251">光線 '</span><span class="sxs-lookup"><span data-stu-id="eeb60-251">ray\`</span></span>|<span data-ttu-id="eeb60-252">0 個以上の EII</span><span class="sxs-lookup"><span data-stu-id="eeb60-252">0 or more EIIs</span></span>|<span data-ttu-id="eeb60-253">JSON RFC section 2.3 にあるように、begin-array (左角かっこ) の直後に、後述する各 EII の配列レコードが続きます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-253">A begin-array (left square bracket) as in section 2.3 of the JSON RFC, followed by an array record for each EII as described further.</span></span> <span data-ttu-id="eeb60-254">EII が複数個存在する場合、配列レコードの間に値区切り記号 (コンマ) が配置されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-254">If there is more than one EII, there are value-separators (commas) between the array records.</span></span> <span data-ttu-id="eeb60-255">最後尾には、end-array が置かれます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-255">All this is followed by an end-array.</span></span><br /><br /> <span data-ttu-id="eeb60-256">例 : 次の XML 要素は JSON フラグメントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-256">Example: The following XML element maps to a JSON fragment.</span></span><br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> <span data-ttu-id="eeb60-257">JSON フラグメントは ["aaa","bbb"] です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-257">The JSON fragment is ["aaa","bbb"]</span></span><br /><br /> <span data-ttu-id="eeb60-258">配列用の XML から JSON へのマッピングでは空白 (`ws`) が生成されることはなく、JSON から XML のマッピングでは空白が無視されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-258">Whitespace (`ws`) is never generated on XML to JSON mapping for arrays and is ignored on JSON to XML mapping.</span></span><br /><br /> <span data-ttu-id="eeb60-259">例 : JSON フラグメント</span><span class="sxs-lookup"><span data-stu-id="eeb60-259">Example: AJSON fragment.</span></span><br /><br /> <span data-ttu-id="eeb60-260">[     "aaa",     "bbb"]</span><span class="sxs-lookup"><span data-stu-id="eeb60-260">[     "aaa",     "bbb"]</span></span><br /><br /> <span data-ttu-id="eeb60-261">マップされる XML 要素は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eeb60-261">The XML element that it maps to.</span></span><br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|  
  
 <span data-ttu-id="eeb60-262">メンバー レコードの動作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eeb60-262">Member Records work as follows:</span></span>  
  
-   <span data-ttu-id="eeb60-263">JSON RFC section 2.2 で規定されるように、内部要素の [local name] は `string` の `member` 部分にマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-263">Inner element’s [local name] maps to the `string` part of the `member` as defined in section 2.2 of the JSON RFC.</span></span>  
  
 <span data-ttu-id="eeb60-264">例 : 次の要素は JSON フラグメントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-264">Example: The following element maps to a JSON fragment.</span></span>  
  
 `<root type="object"/>`  
  
 `<myLocalName type="string">aaa</myLocalName>`  
  
 `</root >`  
  
 <span data-ttu-id="eeb60-265">次の JSON フラグメントが示されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-265">The following JSON fragment is displayed.</span></span>  
  
 `{"myLocalName":"aaa"}`  
  
-   <span data-ttu-id="eeb60-266">XML から JSON へのマッピングでは、JSON でエスケープする必要がある文字はエスケープされ、それ以外はエスケープされません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-266">On the XML to JSON mapping, the characters that must be escaped in JSON are escaped, and the others are not escaped.</span></span> <span data-ttu-id="eeb60-267">"/" 文字は、エスケープする必要のない文字ですが、エスケープされます (JSON から XML へのマッピングではエスケープする必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="eeb60-267">The "/" character, even though it is not a character that must be escaped, is escaped nevertheless (it does not have to be escaped on JSON to XML mapping).</span></span> <span data-ttu-id="eeb60-268">これは、JSON の `DateTime` データに対する ASP.NET AJAX 形式をサポートするために必要な処理です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-268">This is required to support the ASP.NET AJAX format for `DateTime` data in JSON.</span></span>  
  
-   <span data-ttu-id="eeb60-269">JSON から XML へのマッピングでは、すべての文字が (必要に応じて非エスケープ文字も含む) [local name] を生成する `string` を形成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-269">On the JSON to XML mapping, all characters (including the not escaped characters, if necessary) are taken to form a `string` that produces a [local name].</span></span>  
  
-   <span data-ttu-id="eeb60-270">内部要素 [children] は `JSON Type Attribute` の場合と同じように、`Root JSON Element` に従って section 2.2 の値にマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-270">Inner elements [children] map to the value in section 2.2, according to the `JSON Type Attribute` just like for the `Root JSON Element`.</span></span> <span data-ttu-id="eeb60-271">EII の複数レベルの入れ子 (配列内の入れ子も含む) が許可されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-271">Multiple levels of nesting of EIIs (including nesting within arrays) are allowed.</span></span>  
  
 <span data-ttu-id="eeb60-272">例 : 次の要素は JSON フラグメントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-272">Example: The following element maps to a JSON fragment.</span></span>  
  
 `<root type="object">`  
  
 `<myLocalName1 type="string">myValue1</myLocalName1>`  
  
 `<myLocalName2 type="number">2</myLocalName2>`  
  
 `<myLocalName3 type="object">`  
  
 `<myNestedName1 type="boolean">true</myNestedName1>`  
  
 `<myNestedName2 type="null"/>`  
  
 `</myLocalName3>`  
  
 `</root >`  
  
 <span data-ttu-id="eeb60-273">マップされる JSON フラグメントは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eeb60-273">The following JSON fragment is what it maps to.</span></span>  
  
 `{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}`  
  
> [!NOTE]
>  <span data-ttu-id="eeb60-274">上記のマッピングには、XML エンコーディングの手順がありません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-274">There is no XML encoding step in the preceding mapping.</span></span> <span data-ttu-id="eeb60-275">したがって、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、キー名のすべての文字が XML 要素名の有効な文字である JSON ドキュメントのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="eeb60-275">Therefore, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] only supports JSON documents where all characters in key names are valid characters in XML element names.</span></span> <span data-ttu-id="eeb60-276">たとえば、JSON ドキュメント {"<":"a"} は、< が XML 要素の有効な名前ではないため、サポートされません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-276">For example, the JSON document {"<":"a"} is not supported because < is not a valid name for an XML element.</span></span>  
  
 <span data-ttu-id="eeb60-277">逆に、XML では有効であり、JSON では有効でない文字は、上記のマッピングに JSON のエスケープ/エスケープ解除の手順が含まれるため、問題が生じません。</span><span class="sxs-lookup"><span data-stu-id="eeb60-277">The reverse situation (characters valid in XML but not in JSON) does not cause any problems because the preceding mapping includes JSON escaping/unescaping steps.</span></span>  
  
 <span data-ttu-id="eeb60-278">Array Record の動作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eeb60-278">Array Records work as follows:</span></span>  
  
-   <span data-ttu-id="eeb60-279">内部要素の [local name] は "item" です。</span><span class="sxs-lookup"><span data-stu-id="eeb60-279">Inner element’s [local name] is "item".</span></span>  
  
-   <span data-ttu-id="eeb60-280">内部要素の [children] は、Root JSON Element の場合と同じように、JSON Type Attribute に従って section 2.3 の値にマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-280">Inner element’s [children] map to the value in section 2.3, according to the JSON Type Attribute as is does for the Root JSON Element.</span></span> <span data-ttu-id="eeb60-281">EII の複数の入れ子 (オブジェクト内の入れ子も含む) が許可されます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-281">Multiple levels of nesting of EIIs (including nesting within objects) are allowed.</span></span>  
  
 <span data-ttu-id="eeb60-282">例 : 次の要素は JSON フラグメントにマップされます。</span><span class="sxs-lookup"><span data-stu-id="eeb60-282">Example: The following element maps to a JSON fragment.</span></span>  
  
 `<root type="array"/>`  
  
 `<item type="string">myValue1</item>`  
  
 `<item type="number">2</item>`  
  
 `<item type="array">`  
  
 `<item type="boolean">true</item>`  
  
 `<item type="null"/>`  
  
 `</item>`  
  
 `</root >`  
  
 <span data-ttu-id="eeb60-283">JSON フラグメントは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eeb60-283">The following is the JSON fragment.</span></span>  
  
 `["myValue1",2,[true,null]]`  
  
## <a name="see-also"></a><span data-ttu-id="eeb60-284">関連項目</span><span class="sxs-lookup"><span data-stu-id="eeb60-284">See Also</span></span>  
 <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
 [<span data-ttu-id="eeb60-285">スタンドアロン JSON のシリアル化</span><span class="sxs-lookup"><span data-stu-id="eeb60-285">Stand-Alone JSON Serialization</span></span>](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
