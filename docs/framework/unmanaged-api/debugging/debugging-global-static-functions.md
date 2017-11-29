---
title: "デバッグ グローバル静的関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ad5d3ef689a251ea4b154afc5d1bfb387388ddb3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="59dc5-102">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="59dc5-102">Debugging Global Static Functions</span></span>
<span data-ttu-id="59dc5-103">このセクションでは、デバッグ API が使用するアンマネージ グローバル静的関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="59dc5-103">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="59dc5-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="59dc5-104">In This Section</span></span>  
 [<span data-ttu-id="59dc5-105">_EFN_GetManagedExcepStack 関数</span><span class="sxs-lookup"><span data-stu-id="59dc5-105">_EFN_GetManagedExcepStack Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="59dc5-106">指定したマネージ例外オブジェクトのアドレスに応じて、中に含まれているスタック トレースの文字列バージョンを返します。</span><span class="sxs-lookup"><span data-stu-id="59dc5-106">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="59dc5-107">_EFN_GetManagedObjectFieldInfo 関数</span><span class="sxs-lookup"><span data-stu-id="59dc5-107">_EFN_GetManagedObjectFieldInfo Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="59dc5-108">指定したオブジェクト ポインターとフィールド名を使用して、オブジェクトの先頭からフィールドまでのオフセットとフィールドの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="59dc5-108">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="59dc5-109">_EFN_GetManagedObjectName 関数</span><span class="sxs-lookup"><span data-stu-id="59dc5-109">_EFN_GetManagedObjectName Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="59dc5-110">指定したマネージ オブジェクトのポインターを使用して、型の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="59dc5-110">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="59dc5-111">_EFN_StackTrace 関数</span><span class="sxs-lookup"><span data-stu-id="59dc5-111">_EFN_StackTrace Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 <span data-ttu-id="59dc5-112">マネージ スタック トレースのテキスト表現および `CONTEXT` レコードの配列 (アンマネージ コードとマネージ コードの間の各移行につき 1 つ) を提供します。</span><span class="sxs-lookup"><span data-stu-id="59dc5-112">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="59dc5-113">CLRDataCreateInstance 関数</span><span class="sxs-lookup"><span data-stu-id="59dc5-113">CLRDataCreateInstance Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 <span data-ttu-id="59dc5-114">指定した対象プロセスの指定したインターフェイス オブジェクトを作成するために、共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="59dc5-114">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="59dc5-115">PFN_CLRDataCreateInstance 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="59dc5-115">PFN_CLRDataCreateInstance Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="59dc5-116">指定した対象プロセスの指定したインターフェイス オブジェクトを作成するために、CLR データ アクセス サービスによって呼び出される関数を指します。</span><span class="sxs-lookup"><span data-stu-id="59dc5-116">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="59dc5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="59dc5-117">Related Sections</span></span>  
 [<span data-ttu-id="59dc5-118">デバッグ コクラス</span><span class="sxs-lookup"><span data-stu-id="59dc5-118">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="59dc5-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="59dc5-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="59dc5-120">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="59dc5-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="59dc5-121">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="59dc5-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
