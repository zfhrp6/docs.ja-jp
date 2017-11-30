---
title: "Visual Basic における型変換"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b46d813b4fcadd975d87b235e9f3350a365949fa
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="77daa-102">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="77daa-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="77daa-103">値の 1 つのデータ型から別の型に変更するプロセスが呼び出されると*変換*です。</span><span class="sxs-lookup"><span data-stu-id="77daa-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="77daa-104">いずれかの変換は*拡大*または*縮小*関連する型のデータ容量に応じて、します。</span><span class="sxs-lookup"><span data-stu-id="77daa-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="77daa-105">*暗黙的な*または*明示的な*、ソース コード内の構文によって異なります。</span><span class="sxs-lookup"><span data-stu-id="77daa-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="77daa-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="77daa-106">In This Section</span></span>  
 [<span data-ttu-id="77daa-107">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="77daa-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="77daa-108">変換先の型がデータを保持するかどうかによって分類される変換について説明します。</span><span class="sxs-lookup"><span data-stu-id="77daa-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="77daa-109">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="77daa-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="77daa-110">かどうかによって分類される変換について説明します[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]自動的に実行します。</span><span class="sxs-lookup"><span data-stu-id="77daa-110">Discusses conversions classified by whether [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] performs them automatically.</span></span>  
  
 [<span data-ttu-id="77daa-111">文字列とその他の型との変換</span><span class="sxs-lookup"><span data-stu-id="77daa-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="77daa-112">文字列と数値、間の変換を示しています。 `Boolean`、または日付/時刻値。</span><span class="sxs-lookup"><span data-stu-id="77daa-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="77daa-113">方法: オブジェクトを Visual Basic での別の型に変換</span><span class="sxs-lookup"><span data-stu-id="77daa-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="77daa-114">変換する方法を示しています、`Object`変数を他の任意のデータ型にします。</span><span class="sxs-lookup"><span data-stu-id="77daa-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="77daa-115">配列変換</span><span class="sxs-lookup"><span data-stu-id="77daa-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="77daa-116">別のデータ型の配列の間の変換処理を実行する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="77daa-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="77daa-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="77daa-117">Related Sections</span></span>  
 [<span data-ttu-id="77daa-118">データの種類</span><span class="sxs-lookup"><span data-stu-id="77daa-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="77daa-119">導入されています、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]のデータ型し、その使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="77daa-119">Introduces the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="77daa-120">データの種類</span><span class="sxs-lookup"><span data-stu-id="77daa-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="77daa-121">によって提供される基本データ型を一覧表示[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="77daa-121">Lists the elementary data types supplied by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 [<span data-ttu-id="77daa-122">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="77daa-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="77daa-123">データ型を操作するときに発生する可能性がある一般的な問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="77daa-123">Discusses some common problems that can arise when working with data types.</span></span>
