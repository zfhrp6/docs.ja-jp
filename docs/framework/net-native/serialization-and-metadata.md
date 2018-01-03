---
title: "シリアル化とメタデータ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3dea98a381bf468182f24dff27af50e46ad38ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="serialization-and-metadata"></a><span data-ttu-id="d8750-102">シリアル化とメタデータ</span><span class="sxs-lookup"><span data-stu-id="d8750-102">Serialization and Metadata</span></span>
<span data-ttu-id="d8750-103">アプリでオブジェクトをシリアル化および逆シリアル化する場合、ランタイム ディレクティブ (.rd.xml) ファイルにエントリを追加して、必要なメタデータが実行時に確実に存在するようにする必要があることがあります。</span><span class="sxs-lookup"><span data-stu-id="d8750-103">If your app serializes and deserializes objects, you may need to add entries to your runtime directives (.rd.xml) file to ensure that the necessary metadata is present at run time.</span></span> <span data-ttu-id="d8750-104">シリアライザーには次の 2 つのカテゴリがあり、それぞれランタイム ディレクティブ ファイルで異なる処理が必要です。</span><span class="sxs-lookup"><span data-stu-id="d8750-104">There are two categories of serializers, and each requires different handling in your runtime directives file:</span></span>  
  
-   <span data-ttu-id="d8750-105">リフレクション ベースのサードパーティ シリアライザー。</span><span class="sxs-lookup"><span data-stu-id="d8750-105">Reflection-based third-party serializers.</span></span> <span data-ttu-id="d8750-106">この場合、ランタイム ディレクティブ ファイルの変更が必要です。詳細については次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="d8750-106">These require modifications to your runtime directives file, and are discussed in the next section.</span></span>  
  
