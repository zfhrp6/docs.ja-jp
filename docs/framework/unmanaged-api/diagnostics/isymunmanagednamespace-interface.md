---
title: ISymUnmanagedNamespace インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace
helpviewer_keywords:
- ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: d42bea4e-5848-4e43-a883-69af7a313ce9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9408a56b7a1e8cbad94014b55ec5d830e1734810
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426089"
---
# <a name="isymunmanagednamespace-interface"></a><span data-ttu-id="13619-102">ISymUnmanagedNamespace インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13619-102">ISymUnmanagedNamespace Interface</span></span>
<span data-ttu-id="13619-103">名前空間を表します。</span><span class="sxs-lookup"><span data-stu-id="13619-103">Represents a namespace.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="13619-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="13619-104">Methods</span></span>  
  
|<span data-ttu-id="13619-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="13619-105">Method</span></span>|<span data-ttu-id="13619-106">説明</span><span class="sxs-lookup"><span data-stu-id="13619-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="13619-107">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="13619-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-getname-method.md)|<span data-ttu-id="13619-108">この名前空間の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="13619-108">Gets the name of this namespace.</span></span>|  
|[<span data-ttu-id="13619-109">GetNamespaces メソッド</span><span class="sxs-lookup"><span data-stu-id="13619-109">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-getnamespaces-method.md)|<span data-ttu-id="13619-110">この名前空間の子を取得します。</span><span class="sxs-lookup"><span data-stu-id="13619-110">Gets the children of this namespace.</span></span>|  
|[<span data-ttu-id="13619-111">GetVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="13619-111">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-getvariables-method.md)|<span data-ttu-id="13619-112">この名前空間内のグローバル スコープで定義されたすべての変数を返します。</span><span class="sxs-lookup"><span data-stu-id="13619-112">Returns all variables defined at global scope within this namespace.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13619-113">要件</span><span class="sxs-lookup"><span data-stu-id="13619-113">Requirements</span></span>  
 <span data-ttu-id="13619-114">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="13619-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13619-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="13619-115">See Also</span></span>  
 [<span data-ttu-id="13619-116">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13619-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
