---
title: クラスからのスキーマのエクスポート
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF, schema import and export
- schemas [WCF], exporting from classes
- schemas [WCF]
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: bb57b962-70c1-45a9-93d5-e721e340a13f
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d9e63223fce7f86b0cf2a64ba4e7aa2e54ca6219
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="exporting-schemas-from-classes"></a><span data-ttu-id="63bbf-102">クラスからのスキーマのエクスポート</span><span class="sxs-lookup"><span data-stu-id="63bbf-102">Exporting Schemas from Classes</span></span>
<span data-ttu-id="63bbf-103">データ コントラクト モデルで使用されているクラスから XML スキーマ定義言語 (XSD) スキーマを生成するには、 <xref:System.Runtime.Serialization.XsdDataContractExporter> クラスを使います。</span><span class="sxs-lookup"><span data-stu-id="63bbf-103">To generate XML Schema definition language (XSD) schemas from classes that are used in the data contract model, use the <xref:System.Runtime.Serialization.XsdDataContractExporter> class.</span></span> <span data-ttu-id="63bbf-104">このトピックでは、スキーマの作成手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="63bbf-104">This topic describes the process for creating schemas.</span></span>  
  
## <a name="the-export-process"></a><span data-ttu-id="63bbf-105">エクスポート処理</span><span class="sxs-lookup"><span data-stu-id="63bbf-105">The Export Process</span></span>  
 <span data-ttu-id="63bbf-106">スキーマのエクスポート処理では、まず型の定義をエクスポートするので、型定義を XML 形式で記述した <xref:System.Xml.Schema.XmlSchemaSet> を生成します。</span><span class="sxs-lookup"><span data-stu-id="63bbf-106">The schema export process starts with one or more types and produces an <xref:System.Xml.Schema.XmlSchemaSet> that describes the XML projection of these types.</span></span>  
  
 <span data-ttu-id="63bbf-107">`XmlSchemaSet` は、一連の XSD スキーマ ドキュメントを表す [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] のスキーマ オブジェクト モデル (SOM) の一部です。</span><span class="sxs-lookup"><span data-stu-id="63bbf-107">The `XmlSchemaSet` is part of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]’s Schema Object Model (SOM) that represents a set of XSD Schema documents.</span></span> <span data-ttu-id="63bbf-108">XSD ドキュメントを `XmlSchemaSet`から生成するために、 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> クラスの `XmlSchemaSet` プロパティから取得した、スキーマのコレクションを使います。</span><span class="sxs-lookup"><span data-stu-id="63bbf-108">To create XSD documents from an `XmlSchemaSet`, use the collection of schemas from the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the `XmlSchemaSet` class.</span></span> <span data-ttu-id="63bbf-109">次に各 <xref:System.Xml.Schema.XmlSchema> オブジェクトを、 <xref:System.Xml.Serialization.XmlSerializer>を使ってシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="63bbf-109">Then serialize each <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
#### <a name="to-export-schemas"></a><span data-ttu-id="63bbf-110">スキーマをエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="63bbf-110">To export schemas</span></span>  
  
1.  <span data-ttu-id="63bbf-111"><xref:System.Runtime.Serialization.XsdDataContractExporter>のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="63bbf-111">Create an instance of the <xref:System.Runtime.Serialization.XsdDataContractExporter>.</span></span>  
  
2.  <span data-ttu-id="63bbf-112">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="63bbf-112">Optional.</span></span> <span data-ttu-id="63bbf-113"><xref:System.Xml.Schema.XmlSchemaSet> をコンストラクターに渡します。</span><span class="sxs-lookup"><span data-stu-id="63bbf-113">Pass an <xref:System.Xml.Schema.XmlSchemaSet> in the constructor.</span></span> <span data-ttu-id="63bbf-114">この場合、空の <xref:System.Xml.Schema.XmlSchemaSet> から開始するのではなく、スキーマのエクスポート時に生成されたスキーマが、この <xref:System.Xml.Schema.XmlSchemaSet>インスタンスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="63bbf-114">In this case, the schema generated during the schema export is added to this <xref:System.Xml.Schema.XmlSchemaSet> instance instead of starting with a blank <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
3.  <span data-ttu-id="63bbf-115">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="63bbf-115">Optional.</span></span> <span data-ttu-id="63bbf-116"><xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> メソッドのいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="63bbf-116">Call one of the <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> methods.</span></span> <span data-ttu-id="63bbf-117">指定された型がエクスポート可能かどうかを判定するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="63bbf-117">The method determines whether the specified type can be exported.</span></span> <span data-ttu-id="63bbf-118">このメソッドには、次に説明する `Export` メソッドと同じオーバーロードがあります。</span><span class="sxs-lookup"><span data-stu-id="63bbf-118">The method has the same overloads as the `Export` method in the next step.</span></span>  
  
