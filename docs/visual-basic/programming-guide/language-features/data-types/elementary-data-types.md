---
title: "基本データ型 (Visual Basic) |Microsoft ドキュメント"
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
- elementary data types
- data types [Visual Basic], elementary
ms.assetid: dfad6fe9-2da6-49a4-b0b1-2d7ae0283de5
caps.latest.revision: 16
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
ms.openlocfilehash: 6d363fdd7f7f2755aec34dfe82e38d83ba6e56af
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="elementary-data-types-visual-basic"></a><span data-ttu-id="2a280-102">基本データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a280-102">Elementary Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="2a280-103">多くのプログラミング要素に使用できる定義済みのデータ型のセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="2a280-103"> supplies a set of predefined data types, which you can use for many of your programming elements.</span></span> <span data-ttu-id="2a280-104">このセクションでは、これらの型とその使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a280-104">This section describes these types and how to use them.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a280-105">Visual Basic の場合は、各基本データ型は構造体はクラスでサポートされる、<xref:System>名前空間</xref:System>。</span><span class="sxs-lookup"><span data-stu-id="2a280-105">Every elementary data type in Visual Basic is supported by a structure or a class that is in the <xref:System> namespace.</span></span> <span data-ttu-id="2a280-106">コンパイラは、基になる構造体またはクラスのエイリアスとして各データ型のキーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="2a280-106">The compiler uses each data type keyword as an alias for the underlying structure or class.</span></span> <span data-ttu-id="2a280-107">たとえば、変数を宣言する予約語を使用して、 `Byte` <xref:System.Byte?displayProperty=fullName>.</xref:System.Byte?displayProperty=fullName>構造の完全修飾名を使用して宣言することと同じです</span><span class="sxs-lookup"><span data-stu-id="2a280-107">For example, declaring a variable by using the reserved word `Byte` is the same as declaring it by using the fully qualified structure name <xref:System.Byte?displayProperty=fullName>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a280-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2a280-108">In This Section</span></span>  
 [<span data-ttu-id="2a280-109">数値のデータ型</span><span class="sxs-lookup"><span data-stu-id="2a280-109">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 <span data-ttu-id="2a280-110">整数部と整数以外の数値型をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2a280-110">Describes the integral and non-integral numeric types.</span></span>  
  
 [<span data-ttu-id="2a280-111">文字データ型</span><span class="sxs-lookup"><span data-stu-id="2a280-111">Character Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 <span data-ttu-id="2a280-112">説明、`Char`と`String`型です。</span><span class="sxs-lookup"><span data-stu-id="2a280-112">Describes the `Char` and `String` types.</span></span>  
  
 [<span data-ttu-id="2a280-113">その他のデータ型</span><span class="sxs-lookup"><span data-stu-id="2a280-113">Miscellaneous Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)  
 <span data-ttu-id="2a280-114">説明、 `Boolean`、 `Date`、および`Object`型です。</span><span class="sxs-lookup"><span data-stu-id="2a280-114">Describes the `Boolean`, `Date`, and `Object` types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2a280-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a280-115">Related Sections</span></span>  
 [<span data-ttu-id="2a280-116">データの種類</span><span class="sxs-lookup"><span data-stu-id="2a280-116">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="2a280-117">導入されています、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]のデータ型し、その使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a280-117">Introduces the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="2a280-118">データの種類</span><span class="sxs-lookup"><span data-stu-id="2a280-118">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="2a280-119">によって提供される基本データ型の概要を説明[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="2a280-119">Provides an overview of the elementary data types supplied by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>
