---
title: 配列
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2945ead7c22b759ce88f6585e2254e9bc540a7ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570404"
---
# <a name="arrays"></a><span data-ttu-id="da9e3-102">配列</span><span class="sxs-lookup"><span data-stu-id="da9e3-102">Arrays</span></span>
<span data-ttu-id="da9e3-103">**✓ しないで**パブリック Api で配列にコレクションの使用を優先します。</span><span class="sxs-lookup"><span data-stu-id="da9e3-103">**✓ DO** prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="da9e3-104">[コレクション](../../../docs/standard/design-guidelines/guidelines-for-collections.md)コレクションと配列から選択する方法の詳細についても説明します。</span><span class="sxs-lookup"><span data-stu-id="da9e3-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>  
  
 <span data-ttu-id="da9e3-105">**X しないで**読み取り専用配列フィールドを使用します。</span><span class="sxs-lookup"><span data-stu-id="da9e3-105">**X DO NOT** use read-only array fields.</span></span> <span data-ttu-id="da9e3-106">フィールド自体は読み取り専用と変更できない配列内の要素を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="da9e3-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>  
  
 <span data-ttu-id="da9e3-107">**✓ を検討してください**多次元配列ではなくジャグ配列を使用します。</span><span class="sxs-lookup"><span data-stu-id="da9e3-107">**✓ CONSIDER** using jagged arrays instead of multidimensional arrays.</span></span>  
  
 <span data-ttu-id="da9e3-108">ジャグ配列は、要素も配列を含む配列です。</span><span class="sxs-lookup"><span data-stu-id="da9e3-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="da9e3-109">さまざまなサイズは小さい無駄な空間データ (たとえば、スパース マトリックス) の一部のセットと比較して多次元配列の要素を構成する配列ができます。</span><span class="sxs-lookup"><span data-stu-id="da9e3-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="da9e3-110">さらに、いくつかのシナリオで実行時パフォーマンスの向上を発生する可能性がありますので、CLR は、ジャグ配列のインデックス操作を最適化します。</span><span class="sxs-lookup"><span data-stu-id="da9e3-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>  
  
 <span data-ttu-id="da9e3-111">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="da9e3-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="da9e3-112">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="da9e3-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da9e3-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="da9e3-113">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="da9e3-114">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="da9e3-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="da9e3-115">使用方法のガイドライン</span><span class="sxs-lookup"><span data-stu-id="da9e3-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