4.  <span data-ttu-id="63bbf-119"><xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> メソッドのいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="63bbf-119">Call one of the <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> methods.</span></span> <span data-ttu-id="63bbf-120"><xref:System.Type>、 <xref:System.Collections.Generic.List%601> オブジェクトの `Type` 、または <xref:System.Collections.Generic.List%601> オブジェクトの <xref:System.Reflection.Assembly> を受け取る 3 種類のオーバーロードがあります。</span><span class="sxs-lookup"><span data-stu-id="63bbf-120">There are three overloads taking a <xref:System.Type>, a <xref:System.Collections.Generic.List%601> of `Type` objects, or a <xref:System.Collections.Generic.List%601> of <xref:System.Reflection.Assembly> objects.</span></span> <span data-ttu-id="63bbf-121">3 つ目のメソッドの場合、指定されたアセンブリのすべての型がエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="63bbf-121">In the last case, all types in all the given assemblies are exported.</span></span>  
  
     <span data-ttu-id="63bbf-122">`Export` メソッドを何度も呼び出すと、同じ `XmlSchemaSet`に複数の項目が追加されます。</span><span class="sxs-lookup"><span data-stu-id="63bbf-122">Multiple calls to the `Export` method results in multiple items being added to the same `XmlSchemaSet`.</span></span> <span data-ttu-id="63bbf-123">`XmlSchemaSet` に既に存在する型は生成されません。</span><span class="sxs-lookup"><span data-stu-id="63bbf-123">A type is not generated into the `XmlSchemaSet` if it already exists there.</span></span> <span data-ttu-id="63bbf-124">したがって、 `Export` クラスのインスタンスを複数作成するのではなく、同じ `XsdDataContractExporter` に対して `XsdDataContractExporter` を複数回呼び出すようにします。</span><span class="sxs-lookup"><span data-stu-id="63bbf-124">Therefore, calling `Export` multiple times on the same `XsdDataContractExporter` is preferable to creating multiple instances of the `XsdDataContractExporter` class.</span></span> <span data-ttu-id="63bbf-125">これにより、同じスキーマ型が重複して生成される状況を回避できます。</span><span class="sxs-lookup"><span data-stu-id="63bbf-125">This avoids duplicate schema types from being generated.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63bbf-126">エクスポート処理中に障害が発生した場合、 `XmlSchemaSet` は予測できない状態になります。</span><span class="sxs-lookup"><span data-stu-id="63bbf-126">If there is a failure during export, the `XmlSchemaSet` will be in an unpredictable state.</span></span>  
  
5.  <span data-ttu-id="63bbf-127"><xref:System.Xml.Schema.XmlSchemaSet> プロパティを介して、 <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="63bbf-127">Access the <xref:System.Xml.Schema.XmlSchemaSet> through the <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> property.</span></span>  
  
## <a name="export-options"></a><span data-ttu-id="63bbf-128">エクスポート オプション</span><span class="sxs-lookup"><span data-stu-id="63bbf-128">Export Options</span></span>  
 <span data-ttu-id="63bbf-129"><xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> の <xref:System.Runtime.Serialization.XsdDataContractExporter> プロパティとして <xref:System.Runtime.Serialization.ExportOptions> クラスのインスタンスを設定することにより、エクスポート処理の方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="63bbf-129">You can set the <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> property of the <xref:System.Runtime.Serialization.XsdDataContractExporter> to an instance of the <xref:System.Runtime.Serialization.ExportOptions> class to control various aspects of the export process.</span></span> <span data-ttu-id="63bbf-130">具体的には、次のオプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="63bbf-130">Specifically, you can set the following options:</span></span>  
  
-   <span data-ttu-id="63bbf-131"><xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>。</span><span class="sxs-lookup"><span data-stu-id="63bbf-131"><xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>.</span></span> <span data-ttu-id="63bbf-132">`Type` のコレクションであり、エクスポートされる型に対応する既知の型を表します</span><span class="sxs-lookup"><span data-stu-id="63bbf-132">This collection of `Type` represents the known types for the types being exported.</span></span> <span data-ttu-id="63bbf-133">(詳細については、次を参照してください[データ コントラクトの既知の型](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。)。これらの既知の型は、`Export` メソッドに渡された型と共に、`Export` 呼び出しが行われるたびにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="63bbf-133">(For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).) These known types are exported on every `Export` call in addition to the types passed to the `Export` method.</span></span>  
  
