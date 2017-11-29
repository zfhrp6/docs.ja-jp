---
title: "構造体のプロファイリング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
caps.latest.revision: "27"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42762812c9d27073fac34b20df5011b386f05740
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-structures"></a><span data-ttu-id="b323c-102">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="b323c-102">Profiling Structures</span></span>
<span data-ttu-id="b323c-103">このセクションではプロファイル API で使用されるアンマネージ構造体について説明します。</span><span class="sxs-lookup"><span data-stu-id="b323c-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b323c-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b323c-104">In This Section</span></span>  
 [<span data-ttu-id="b323c-105">COR_PRF_ASSEMBLY_REFERENCE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="b323c-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="b323c-106">共通言語ランタイムに、アセンブリ参照クロージャー ウォークを実行するときに考慮するべき参照アセンブリに関する詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="b323c-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="b323c-107">COR_PRF_CODE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="b323c-107">COR_PRF_CODE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)  
 <span data-ttu-id="b323c-108">メモリに格納されている 1 個の連続ブロックからなるネイティブ コードを表します。</span><span class="sxs-lookup"><span data-stu-id="b323c-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="b323c-109">COR_PRF_EX_CLAUSE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="b323c-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="b323c-110">特定の例外句インスタンスおよび関連するフレームに関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="b323c-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="b323c-111">COR_PRF_FUNCTION 構造体</span><span class="sxs-lookup"><span data-stu-id="b323c-111">COR_PRF_FUNCTION Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-structure.md)  
 <span data-ttu-id="b323c-112">関数の一意の表記を、その関数の ID を再コンパイルされたバージョンの ID と組み合わせることによって、提供します。</span><span class="sxs-lookup"><span data-stu-id="b323c-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="b323c-113">COR_PRF_FUNCTION_ARGUMENT_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="b323c-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="b323c-114">関数の引数を左から右方向で表します。</span><span class="sxs-lookup"><span data-stu-id="b323c-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="b323c-115">COR_PRF_FUNCTION_ARGUMENT_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="b323c-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="b323c-116">メモリに左から右方向へ連続で格納される関数の引数のブロックを表します。</span><span class="sxs-lookup"><span data-stu-id="b323c-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="b323c-117">COR_PRF_GC_GENERATION_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="b323c-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="b323c-118">ガーベッジ コレクションを実行中のメモリ範囲 (ブロック) を説明します。</span><span class="sxs-lookup"><span data-stu-id="b323c-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b323c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="b323c-119">Related Sections</span></span>  
 <span data-ttu-id="b323c-120">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="b323c-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="b323c-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="b323c-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="b323c-122">プロファイルの概要</span><span class="sxs-lookup"><span data-stu-id="b323c-122">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="b323c-123">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b323c-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="b323c-124">プロファイリング グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="b323c-124">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="b323c-125">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="b323c-125">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
