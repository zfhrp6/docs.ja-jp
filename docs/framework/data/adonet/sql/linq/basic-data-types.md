---
title: "基本データ型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ae0bb07688cf1e9573d02826f186811cd7340c90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="basic-data-types"></a><span data-ttu-id="39a36-102">基本データ型</span><span class="sxs-lookup"><span data-stu-id="39a36-102">Basic Data Types</span></span>
<span data-ttu-id="39a36-103">LINQ to SQL クエリは、Microsoft SQL Server で実行される前に Transact-SQL に変換されるため、</span><span class="sxs-lookup"><span data-stu-id="39a36-103">Because LINQ to SQL queries translate to Transact-SQL before they are executed on the Microsoft SQL Server.</span></span> <span data-ttu-id="39a36-104">LINQ to SQL は、SQL Server が基本データ型に対してサポートするのと同じ組み込み機能の多くをサポートします。</span><span class="sxs-lookup"><span data-stu-id="39a36-104">LINQ to SQL supports much of the same built-in functionality that SQL Server does for basic data types.</span></span>  
  
## <a name="casting"></a><span data-ttu-id="39a36-105">キャスト</span><span class="sxs-lookup"><span data-stu-id="39a36-105">Casting</span></span>  
 <span data-ttu-id="39a36-106">SQL Server 内に同様の有効な変換が存在する場合は、変換元の CLR 型から変換先の CLR 型への暗黙的または明示的なキャストが有効になります。</span><span class="sxs-lookup"><span data-stu-id="39a36-106">Implicit or explicit casts are enabled from a source CLR type to a target CLR type if there is a similar valid conversion within SQL Server.</span></span> <span data-ttu-id="39a36-107">CLR のキャストの詳細については、次を参照してください。 [CType 関数](~/docs/visual-basic/language-reference/functions/ctype-function.md)([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) および[として](~/docs/csharp/language-reference/keywords/as.md)です。</span><span class="sxs-lookup"><span data-stu-id="39a36-107">For more information about CLR casting, see [CType Function](~/docs/visual-basic/language-reference/functions/ctype-function.md) ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) and [as](~/docs/csharp/language-reference/keywords/as.md).</span></span> <span data-ttu-id="39a36-108">変換後、CLR 式に対して実行される操作の動作は、変換先の型に通常割り当てられる他の CLR 式の動作と一致するように、キャストによって変更されます。</span><span class="sxs-lookup"><span data-stu-id="39a36-108">After conversion, casts change the behavior of operations performed on a CLR expression to match the behavior of other CLR expressions that naturally map to the destination type.</span></span> <span data-ttu-id="39a36-109">継承の割り当てのコンテキストにおいてもキャストは変換可能です。</span><span class="sxs-lookup"><span data-stu-id="39a36-109">Casts are also translatable in the context of inheritance mapping.</span></span> <span data-ttu-id="39a36-110">より厳密なエンティティ サブタイプにオブジェクトを変換して、そのサブタイプに固有のデータへのアクセスを可能にすることができます。</span><span class="sxs-lookup"><span data-stu-id="39a36-110">Objects can be cast to more specific entity subtypes so that their subtype-specific data can be accessed.</span></span>  
  
## <a name="equality-operators"></a><span data-ttu-id="39a36-111">等値演算子</span><span class="sxs-lookup"><span data-stu-id="39a36-111">Equality Operators</span></span>  
 <span data-ttu-id="39a36-112">LINQ to SQL は、LINQ to SQL クエリ内の基本データ型で次の等値演算子をサポートします。</span><span class="sxs-lookup"><span data-stu-id="39a36-112">LINQ to SQL supports the following equality operators on basic data types inside LINQ to SQL queries:</span></span>  
  
-   <span data-ttu-id="39a36-113">等値演算子および非等値演算子 : 等値演算子および非等値演算子は、数値型、<xref:System.Boolean> 型、<xref:System.DateTime> 型、および <xref:System.TimeSpan> 型についてサポートされます。</span><span class="sxs-lookup"><span data-stu-id="39a36-113">Equal and Inequality Operator: Equality and inequality operators are supported for numeric <xref:System.Boolean>, <xref:System.DateTime>, and <xref:System.TimeSpan> types.</span></span> <span data-ttu-id="39a36-114">詳細については[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]演算子`=`と`<>`を参照してください[比較演算子](~/docs/visual-basic/language-reference/operators/comparison-operators.md)です。</span><span class="sxs-lookup"><span data-stu-id="39a36-114">For more about [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] operators `=` and `<>`, see [Comparison Operators](~/docs/visual-basic/language-reference/operators/comparison-operators.md).</span></span> <span data-ttu-id="39a36-115">C# の比較演算子の詳細については`==`と`!=`を参照してください[演算子 = =](~/docs/csharp/language-reference/operators/equality-comparison-operator.md)と[! = 演算子](~/docs/csharp/language-reference/operators/not-equal-operator.md)、それぞれ</span><span class="sxs-lookup"><span data-stu-id="39a36-115">For more information about C# comparison operators `==` and `!=`, see [== Operator](~/docs/csharp/language-reference/operators/equality-comparison-operator.md) and [!= Operator](~/docs/csharp/language-reference/operators/not-equal-operator.md), respectively</span></span>  
  
-   <span data-ttu-id="39a36-116">Is 演算子 : `IS` 演算子には、継承の割り当ての使用時にサポートされる変換があります。</span><span class="sxs-lookup"><span data-stu-id="39a36-116">Is operator: The `IS` operator has a supported translation when inheritance mapping is being used.</span></span> <span data-ttu-id="39a36-117">これは、オブジェクトが特定の種類のエンティティであるかどうかを検査する場合に、判別列を直接調べる代わりとして使用でき、判別列のチェックに変換されます。</span><span class="sxs-lookup"><span data-stu-id="39a36-117">It can be used instead of directly testing the discriminator column to determine whether an object is of a specific entity type, and is translated to a check on the discriminator column.</span></span> <span data-ttu-id="39a36-118">Visual Basic および C# の場合は、演算子の詳細については、次を参照してください。 [Is 演算子](~/docs/visual-basic/language-reference/operators/is-operator.md)と[は](~/docs/csharp/language-reference/keywords/is.md)します。</span><span class="sxs-lookup"><span data-stu-id="39a36-118">For more information about the Visual Basic and C# Is operators, see [Is Operator](~/docs/visual-basic/language-reference/operators/is-operator.md) and [is](~/docs/csharp/language-reference/keywords/is.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39a36-119">参照</span><span class="sxs-lookup"><span data-stu-id="39a36-119">See Also</span></span>  
 [<span data-ttu-id="39a36-120">SQL と CLR の型マッピング</span><span class="sxs-lookup"><span data-stu-id="39a36-120">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="39a36-121">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="39a36-121">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