-   <span data-ttu-id="63bbf-134"><xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>。</span><span class="sxs-lookup"><span data-stu-id="63bbf-134"><xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>.</span></span> <span data-ttu-id="63bbf-135">このプロパティを介して <xref:System.Runtime.Serialization.IDataContractSurrogate> を渡すことにより、エクスポート処理をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="63bbf-135">An <xref:System.Runtime.Serialization.IDataContractSurrogate> can be supplied through this property that will customize the export process.</span></span> <span data-ttu-id="63bbf-136">詳細については、次を参照してください。[データ コントラクト サロゲート](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)です。</span><span class="sxs-lookup"><span data-stu-id="63bbf-136">For more information, see [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span> <span data-ttu-id="63bbf-137">既定では、サロゲートは使用されません。</span><span class="sxs-lookup"><span data-stu-id="63bbf-137">By default, no surrogate is used.</span></span>  
  
## <a name="helper-methods"></a><span data-ttu-id="63bbf-138">ヘルパー メソッド</span><span class="sxs-lookup"><span data-stu-id="63bbf-138">Helper Methods</span></span>  
 <span data-ttu-id="63bbf-139">`XsdDataContractExporter` には、主要な機能であるスキーマのエクスポート処理に加え、型に関する情報を調べるためのヘルパー メソッドが定義されています。</span><span class="sxs-lookup"><span data-stu-id="63bbf-139">In addition to its primary role of exporting schema, the `XsdDataContractExporter` provides several useful helper methods that provide information about types.</span></span> <span data-ttu-id="63bbf-140">以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="63bbf-140">These include:</span></span>  
  
-   <span data-ttu-id="63bbf-141"><xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A> メソッド</span><span class="sxs-lookup"><span data-stu-id="63bbf-141"><xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A> method.</span></span> <span data-ttu-id="63bbf-142">`Type` を受け取り、この型をルート オブジェクトとしてシリアル化した場合に使用されるルート要素名と名前空間を表す <xref:System.Xml.XmlQualifiedName> を返します。</span><span class="sxs-lookup"><span data-stu-id="63bbf-142">This method takes a `Type` and returns an <xref:System.Xml.XmlQualifiedName> that represents the root element name and namespace that would be used if this type were serialized as the root object.</span></span>  
  
-   <span data-ttu-id="63bbf-143"><xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A> メソッド</span><span class="sxs-lookup"><span data-stu-id="63bbf-143"><xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A> method.</span></span> <span data-ttu-id="63bbf-144">`Type` を引数とし、この型をスキーマにエクスポートした場合に使用される XSD スキーマ型の名前を表す <xref:System.Xml.XmlQualifiedName> を返します。</span><span class="sxs-lookup"><span data-stu-id="63bbf-144">This method takes a `Type` and returns an <xref:System.Xml.XmlQualifiedName> that represents the name of the XSD schema type that would be used if this type were exported to the schema.</span></span> <span data-ttu-id="63bbf-145">スキーマ内で匿名型として表される <xref:System.Xml.Serialization.IXmlSerializable> 型を引数として渡すと、 `null`を返します。</span><span class="sxs-lookup"><span data-stu-id="63bbf-145">For <xref:System.Xml.Serialization.IXmlSerializable> types represented as anonymous types in the schema, this method returns `null`.</span></span>  
  
-   <span data-ttu-id="63bbf-146"><xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A> メソッド</span><span class="sxs-lookup"><span data-stu-id="63bbf-146"><xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A> method.</span></span> <span data-ttu-id="63bbf-147">スキーマ内で匿名型として表される <xref:System.Xml.Serialization.IXmlSerializable> 型を渡した場合にのみ有効なメソッドで、それ以外の型の場合は `null` を返します。</span><span class="sxs-lookup"><span data-stu-id="63bbf-147">This method works only with <xref:System.Xml.Serialization.IXmlSerializable> types that are represented as anonymous types in the schema, and returns `null` for all other types.</span></span> <span data-ttu-id="63bbf-148">匿名型に対しては、特定の <xref:System.Xml.Schema.XmlSchemaType> を表す `Type`を返します。</span><span class="sxs-lookup"><span data-stu-id="63bbf-148">For anonymous types, this method returns an <xref:System.Xml.Schema.XmlSchemaType> that represents a given `Type`.</span></span>  
  
 <span data-ttu-id="63bbf-149">以上のメソッドの動作は、エクスポート オプションの影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="63bbf-149">Export options affect all of these methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63bbf-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="63bbf-150">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 [<span data-ttu-id="63bbf-151">スキーマのインポートとエクスポート</span><span class="sxs-lookup"><span data-stu-id="63bbf-151">Schema Import and Export</span></span>](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)  
 [<span data-ttu-id="63bbf-152">クラスを作成するためのスキーマのインポート</span><span class="sxs-lookup"><span data-stu-id="63bbf-152">Importing Schema to Generate Classes</span></span>](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)