-   <span data-ttu-id="d8750-107">.NET Framework クラス ライブラリにある非リフレクション ベースのシリアライザー。</span><span class="sxs-lookup"><span data-stu-id="d8750-107">Non-reflection based serializers found in the .NET Framework class library.</span></span> <span data-ttu-id="d8750-108">この場合、ランタイム ディレクティブ ファイルの変更が必要なことがあります。詳細については、「[Microsoft のシリアライザー](#Microsoft)」セクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="d8750-108">These may require modifications to your runtime directives file, and are discussed in the [Microsoft serializers](#Microsoft) section.</span></span>  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a><span data-ttu-id="d8750-109">サードパーティ シリアライザー</span><span class="sxs-lookup"><span data-stu-id="d8750-109">Third-party serializers</span></span>  
 <span data-ttu-id="d8750-110">Newtonsoft.JSON などのサードパーティ シリアライザーは通常リフレクション ベースです。</span><span class="sxs-lookup"><span data-stu-id="d8750-110">Third-part serializers, including Newtonsoft.JSON, typically are reflection-based.</span></span> <span data-ttu-id="d8750-111">シリアル化データのバイナリ ラージ オブジェクト (BLOB) の場合、対象の型のフィールドを名前で検索することで、データ内のフィールドが具象型に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="d8750-111">Given a binary large object (BLOB) of serialized data, the fields in the data are assigned to a concrete type by looking up the fields of the target type by name.</span></span> <span data-ttu-id="d8750-112">少なくとも、これらのライブラリを使用すると、`List<Type>` コレクションでシリアル化または逆シリアル化しようとする <xref:System.Type> オブジェクトごとに [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="d8750-112">At a minimum, using these libraries causes [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exceptions for each <xref:System.Type> object that you try to serialize or deserialize in a `List<Type>` collection.</span></span>  
  
 <span data-ttu-id="d8750-113">これらのシリアライザーでメタデータの欠落により引き起こされる問題に対処する最も簡単な方法は、1 つの名前空間 (`App.Models` など) でシリアル化に使用される型を収集し、`Serialize` メタデータ ディレクティブを適用することです。</span><span class="sxs-lookup"><span data-stu-id="d8750-113">The easiest way to address issues caused by missing metadata for these serializers is to collect types that will be used in serialization under a single namespace (such as `App.Models`) and apply a `Serialize` metadata directive to it:</span></span>  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="d8750-114">この例で使用されている構文の詳細については、「[\<Namespace> 要素](../../../docs/framework/net-native/namespace-element-net-native.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8750-114">For information about the syntax used in the example, see [\<Namespace> Element](../../../docs/framework/net-native/namespace-element-net-native.md).</span></span>  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a><span data-ttu-id="d8750-115">Microsoft のシリアライザー</span><span class="sxs-lookup"><span data-stu-id="d8750-115">Microsoft serializers</span></span>  
 <span data-ttu-id="d8750-116"><xref:System.Runtime.Serialization.DataContractSerializer>、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>、および <xref:System.Xml.Serialization.XmlSerializer> クラスではリフレクションを利用しませんが、シリアル化または逆シリアル化されるオブジェクトに基づいてコードが生成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8750-116">Although the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes do not rely on reflection, they do require code to be generated based on the object to be serialized or deserialized.</span></span> <span data-ttu-id="d8750-117">各シリアライザーのオーバーロードされたコンストラクターには、シリアル化または逆シリアル化される型を指定する <xref:System.Type> パラメーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d8750-117">The overloaded constructors for each serializer include a <xref:System.Type> parameter that specifies the type to be serialized or deserialized.</span></span> <span data-ttu-id="d8750-118">次の 2 つのセクションで説明するように、コードでのその型の指定方法によってユーザーが実行する必要のあるアクションが定義されます。</span><span class="sxs-lookup"><span data-stu-id="d8750-118">How you specify that type in your code defines the action you must take, as discussed in the next two sections.</span></span>  
  
### <a name="typeof-used-in-the-constructor"></a><span data-ttu-id="d8750-119">コンストラクターで使用される typeof</span><span class="sxs-lookup"><span data-stu-id="d8750-119">typeof used in the constructor</span></span>  
 <span data-ttu-id="d8750-120">これらのシリアル化クラスのコンストラクターを呼び出し、メソッド呼び出しに C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) キーワードを含めた場合、**それ以外に行う必要がある作業はありません**。</span><span class="sxs-lookup"><span data-stu-id="d8750-120">If you call a constructor of these serialization classes and include the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword in the method call, **you do not have to do any additional work**.</span></span> <span data-ttu-id="d8750-121">たとえば、シリアル化クラス コンストラクターに対する次の各呼び出しでは、`typeof` キーワードがコンストラクターに渡される式の一部として使用されます。</span><span class="sxs-lookup"><span data-stu-id="d8750-121">For example, in each of the following calls to a serialization class constructor, the `typeof` keyword is used as part of the expression passed to the constructor.</span></span>  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 <span data-ttu-id="d8750-122">[!INCLUDE[net_native](../../../includes/net-native-md.md)] コンパイラは、このコードを自動的に処理します。</span><span class="sxs-lookup"><span data-stu-id="d8750-122">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler will automatically handle this code.</span></span>  
  
### <a name="typeof-used-outside-the-constructor"></a><span data-ttu-id="d8750-123">コンストラクターの外部で使用される typeof</span><span class="sxs-lookup"><span data-stu-id="d8750-123">typeof used outside the constructor</span></span>  
 <span data-ttu-id="d8750-124">次のコードのように、これらのシリアル化クラスのコンストラクターを呼び出し、コンストラクターの <xref:System.Type> パラメーターに提供する式の外部で C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) キーワードを使用した場合、[!INCLUDE[net_native](../../../includes/net-native-md.md)] コンパイラは型を解決できません。</span><span class="sxs-lookup"><span data-stu-id="d8750-124">If you call a constructor of these serialization classes and use the C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) keyword outside the expression supplied to the constructor’s <xref:System.Type> parameter, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve the type:</span></span>  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 <span data-ttu-id="d8750-125">この場合は、次のようなエントリを追加して、ランタイム ディレクティブ ファイルで型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8750-125">In this case, you must specify the type in the runtime directives file by adding an entry like this:</span></span>  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 <span data-ttu-id="d8750-126">同様に、次のコードのように <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> などのコンストラクターを呼び出し、シリアル化する追加の <xref:System.Type> オブジェクトの配列を指定した場合も、[!INCLUDE[net_native](../../../includes/net-native-md.md)] コンパイラはこれらの型を解決できません。</span><span class="sxs-lookup"><span data-stu-id="d8750-126">Similarly, if you call a constructor such as <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> and provide an array of additional <xref:System.Type> objects to serialize, as in the following code, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler cannot resolve these types.</span></span>  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 <span data-ttu-id="d8750-127">型ごとに次のようなエントリをランタイム ディレクティブ ファイルに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8750-127">You must add entries such as the following for each type to the runtime directives file:</span></span>  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 <span data-ttu-id="d8750-128">この例で使用されている構文の詳細については、「[\<Type> 要素](../../../docs/framework/net-native/type-element-net-native.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8750-128">For information about the syntax used in the example, see [\<Type> Element](../../../docs/framework/net-native/type-element-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8750-129">参照</span><span class="sxs-lookup"><span data-stu-id="d8750-129">See Also</span></span>  
 [<span data-ttu-id="d8750-130">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="d8750-130">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="d8750-131">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="d8750-131">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="d8750-132">\<型 > 要素</span><span class="sxs-lookup"><span data-stu-id="d8750-132">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="d8750-133">\<Namespace > 要素</span><span class="sxs-lookup"><span data-stu-id="d8750-133">\<Namespace> Element</span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)
