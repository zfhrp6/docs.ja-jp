---
title: "属性に格納されている情報の取得"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d3fd9a5a49d65b37d2cdb5107e9c516a6df5847
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-information-stored-in-attributes"></a><span data-ttu-id="49c03-102">属性に格納されている情報の取得</span><span class="sxs-lookup"><span data-stu-id="49c03-102">Retrieving Information Stored in Attributes</span></span>
<span data-ttu-id="49c03-103">簡単なプロセスは、カスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="49c03-103">Retrieving a custom attribute is a simple process.</span></span> <span data-ttu-id="49c03-104">最初に、取得する属性のインスタンスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="49c03-104">First, declare an instance of the attribute you want to retrieve.</span></span> <span data-ttu-id="49c03-105">次に、使用、<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>新しい属性を取得する属性の値を初期化します。</span><span class="sxs-lookup"><span data-stu-id="49c03-105">Then, use the <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> method to initialize the new attribute to the value of the attribute you want to retrieve.</span></span> <span data-ttu-id="49c03-106">新しい属性が初期化されると、単にそのプロパティを使用する値を取得します。</span><span class="sxs-lookup"><span data-stu-id="49c03-106">Once the new attribute is initialized, you simply use its properties to get the values.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="49c03-107">このトピックでは、実行コンテキストに読み込まれるコードの属性を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="49c03-107">This topic describes how to retrieve attributes for code loaded into the execution context.</span></span> <span data-ttu-id="49c03-108">リフレクション専用コンテキストに読み込まれるコードの属性を取得するには、使用する必要があります、<xref:System.Reflection.CustomAttributeData>クラスのように[する方法: リフレクション コンテキストにアセンブリをロード](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)です。</span><span class="sxs-lookup"><span data-stu-id="49c03-108">To retrieve attributes for code loaded into the reflection-only context, you must use the <xref:System.Reflection.CustomAttributeData> class, as shown in [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
 <span data-ttu-id="49c03-109">このセクションでは、次の属性を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="49c03-109">This section describes the following ways to retrieve attributes:</span></span>  
  
-   [<span data-ttu-id="49c03-110">属性の 1 つのインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="49c03-110">Retrieving a single instance of an attribute</span></span>](#cpconretrievingsingleinstanceofattribute)  
  
-   [<span data-ttu-id="49c03-111">同じスコープに適用される属性の複数のインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="49c03-111">Retrieving multiple instances of an attribute applied to the same scope</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [<span data-ttu-id="49c03-112">他のスコープに適用される属性の複数のインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="49c03-112">Retrieving multiple instances of an attribute applied to different scopes</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a><span data-ttu-id="49c03-113">属性の 1 つのインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="49c03-113">Retrieving a Single Instance of an Attribute</span></span>  
 <span data-ttu-id="49c03-114">次の例で、 `DeveloperAttribute` (前のセクションで説明) に適用される、`MainApp`クラス レベルのクラスです。</span><span class="sxs-lookup"><span data-stu-id="49c03-114">In the following example, the `DeveloperAttribute` (described in the previous section) is applied to the `MainApp` class on the class level.</span></span> <span data-ttu-id="49c03-115">`GetAttribute`メソッドを使用**されていて**に格納されている値を取得する`DeveloperAttribute`それらをコンソールに表示する前にクラス レベル上。</span><span class="sxs-lookup"><span data-stu-id="49c03-115">The `GetAttribute` method uses **GetCustomAttribute** to retrieve the values stored in `DeveloperAttribute` on the class level before displaying them to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 <span data-ttu-id="49c03-116">このプログラムは、実行時に、次のテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="49c03-116">This program displays the following text when executed.</span></span>  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 <span data-ttu-id="49c03-117">属性が見つからない場合、**されていて**メソッド初期化`MyAttribute`を null 値にします。</span><span class="sxs-lookup"><span data-stu-id="49c03-117">If the attribute is not found, the **GetCustomAttribute** method initializes `MyAttribute` to a null value.</span></span> <span data-ttu-id="49c03-118">この例で確認`MyAttribute`このようなインスタンスの属性が見つからない場合、ユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="49c03-118">This example checks `MyAttribute` for such an instance and notifies the user if no attribute is found.</span></span> <span data-ttu-id="49c03-119">場合、`DeveloperAttribute`はクラス スコープで、次のメッセージをコンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="49c03-119">If the `DeveloperAttribute` is not found in the class scope, the following message displays to the console.</span></span>  
  
```  
The attribute was not found.   
```  
  
 <span data-ttu-id="49c03-120">この例では、属性の定義が、現在の名前空間にある前提としています。</span><span class="sxs-lookup"><span data-stu-id="49c03-120">This example assumes that the attribute definition is in the current namespace.</span></span> <span data-ttu-id="49c03-121">現在の名前空間がない場合、属性の定義が存在する名前空間をインポートしてください。</span><span class="sxs-lookup"><span data-stu-id="49c03-121">Remember to import the namespace in which the attribute definition resides if it is not in the current namespace.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a><span data-ttu-id="49c03-122">同じスコープに適用される属性の複数のインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="49c03-122">Retrieving Multiple Instances of an Attribute Applied to the Same Scope</span></span>  
 <span data-ttu-id="49c03-123">前の例では、検査するクラスとを検索する特定の属性に渡されるの<xref:System.Attribute.GetCustomAttribute%2A>します。</span><span class="sxs-lookup"><span data-stu-id="49c03-123">In the previous example, the class to inspect and the specific attribute to find are passed to <xref:System.Attribute.GetCustomAttribute%2A>.</span></span> <span data-ttu-id="49c03-124">そのコードは、属性の 1 つのインスタンスは、クラス レベルで適用されても専用の場合は動作します。</span><span class="sxs-lookup"><span data-stu-id="49c03-124">That code works well if only one instance of an attribute is applied on the class level.</span></span> <span data-ttu-id="49c03-125">ただし、同じクラス レベルでは、属性の複数のインスタンスが適用されている場合、**されていて**メソッドがすべての情報を取得できません。</span><span class="sxs-lookup"><span data-stu-id="49c03-125">However, if multiple instances of an attribute are applied on the same class level, the **GetCustomAttribute** method does not retrieve all the information.</span></span> <span data-ttu-id="49c03-126">使用できる場合は、同じ属性の複数のインスタンスが同じスコープに適用されます、<xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>配列属性のすべてのインスタンスを配置します。</span><span class="sxs-lookup"><span data-stu-id="49c03-126">In cases where multiple instances of the same attribute are applied to the same scope, you can use <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> to place all instances of an attribute into an array.</span></span> <span data-ttu-id="49c03-127">たとえば、次の 2 つのインスタンス`DeveloperAttribute`、同じクラスのクラス レベルで適用される、`GetAttribute`メソッドは、両方の属性に含まれる情報を表示するように変更できます。</span><span class="sxs-lookup"><span data-stu-id="49c03-127">For example, if two instances of `DeveloperAttribute` are applied on the class level of the same class, the `GetAttribute` method can be modified to display the information found in both attributes.</span></span> <span data-ttu-id="49c03-128">ただし、同じレベルでは、複数の属性を適用すると属性を定義する必要があります、 **AllowMultiple**プロパティに設定**true**で、<xref:System.AttributeUsageAttribute>です。</span><span class="sxs-lookup"><span data-stu-id="49c03-128">Remember, to apply multiple attributes on the same level, the attribute must be defined with the **AllowMultiple** property set to **true** in the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="49c03-129">次のコード例を使用する方法を示しています、 **GetCustomAttributes**メソッドのすべてのインスタンスを参照している配列を作成する`DeveloperAttribute`いずれかでクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="49c03-129">The following code example shows how to use the **GetCustomAttributes** method to create an array that references all instances of `DeveloperAttribute` in any given class.</span></span> <span data-ttu-id="49c03-130">すべての属性の値は、コンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="49c03-130">The values of all attributes are then displayed to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 <span data-ttu-id="49c03-131">属性が見つからない場合、このコードをユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="49c03-131">If no attributes are found, this code alerts the user.</span></span> <span data-ttu-id="49c03-132">両方のインスタンスにそれ以外の場合、情報が含まれている`DeveloperAttribute`が表示されます。</span><span class="sxs-lookup"><span data-stu-id="49c03-132">Otherwise, the information contained in both instances of `DeveloperAttribute` is displayed.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a><span data-ttu-id="49c03-133">他のスコープに適用される属性の複数のインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="49c03-133">Retrieving Multiple Instances of an Attribute Applied to Different Scopes</span></span>  
 <span data-ttu-id="49c03-134"><xref:System.Attribute.GetCustomAttributes%2A>と<xref:System.Attribute.GetCustomAttribute%2A>メソッドせずクラス全体を検索してそのクラスの属性のすべてのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="49c03-134">The <xref:System.Attribute.GetCustomAttributes%2A> and <xref:System.Attribute.GetCustomAttribute%2A> methods do not search an entire class and return all instances of an attribute in that class.</span></span> <span data-ttu-id="49c03-135">代わりが指定されたメソッドまたはメンバーを 1 つだけを同時に検索します。</span><span class="sxs-lookup"><span data-stu-id="49c03-135">Rather, they search only one specified method or member at a time.</span></span> <span data-ttu-id="49c03-136">すべてのメソッドまたはメンバーに個別に指定する必要がありますすべてのメンバーに適用される同じ属性を持つクラスがあるし、それらのメンバーに適用されるすべての属性の値を取得する、 **GetCustomAttributes**と**されていて**です。</span><span class="sxs-lookup"><span data-stu-id="49c03-136">If you have a class with the same attribute applied to every member and you want to retrieve the values in all the attributes applied to those members, you must supply every method or member individually to **GetCustomAttributes** and **GetCustomAttribute**.</span></span>  
  
 <span data-ttu-id="49c03-137">次のコード例は、パラメーターとしてクラスを受け取りし、検索、 `DeveloperAttribute` (定義されている以前) とそのクラスの各メソッドはすべて、クラス レベルでします。</span><span class="sxs-lookup"><span data-stu-id="49c03-137">The following code example takes a class as a parameter and searches for the `DeveloperAttribute` (defined previously) on the class level and on every individual method of that class.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 <span data-ttu-id="49c03-138">インスタンスがない場合、`DeveloperAttribute`メソッド レベルまたはクラス レベル上にある、`GetAttribute`メソッドは、属性が見つかりましたがないユーザーに通知し、メソッドまたは属性が含まれていないクラスの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="49c03-138">If no instances of the `DeveloperAttribute` are found on the method level or class level, the `GetAttribute` method notifies the user that no attributes were found and displays the name of the method or class that does not contain the attribute.</span></span> <span data-ttu-id="49c03-139">属性が見つかった場合、 `Name`、 `Level`、および`Reviewed`フィールドがコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="49c03-139">If an attribute is found, the `Name`, `Level`, and `Reviewed` fields are displayed to the console.</span></span>  
  
 <span data-ttu-id="49c03-140">メンバーを使用することができます、<xref:System.Type>クラスを渡されたクラスで、個々 のメソッドとメンバーを取得します。</span><span class="sxs-lookup"><span data-stu-id="49c03-140">You can use the members of the <xref:System.Type> class to get the individual methods and members in the passed class.</span></span> <span data-ttu-id="49c03-141">この例の最初のクエリ、**型**クラス レベルの属性情報を取得するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="49c03-141">This example first queries the **Type** object to get attribute information for the class level.</span></span> <span data-ttu-id="49c03-142">次に、使用して<xref:System.Type.GetMethods%2A?displayProperty=nameWithType>を配列のすべてのメソッドのインスタンスを配置する<xref:System.Reflection.MemberInfo?displayProperty=nameWithType>メソッド レベルの属性情報を取得するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="49c03-142">Next, it uses <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> to place instances of all methods into an array of <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objects to retrieve attribute information for the method level.</span></span> <span data-ttu-id="49c03-143">使用することも、<xref:System.Type.GetProperties%2A?displayProperty=nameWithType>プロパティ レベルの属性を確認するメソッドまたは<xref:System.Type.GetConstructors%2A?displayProperty=nameWithType>コンス トラクターのレベルの属性を確認します。</span><span class="sxs-lookup"><span data-stu-id="49c03-143">You can also use the <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> method to check for attributes on the property level or <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> to check for attributes on the constructor level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49c03-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="49c03-144">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="49c03-145">属性</span><span class="sxs-lookup"><span data-stu-id="49c03-145">Attributes</span></span>](../../../docs/standard/attributes/index.md)
