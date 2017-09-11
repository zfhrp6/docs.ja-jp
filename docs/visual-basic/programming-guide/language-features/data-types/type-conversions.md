---
title: "Visual Basic での変換の入力 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- conversions, type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion
- conversions, data type
- changing data types
- data type conversion
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 61606572dd1f10dc5df4ed4baec02f230a23c8d6
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="74a23-102">Visual Basic における型変換</span><span class="sxs-lookup"><span data-stu-id="74a23-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="74a23-103">1 つのデータ型から別の型に値を変更するプロセスと呼ばれます*変換*します。</span><span class="sxs-lookup"><span data-stu-id="74a23-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="74a23-104">変換は、*拡大*または*縮小*含まれる型のデータの容量に応じて、します。</span><span class="sxs-lookup"><span data-stu-id="74a23-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="74a23-105">*暗黙的な*または*明示的な*ソース コード内の構文によって異なります。</span><span class="sxs-lookup"><span data-stu-id="74a23-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="74a23-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="74a23-106">In This Section</span></span>  
 [<span data-ttu-id="74a23-107">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="74a23-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="74a23-108">変換先の型がデータを保持するかどうかによって分類される変換について説明します。</span><span class="sxs-lookup"><span data-stu-id="74a23-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="74a23-109">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="74a23-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="74a23-110">かどうかによって分類される変換について説明します[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]自動的に実行します。</span><span class="sxs-lookup"><span data-stu-id="74a23-110">Discusses conversions classified by whether [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] performs them automatically.</span></span>  
  
 [<span data-ttu-id="74a23-111">文字列とその他の型との変換</span><span class="sxs-lookup"><span data-stu-id="74a23-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="74a23-112">文字列と数値、間の変換を示しています。 `Boolean`、または日付/時刻値。</span><span class="sxs-lookup"><span data-stu-id="74a23-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="74a23-113">方法: Visual Basic での別の型のオブジェクトの変換</span><span class="sxs-lookup"><span data-stu-id="74a23-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="74a23-114">変換する方法を示しています、`Object`変数を他のデータ型にします。</span><span class="sxs-lookup"><span data-stu-id="74a23-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="74a23-115">配列変換</span><span class="sxs-lookup"><span data-stu-id="74a23-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="74a23-116">作業をさまざまなデータ型の配列間で変換するプロセス。</span><span class="sxs-lookup"><span data-stu-id="74a23-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="74a23-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="74a23-117">Related Sections</span></span>  
 [<span data-ttu-id="74a23-118">データの種類</span><span class="sxs-lookup"><span data-stu-id="74a23-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="74a23-119">導入されています、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]のデータ型し、その使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="74a23-119">Introduces the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="74a23-120">データの種類</span><span class="sxs-lookup"><span data-stu-id="74a23-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="74a23-121">によって提供される基本データ型を一覧表示[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="74a23-121">Lists the elementary data types supplied by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 [<span data-ttu-id="74a23-122">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="74a23-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="74a23-123">データ型を使用する場合に生じる可能性のある一般的な問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="74a23-123">Discusses some common problems that can arise when working with data types.</span></span>
