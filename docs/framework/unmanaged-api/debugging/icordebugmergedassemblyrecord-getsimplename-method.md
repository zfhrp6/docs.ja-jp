---
title: ICorDebugMergedAssemblyRecord::GetSimpleName メソッド
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8c5499b63e5201fbf42ece07f4f3eff52129e09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417493"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="503c1-102">ICorDebugMergedAssemblyRecord::GetSimpleName メソッド</span><span class="sxs-lookup"><span data-stu-id="503c1-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="503c1-103">アセンブリの簡易名を取得します。</span><span class="sxs-lookup"><span data-stu-id="503c1-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="503c1-104">構文</span><span class="sxs-lookup"><span data-stu-id="503c1-104">Syntax</span></span>  
  
```  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="503c1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="503c1-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="503c1-106">[in] `szName` バッファー内の文字数。</span><span class="sxs-lookup"><span data-stu-id="503c1-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="503c1-107">[out] `szName` バッファーに実際に書き込まれた文字数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="503c1-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="503c1-108">文字配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="503c1-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="503c1-109">コメント</span><span class="sxs-lookup"><span data-stu-id="503c1-109">Remarks</span></span>  
 <span data-ttu-id="503c1-110">このメソッドは、アセンブリの簡易名 ("System.Collections" など) を取得します。簡易名には、ファイル拡張子、バージョン、カルチャ、公開キー トークンが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="503c1-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="503c1-111">これはマネージ コード内の <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> プロパティに対応します。</span><span class="sxs-lookup"><span data-stu-id="503c1-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="503c1-112">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="503c1-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="503c1-113">要件</span><span class="sxs-lookup"><span data-stu-id="503c1-113">Requirements</span></span>  
 <span data-ttu-id="503c1-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="503c1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="503c1-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="503c1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="503c1-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="503c1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="503c1-117">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="503c1-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="503c1-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="503c1-118">See Also</span></span>  
 [<span data-ttu-id="503c1-119">ICorDebugMergedAssemblyRecord インターフェイス</span><span class="sxs-lookup"><span data-stu-id="503c1-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="503c1-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="503c1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
