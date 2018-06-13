---
title: ILCodeKind 列挙型
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0881b3903200c023cfa2fe32bf89f62234da29c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424028"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="a84bc-102">ILCodeKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="a84bc-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="a84bc-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="a84bc-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a84bc-104">デバッガーがローカル変数またはプロファイラー ReJIT インストルメンテーションに追加されたコードにアクセスできるかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="a84bc-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a84bc-105">構文</span><span class="sxs-lookup"><span data-stu-id="a84bc-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="a84bc-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a84bc-106">Members</span></span>  
  
|<span data-ttu-id="a84bc-107">メンバー名</span><span class="sxs-lookup"><span data-stu-id="a84bc-107">Member name</span></span>|<span data-ttu-id="a84bc-108">説明</span><span class="sxs-lookup"><span data-stu-id="a84bc-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="a84bc-109">デバッガーは、ReJIT インストルメンテーションからの情報に対してアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="a84bc-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="a84bc-110">デバッガーは、ReJIT インストルメンテーションからの情報に対してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a84bc-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a84bc-111">コメント</span><span class="sxs-lookup"><span data-stu-id="a84bc-111">Remarks</span></span>  
 <span data-ttu-id="a84bc-112">メンバー、`ILCodeKind`に列挙体を渡すことができます、 [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)と[GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)デバッガーがプロファイラーに追加される変数にアクセスできるかどうかを判断する方法ReJIT インストルメンテーションにされ、 [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)デバッガーがアクセスできるかどうかを判断するメソッドには、IL がインストルメント化します。</span><span class="sxs-lookup"><span data-stu-id="a84bc-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a84bc-113">要件</span><span class="sxs-lookup"><span data-stu-id="a84bc-113">Requirements</span></span>  
 <span data-ttu-id="a84bc-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a84bc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a84bc-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a84bc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a84bc-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a84bc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a84bc-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a84bc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a84bc-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a84bc-118">See Also</span></span>  
 [<span data-ttu-id="a84bc-119">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="a84bc-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="a84bc-120">ICorDebugILFrame4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a84bc-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="a84bc-121">ReJIT: ハウツー ガイド</span><span class="sxs-lookup"><span data-stu-id="a84bc-121">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
